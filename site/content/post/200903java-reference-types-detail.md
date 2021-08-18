---
layout: default
title: 'Java 新手进阶&#65306;细说引用类型'
date: None
author:
    display_name: 
---

　　在前几天的帖子《[Java性能优化\[1\]：基本类型 vs 引用类型](https://program-think.blogspot.com/2009/03/java-performance-tuning-1-two-types.html)》里，俺大概介绍了“引用类型”与“基本类型”在存储上的区别。昨天有网友在评论中批评说“引用类型变量和它所引用的对象”没区分清楚，容易混淆。所以今天专门来说一下引用类型的相关细节。  
　　另外，顺便也把[原先的帖子](https://program-think.blogspot.com/2009/03/java-performance-tuning-1-two-types.html)中，关于“两种类型的存储方式”这节补充了一下，加点插图，有助于大伙儿的理解。  
　　其实，引用类型的变量非常类似于 C/C++ 的指针。为了形象起见，也为了打字方便，本文后面的内容，都把“引用类型的变量”称为【**指针**】。所以，如果你原先有 C/C++ 背景，今天讲的内容对你来说应该很好理解；否则的话，可能要多琢磨琢磨了。 　　假设咱们在【函数中】写了如下这个简单的语句：

StringBuffer str \= new StringBuffer("Hello world");

　　别看这个语句简单，其实包含了如下三个步骤： 　　首先，new 操作符会在【堆】（Heap）里申请了一坨内存，把创建好的 StringBuffer 对象放进去。 　　其次，StringBuffer str 声明了一个指针。这个指针本身是存储在【栈】（Stack）上的（因为前面俺说了：此语句写在【函数中】），用来指向某个 StringBuffer 类型的对象。或者换一种说法，这个指针可以用来保存某个 StringBuffer 对象的地址。 　　最后，当中这个 等于号（赋值符号）把两者关联起来，也就是把刚申请的那一坨内存的地址保存成 str 的值。

　　为了加深列位看官的印象，把[上次那篇帖子](https://program-think.blogspot.com/2009/03/java-performance-tuning-1-two-types.html)的图片再拿出来秀一下：

  

![不见图 请翻墙](https://lh4.googleusercontent.com/IWDtsm7VLuu_uhdh7j8ZsOu4_x5b-5RmX3-GjhPETeu53ojrO2fZEZhQm5xkQGF4g5CtBNL9bXkRp2PJ2l0fsebBfyC4QCvWy1hGYiMkS0zgmtRyAM2xger0UX2c08P9dQu0nPc7)

  
　　通过上述的图解，大伙儿应该明白指针变量和该指针变量指向的【对象】是一个什么关系了吧？ 　　还是接着刚才的例子，再来看赋值的问题。对于如下语句：　　这个赋值语句是啥意思捏？实际上就是把 str 的地址复制给 str2；记住，是地址的复制，StringBuffer 对象本身并【没有】复制。所以两个指针指向的是同一个东东。 　　再搞一张示意图，如下（今天画这些图可把俺累坏了）：

![不见图 请翻墙](https://lh3.googleusercontent.com/IipVIIuED4vXXlv6ydLEDujhVx_B9UAhTCcSsZq-88Pdap0UuErhz5qUg6ussV6u0CLtIX9MY9aqRxp4PrUDfPkLlh7deFS0BZMd39L3oMFBMRK85-HgYcggO7AkcWQDl4sRDvqU)

　　明白了赋值，判断相等的问题（就是==操作符）也就简单了。当我们写如下语句时，只是判断两个指针的【值】（也就是对象的地址）是否相等，并【不是】判断“被指向的对象”是否内容相同。　　实际上两个指针的值相同，则肯定是指向同一个对象（所以对象内容必定相同）。但是两个内容相同的对象，它们的地址可能不一样（比如克隆出来的多个对象之间，地址就不同）。 　　针对引用类型变量的 final 修饰符也是很多人搞混淆的地方。实际上 final 只是修饰指针的值（也就是限定指针保存的地址不能变）。至于该指针指向的对象，内容是否能变，那就管不着了。所以，对于如下语句：

final StringBuffer strConst \= new StringBuffer();

　　你可以修改它指向的对象的【内容】，比如：  

strConst.append("hello world");

　　但是【不能】修改它的【值】，比如：  
  
　　引用类型（在函数调用中）的传参问题，是一个相当扯的问题。有些书上说是传值，有些书上说是传引用。搞得 Java 程序员都快成神经分裂了。所以，我们最后来谈一下“引用类型参数传递”的问题。 　　还是拿刚才的例子，假设现在要把刚才创建的那一坨字符串打印出来，我们会使用如下语句：　　这个语句又是什么意思捏？这时候就两说了。 　　第一种理解： 　　可以认为传进函数的是 str 这个指针，指针说白了就是一个地址的值，说得再白一点，就是个整数。按照这种理解，就是传值的方式。也就是说，参数传递的是指针本身，所以是传值的。 　　第二种理解： 　　可以认为传进去的是 StringBuffer 对象，按照这种理解，就是传引用方式了。因为我们确实是把对象的地址（也就是引用）给传了进去。 　　费了这么多口水，其实不论是“传引用”还是“传值”，都可以讲得通，关键取决于你是【如何看待】参数所传递的【东西】。这就好比量子力学中“光的波粒二象性”，如果你以粒子的方式去测量它，它看起来像粒子；如果你以波动的方式去观测它，它看起来像波动。假如你不太懂量子力学，前面这话就当我没说 :-)

**俺博客上，和本文相关的帖子（需翻墙）**：

  
[Java 新手的通病（系列）](https://program-think.blogspot.com/2009/01/defect-of-java-beginner-0-overview.html)  
[Java 性能优化（系列）](https://program-think.blogspot.com/2009/03/java-performance-tuning-0-overview.html)

