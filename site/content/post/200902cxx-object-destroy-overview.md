---
layout: default
title: 'C++ 对象是怎么死的&#65311;为什么要写这个系列&#65311;'
date: None
author:
    display_name: 
---

　　要说 C++ 对象是怎么死的，得先从 C++ 的析构函数说起。这玩意儿是我本人很喜欢的一个语言特性（可惜有好几个语言没有类似的玩意儿，具体就不点名了，免得引发口水战）。我们可以利用 C++ 的构造和析构函数，来实现 Guard 模式，写出比较清晰、简练和异常安全的代码。由于 Guard 模式在 C++ 程序中运用挺多，所以保证【**所有对象被析构**】就是一个很重要很严肃的问题。  
　　另外，我发现很多 C++ 程序员只关心内存泄露问题，不关心（或不清楚）资源泄露问题（很类似于我在“[Java新手通病\[3\]](https://program-think.blogspot.com/2009/02/defect-of-java-beginner-3-code-style.html#gc)”提到的现象）。比如昨天的《[C++对象是怎么死的？进程篇](https://program-think.blogspot.com/2009/02/cxx-object-destroy-with-process.html)》发布后，就有同学问了：进程死都死了，对象没销毁又有什么关系捏？其实大有关系啊！虽然操作系统会在进程死后帮它收尸（也就是把某些资源，比如内存进行回收），基本不用担心内存泄露的问题。但是别忘了，除了内存资源，进程中可能还包含有其它业务层面的资源，而这些资源，操作系统是不会帮你自动回收的。所以我要再啰嗦一次：【**资源泄露往往比内存泄露要严重得多啊**】。啰嗦完之后，为了加深印象，再举如下一个例子。 　　比如某业务逻辑 Foo 需要操作大量的临时文件（放在某动态生成的临时目录中），为了保证该业务逻辑结束后（可能是正常结束，也可能中途抛出异常），该临时目录总是被删除，可以使用如下的 Guard 模式。

class CTempDirGuard
{
public: CTempDirGuard(const string& sFolderName) { // 创建某临时目录 } virtual ~CTempDirGuard() { // 把该临时目录整个儿删除 }
}; void Foo()
{ CTempDirGuard guard(xxx); // 声明guard对象 // 往临时目录放东西 // 不管是出现 return 语句还是有异常抛出，guard 都会被析构，因而该 xxx 目录会被删除 // 但是如果程序执行到此处，却发生进程的非自然死亡， // 在这种情况下，该 guard 对象将【不会】被析构——因此会留下一个垃圾目录，浪费了硬盘资源
}

  
　　鉴于上述所说的两个原因，所以我一直想写一个这方面的帖子。正好前几天写了帖子讨论“[架构设计的多进程问题](https://program-think.blogspot.com/2009/02/multi-process-vs-multi-thread.html)”，之后就就顺便写了一个帖子：《C++ 进程是怎么死的？》，讨论了一下由于进程不同的死法对C++对象析构的影响。等写完之后突然想到：除了进程终止的问题可能导致 C++ 对象的【不】正常析构，还有线程等其它因素也可能会让 C++ 对象【不】正常析构。所以干脆就改了个名，叫《C++ 对象是怎么死的？》 :-)  
另外，为了方便阅读，把本系列帖子的目录整理如下：

1、[进程篇](https://program-think.blogspot.com/2009/02/cxx-object-destroy-with-process.html)

  
2、[对标准输入输出流的进一步探讨](https://program-think.blogspot.com/2009/02/cxx-object-destroy-with-io-stream.html)  
3、[Win32 线程篇](https://program-think.blogspot.com/2009/03/cxx-object-destroy-with-thread-win32.html)  
4、[POSIX 线程篇（pthread）](https://program-think.blogspot.com/2009/03/cxx-object-destroy-with-thread-posix.html)

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[每周转载：IT 大牛谈编程语言（网文3篇）](https://program-think.blogspot.com/2012/05/weekly-share-5.html)》  
《[如何成为优秀开发人员](https://program-think.blogspot.com/2009/01/0.html)》（系列）

