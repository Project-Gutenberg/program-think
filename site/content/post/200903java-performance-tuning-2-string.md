---
layout: default
title: 'Java 性能优化[2]&#65306;字符串过滤实战'
date: None
author:
    display_name: 
---

　　[上一个帖子](https://program-think.blogspot.com/2009/03/java-performance-tuning-1-two-types.html)已经介绍了基本类型和引用类型的性能差异（主要是由于内存分配方式不同导致）。为了给列位看官加深印象，今天拿一个具体的例子来实地操作一把，看看优化的效果如何。 　　首先描述一下需求：

给定一个 String 对象，过滤掉除了**数字**（字符'0'到'9'）以外的其它字符。要求时间开销尽可能小。过滤函数的原型如下：

  

String filter(String str);

　　针对上述需求，俺写了5个不同的过滤函数。为了叙述方便，函数名分别定为 filter1 到 filter5。其中 filter1 性能最差、filter5 性能最好。在看后续的内容之前，你先暗自思考一下，如果由你来实现该函数，大概会写成什么样？最好把你想好的函数写下来，便于跟俺给出的例子作对比。  
　　为了方便测试性能，先准备好一坨测试代码，具体如下：

class Test
{ public static void main(String\[\] args) { if(args.length != 1) { return; } String str \= ""; long nBegin \= System.currentTimeMillis(); for(int i\=0; i<1024\*1024; i++) { str \= filterN(args\[0\]); // 此处调用某个具体的过滤函数 } long nEnd \= System.currentTimeMillis(); System.out.println(nEnd\-nBegin); System.out.println(str); }
};

　　在没有想好你的实现方式之前，先别偷看后续内容哦！另外，先注明一下，俺的 Java 环境是 JDK 1.5.0-09，使用的测试字符串是随机生成的，长度32个 char，只含字母和数字。由于 JDK 版本和机器性能不尽相同，你在自己机器上测试的结果可能跟俺下面给出的数值不太一样。 　　先来揭晓性能最差的filter1，代码如下：

private static String filter1(String strOld)
{ String strNew \= new String(); for(int i\=0; i<strOld.length(); i++) { if('0'<=strOld.charAt(i) && strOld.charAt(i)<='9') { strNew += strOld.charAt(i); } } return strNew;
}

　　如果你的代码不幸和 filter1 雷同，那你的 Java 功底可就是相当糟糕了，连字符串拼接需要用 StringBuffer 来优化都没搞明白。 　　为了和后续对比，先记下 filter1 的处理时间，大约在 8.81-8.90秒 之间。 　　再来看看 filter2，代码如下：

private static String filter2(String strOld)
{ StringBuffer strNew \= new StringBuffer(); for(int i\=0; i<strOld.length(); i++) { if('0'<=strOld.charAt(i) && strOld.charAt(i)<='9') { strNew.append(strOld.charAt(i)); } } return strNew.toString();
}

　　其实刚才在评价 filter1 的时候，已经泄露了 filter2 的天机。filter2 通过使用 StringBuffer 来优化连接字符串的性能。为什么 StringBuffer 连接字符串的性能比 String 好，这个已经是老生常谈，俺在这儿就不细说啦。尚不清楚的同学自己上 Google 一查便知。估计应该有挺多同学会写出类似 filter2 的代码。 　　有些同学可能会问：为啥不用 StringBuilder？ 　　确实，在 JDK 1.5 新增加了 StringBuilder 这个类，其性能会比 StringBuffer 更好。不过捏，考虑到有可能要拿到其它版本的 JDK 上作对比测试，而且 StringBuilder 和 StringBuffer 之间的差异【不是】本文讨论的重点，所以后面的例子都使用 StringBuffer 来实现。 　　filter2 的处理时间大约为 2.14-2.18秒，提升了大约4倍。 　　接着看看 filter3，代码如下：

private static String filter3(String strOld)
{ StringBuffer strNew \= new StringBuffer(); int nLen \= strOld.length(); for(int i\=0; i<nLen; i++) { char ch \= strOld.charAt(i); if('0'<=ch && ch<='9') { strNew.append(ch); } } return strNew.toString();
}

　　乍一看，filter3 和 filter2 的代码差不多嘛！再仔细瞧一瞧，原来先把 strOld.charAt(i) 赋值给 char 变量，节省了重复调用 charAt() 方法的开销；另外把 strOld.length() 先保存为 nLen，也节省了重复调用 length() 的开销。能想到这一步的同学，估计是比较细心的。 　　经过此一优化，处理时间节省为 1.48-1.52秒，提升了约30%。由于 charAt() 和 length() 的内部实现都挺简单的，所以提升的性能不太明显。 　　另外补充一下，经网友反馈，在 JDK 1.6 上，filter3 和 filter2 的性能基本相同。俺估计：可能是因为 JDK 1.6 在编译时已经进行了相关的优化。 　　然后看看 filter4，代码如下：

private static String filter4(String strOld)
{ int nLen \= strOld.length(); StringBuffer strNew \= new StringBuffer(nLen); for(int i\=0; i<nLen; i++) { char ch \= strOld.charAt(i); if('0'<=ch && ch<='9') { strNew.append(ch); } } return strNew.toString();
}

　　filter4 和 filter3 差别也很小，唯一差别就在于调用了 StringBuffer 带参数的构造函数。通过 StringBuffer 的构造函数设置初始的容量大小，可以有效避免 append() 追加字符时重新分配内存，从而提高性能。 　　filter4 的处理时间大约在 1.33-1.39秒，约提高10%左右。可惜提升的幅度有点小 :-( 　　最后来看看“终极版本”——性能最好的 filter5。

private static String filter5(String strOld)
{ int nLen \= strOld.length(); char\[\] chArray \= new char\[nLen\]; int nPos \= 0; for(int i\=0; i<nLen; i++) { char ch \= strOld.charAt(i); if('0'<=ch && ch<='9') { chArray\[nPos\] \= ch; nPos++; } } return new String(chArray, 0, nPos);
}

　　猛一看，你可能会想：这个 filter5 和前几个版本的差别也忒大了吧！filter5 既没有用 String 也没有用 StringBuffer，而是拿字符数组进行中间处理。 　　filter5 的处理时间，只用了0.72-0.78秒，相对于 filter4 提升了将近50%。为啥捏？是不是因为直接操作字符数组，节省了 append(char) 的调用？通过查看 append(char) 的源代码，内部的实现很简单，应该不至于提升这么多。 　　那是什么原因捏？ 　　首先，虽然 filter5 有一个字符数组的创建开销，但是相对于 filter4 来说，StringBuffer 的构造函数内部也会有字符数组的创建开销。两相抵消。所以 filter5 比 filter4 还多节省了 StringBuffer 对象本身的创建开销。（在俺的 JDK 1.5 环境中，这个因素比较明显） 　　其次，由于 StringBuffer 是线程安全的（它的方法都是 synchronized），因此调用它的方法有一定的同步开销，而字符数组则没有，这又是一个性能提升的地方。（经热心读者反馈，此因素在 JDK 1.6 中比较明显） 　　基于上述两个因素，所以 filter5 比 filter4 又有较大幅度的提升。  
　　上述5个版本，filter1 和 filter5 的性能相差约12倍（已经超过一个数量级）。除了 filter3 相对于 filter2 是通过消除函数重复调用来提升性能，其它的几个版本都是通过节省内存分配，降低了时间开销。可见内存分配对于性能的影响有多大啊！如果你是看了[上一个帖子](https://program-think.blogspot.com/2009/03/java-performance-tuning-1-two-types.html)才写出 filter4 或者 filter5，那说明你已经领会了个中奥妙，俺那个帖子也就没白写了。 　　另外，需要补充说明一下。版本4和版本5使用了空间换时间的手法来提升性能。假如被过滤的字符串【很大】，并且数字字符的比例【很低】，这种方式就不太合算了。 　　举个例子：被处理的字符串中，绝大部分都只含有不到10%的数字字符，只有少数字符串包含较多的数字字符。这时候该怎么办捏？ 　　对于 filter4 来说，可以把 new StringBuffer(nLen); 修改为 new StringBuffer(nLen/10); 来节约空间开销。但是 filter5 就没法这么玩了。 　　所以，具体该用“版本4”还是“版本5”，要看具体情况了。只有在你【非常】看重时间开销，且数字字符比例很高（至少大于50%）的情况下，用 filter5 才合算。否则的话，建议用 filter4。

　　下一个帖子，打算介绍一下“[关于垃圾回收（GC）](https://program-think.blogspot.com/2009/04/java-performance-tuning-3-gc.html)”的话题。

[回到本系列的目录](https://program-think.blogspot.com/2009/03/java-performance-tuning-0-overview.html#index)

