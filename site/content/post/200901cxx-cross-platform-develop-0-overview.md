---
layout: default
title: 'C++ 的可移植性和跨平台开发[0]&#65306;概述'
date: None
author:
    display_name: 
---

　　今天聊聊 C++ 的可移植性问题。如果你平时使用 C++ 进行开发，并且你对 C++ 的可移植性问题不是非常清楚，那么建议你看看这个系列。即使你目前没有跨平台开发的需要，了解可移植性方面的知识对你还是很有帮助的。 　　C++ 的可移植性这个话题很大，包括了编译器、操作系统、硬件体系等很多方面，每一个方面都有很多内容。鉴于本人能力、精力都有限，只能介绍每一个方面最容易碰到的问题，供大伙儿参考。 　　后面我会分别从编译器、C++ 语法、操作系统、第三方库、辅助工具、开发流程等方面进行介绍。 为了方便阅读，把本系列帖子的目录整理如下：

1\. [编译器](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-1-compiler.html)

  
2\. [语法](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-2-language.html)  
3\. [异常处理](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-3-exception.html)  
4\. [硬件体系](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-4-hardware.html)  
5\. [操作系统](https://program-think.blogspot.com/2009/02/cxx-cross-platform-develop-5-os.html)  
6\. [多线程](https://program-think.blogspot.com/2009/04/cxx-cross-platform-develop-6-thread.html) 7. （未完待续）

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[每周转载：IT 大牛谈编程语言（网文3篇）](https://program-think.blogspot.com/2012/05/weekly-share-5.html)》  
《[如何成为优秀开发人员](https://program-think.blogspot.com/2009/01/0.html)》（系列）

