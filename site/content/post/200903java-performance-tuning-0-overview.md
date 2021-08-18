---
layout: default
title: 'Java 性能优化[0]&#65306;概述'
date: None
author:
    display_name: 
---

　　考虑写性能优化系列，主要是因为之前看到了太多性能其烂无比的 Java 代码（有些代码看得俺口瞪目呆）。很多 Java 程序员在写程序时，由于不太了解 JVM 及语言本身的一些运作机制，从而导致了代码的性能出现【严重】问题（性能差一个数量级以上，我才称为“严重”）。  
　　虽然网上也有针对 Java 性能的介绍，但是很多内容都仅仅告诉读者“该这么做”，而没有讲“为什么该这么做”。典型的例子就是关于 String 和 StringBuffer（StringBuilder），光介绍如何用，却没有说为什么这样用。这种现象导致了很多 Java 程序员只知其然，不知其所以然。所以本系列帖子会尽量介绍一些“所以然”的东东（也就是[学习技术三部曲](https://program-think.blogspot.com/2009/02/study-technology-in-three-steps.html)的 HOW 和 WHY），希望对 Java 程序员有所帮助。  
　　先初步考虑聊如下几个话题：

1\. [基本类型 vs 引用类型](https://program-think.blogspot.com/2009/03/java-performance-tuning-1-two-types.html)

  
2\. [字符串过滤实战](https://program-think.blogspot.com/2009/03/java-performance-tuning-2-string.html)  
3\. [关于垃圾回收（GC）](https://program-think.blogspot.com/2009/04/java-performance-tuning-3-gc.html)  
4\. [finalize函数](https://program-think.blogspot.com/2009/06/java-performance-tuning-4-finalize.html) 5. （未完待续）

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[每周转载：IT 大牛谈编程语言（网文3篇）](https://program-think.blogspot.com/2012/05/weekly-share-5.html)》  
《[如何成为优秀开发人员](https://program-think.blogspot.com/2009/01/0.html)》（系列）

