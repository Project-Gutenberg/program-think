---
layout: default
title: 'Java 性能优化[1]&#65306;基本类型 vs 引用类型'
date: None
author:
    display_name: 
---

　　[在 Java 性能优化系列](https://program-think.blogspot.com/2009/03/java-performance-tuning-0-overview.html)中，内存管理是一个要优先考虑的关键因素。而说到内存分配，就必然会涉及到基本类型和引用类型。所以我们今天就先来介绍一下这两种类型在性能方面各自有什么奥妙（关于引用类型的其它奥妙，请看“[这里](https://program-think.blogspot.com/2009/03/java-reference-types-detail.html)”）。 　　先明确一下什么是“基本类型”，什么是“引用类型”。 　　简单地说，所谓基本类型就是 Java 语言中如下的8种内置类型：

> boolean char byte short int long float double

　　而引用类型就是那些可以通过 new 来创建对象的类型（基本上都是派生自 Object）。 　　这两种类型的差异，首先体现在存储方式上。 　　当你在**函数中**创建一个引用类型的对象时，比如下面这句：  

StringBuffer str = new StringBuffer();

　　该 StringBuffer 【对象】的内容是存储在堆（Heap）上的，需要申请堆内存。而变量 str 只不过是针对该 StringBuffer 对象的一个引用（或者叫地址）。变量 str 的【值】（也就是 StringBuffer 对象的地址）是存储在【栈】上的。 　　当你在【函数中}创建一个基本类型的变量时，比如下面这句：  

int n = 123;

　　这个变量 n 的【值】也是存储在栈（Stack）上的，但是这个语句不需要再从堆中申请内存了。 　　为了更加形象，便于大伙儿理解，简单画了一个示意图如下：

![不见图 请翻墙](https://lh4.googleusercontent.com/IWDtsm7VLuu_uhdh7j8ZsOu4_x5b-5RmX3-GjhPETeu53ojrO2fZEZhQm5xkQGF4g5CtBNL9bXkRp2PJ2l0fsebBfyC4QCvWy1hGYiMkS0zgmtRyAM2xger0UX2c08P9dQu0nPc7)

　　可能有同学会小声问：堆和栈有啥区别捏？ 　　要说堆和栈的差别，那可就大了去了。如果你对这两个概念还是不太明白或者经常混淆，建议先找本操作系统的书拜读一下。

　　由于[本系列](https://program-think.blogspot.com/2009/03/java-performance-tuning-0-overview.html)是介绍性能，所以来讨论一下堆和栈在性能方面的差别（这个差异是很大滴）。堆相对进程来说是全局的，能够被所有线程访问；而栈是线程局部的，只能本线程访问。打个比方，栈就好比个人小金库，堆就好比国库。你从个人小金库拿钱去花，不需要办什么手续，拿了就花，但是钱数有限；而国库里面的钱虽然很多，但是每次申请花钱要打报告、盖图章、办 N 多手续，耗时又费力。

　　同样道理，由于堆是所有线程共有的，从堆里面申请内存要进行相关的加锁操作，因此申请堆内存的复杂度和时间开销比栈要大很多；从栈里面申请内存，虽然又简单又快，但是栈的大小有限，分配不了太多内存。 　　可能有同学又问了，干嘛把两种类型分开存储，干嘛不放到一起捏？这个问题问得好！下面我们就来揣测一下，当初 Java 为啥设计成这样。

　　当年 Java 它爹（[James Gosling](https://en.wikipedia.org/wiki/James_Gosling)）设计语言的时候，对于这个问题有点进退两难。如果把各种东东都放置到栈中，显然不现实，一来栈是线程私有的（不便于共享），二来栈的大小是有限的，三来栈的结构也间接限制了它的用途。那为啥不把各种东东都放置到堆里面捏？都放堆里面，倒是能绕过上述问题，但是刚才也提到了，申请堆内存要办很多手续，太繁琐。如果仅仅在函数中写一个简单的“int n = 0;”，也要到堆里面去分配内存，那性能就大大滴差了（要知道 Java 是1995年生出来的，那年头俺买了台 PC 配【4兆内存】就属豪华配置了）。

　　左思右想之后，Java 它爹只好做了一个折中：把类型分为“基本类型”和“引用类型”，两者使用不同的创建方式。这种差异从 Java 语法上也可以看出来：引用类型总是用 new 创建对象（提醒一下：某些单键对象/单例对象，表面上没用 new，但是在 getInstance() 内部也还是用 new 创建的）；而基本类型则【不需要】用 new 来创建。 　　顺便跑题一下，斗胆评价 Java 它爹这种设计的弊端（希望 Java Fans 不要跟我急）。我个人认为：这个折中的决策，带来了许多深远的影响，随手举出几个例子： 1、由于基本类型不是派生自 Object，因此不能算是纯种的对象。这导致了 Java 的“【纯】面向对象”招牌打了折扣（当年 Sun 老是吹嘘 Java 是“纯”OO 的语言，其实 Java 的 OO 是不够纯粹滴）。 2、由于基本类型不是派生自 Object，出于某些场合（比如容器类）的考虑，不得不为每个基本类型加上对应的包装类（比如 Integer、Byte 等），使得语言变得有点冗余。  
　　从上述的介绍，我们应该明白，使用 new 创建对象的开销是【不小】的。在程序中能避免就应该尽量避免。另外，使用 new 创建对象，不光是创建时开销大，将来垃圾回收时，销毁对象也是有开销的（关于 GC 的开销，咱们会在后面的帖子细谈）。[下一个帖子](https://program-think.blogspot.com/2009/03/java-performance-tuning-2-string.html)，我们找一个例子来实战一下。

[回到本系列的目录](https://program-think.blogspot.com/2009/03/java-performance-tuning-0-overview.html#index)

