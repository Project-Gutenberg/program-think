---
layout: default
title: 'C++ 对象是怎么死的&#65311;Win32 线程篇'
date: None
author:
    display_name: 
---

　　在[前面的帖子](https://program-think.blogspot.com/2009/02/cxx-object-destroy-with-process.html)里聊完了进程终止对C++对象析构的影响。今天咱们来说一下线程对于C++对象析构的影响。  
　　由于 C++ 03 标准【没有】包含线程的概念，而（截至写本文时）C++ 0x 尚未正式发布。所以对线程的讨论只好根据特定的操作系统平台来谈。对于操作系统自带的线程 API，目前比较流行的款式是 Windows 平台提供的线程 API 和 POSIX 平台上的 pthread API。但是这两种线程 API 的差异实在是太大，没法拿出来一起聊。我只好把“线程篇”的帖子再拆分一下，今天先来聊一聊 Win32 的线程 API（下一篇再聊 pthread）。  
　　另外，对于进行跨平台开发的同学，应该已经用上了某些跨平台的第三方线程库（比如 ACE、Boost ...），对于这些库的介绍，初步打算放到“[C++的可移植性和跨平台开发](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-0-overview.html)”系列中。 　　本来照例要先介绍线程的几种死法，但是考虑到很多 Windows 程序员经常混淆线程 API，搞不清楚到底该用哪个。所以先来说一下两套线程 API 的问题。 　　首先，Windows 操作系统本身提供了线程的创建函数 CreateThread 和销毁函数 ExitThread。顾名思义，其中的 CreateThread 用于创建线程，ExitThread 用于在线程函数内部退出线程（也就是自杀）。 　　其次，在 Visual C++ 自带的 C 运行库（以下简称 CRT）中，还带了另外4个 API 函数，分别是：\_beginthread，\_endthread，\_beginthreadex，\_endthreadex。其中的 \_beginthread 和 \_beginthreadex 用于创建线程（它们内部调用了 CreateThread ），而 \_endthread 和 \_endthreadex 用于自杀（它们内部调用了 ExitThread）。 　　某些同学看到这里，被搞懵了，心想：“干嘛要搞这么多玩意儿出来糊弄人？有 CreateThread 和 ExitThread 不就够了嘛！”其实你有所不知，此中大有奥妙啊！ 　　OS API 作为操作系统本身提供的 API 函数，它被设计为语言无关的。它们不光可以被 C++ 调用，还可以被其它诸如 VB、Python、Delphi 等开发语言来调用。所以它们不会（也不能够）帮你处理一些和具体编程语言相关的琐事。 　　而 CRT API 虽然最终还是要调用 OS API 来完成核心的功能，但是 CRT API 可以在不知不觉中多帮我们干了一些虽琐碎但重要的工作。（如果同学们想窥探一下 CRT API 内部都干了些啥，可以拜读一下 Win32 编程的经典名著《Windows 核心编程》的 6.7章节，里面介绍得挺细致的）

　　费了这么多口水，无非是要同学们牢记：以后在 Windows 平台下开发多线程程序，【**千万不要**】直接使用这两个线程 API（也就是 CreateThread 和 ExitThread），否则后果自负 :-)

　　另外，顺便补充一下。除了上述提到的 CRT 库。其它一些 Windows 平台的 C++ 库也可能提供了线程的启动函数（比如 MFC 的 AfxBeginThread），这些函数也对 OS API 进行了包装，所以它们用起来也是安全滴。 　　说完了两套 API，开始来讨论一下线程的几种死法。线程和进程一样，也有三种死法。详见如下：  
　　一般来说，每个线程都会对应某个函数（以下称为“线程函数”）。线程函数是线程运行的主体。所谓的“自然死亡”，就是通过**return**语句结束线程函数的执行。  
　　所谓的“自杀”，就是当前线程通过调用某 API 把【自己】给停掉。前面已经说了 OS API 的坏话，同学们应该明白【**不能**】再用它们。那我们能否使用 CRT API 来进行自杀呢？请看 [MSDN 上的相关文档](http://msdn.microsoft.com/en-us/library/hw264s73.aspx)。上面说了，如果使用 \_endthread 或 \_endthreadex，将导致析构函数【**不被调用**】。 　　所谓的“它杀”，很明显，就是其它线程通过调用某 API 把当前线程给【强行】停掉。对于 Windows 平台来说，实现“它杀”比较简单，使用 TernimateThread 就直接干掉了（它杀也是三种里面最野蛮的）。  
　　照[前一个帖子](https://program-think.blogspot.com/2009/02/cxx-object-destroy-with-process.html)的风格，还是把类对象分为三种：局部非静态对象、局部静态对象、非局部对象（全局对象）。 　　由于“非局部对象”是在 main 之前就创建、在进程死亡时析构，暂时与线程扯不上太大关系。剩下的两种局部对象，在宿主线程（所谓宿主线程，就是创建该局部对象的线程）死亡时会受到什么影响捏？请看如下的对照表： －－－－－－－－－－－－－－－－－－－－－－－－－－ ｜　　　　　｜　局部非静态对象　｜　局部静态对象　｜ ｜自然死亡　｜　能　　　　　　　｜　能　　　　　　｜ ｜自杀　　　｜　不能　　　　　　｜　能　　　　　　｜ ｜它杀　　　｜　不能　　　　　　｜　能　　　　　　｜ －－－－－－－－－－－－－－－－－－－－－－－－－－ 　　从上述结果可以看出，Windows 上线程的死法还是以自然死亡为最安全，这点和进程的死法类似。所以同学们在 Windows 上开发时，要尽量避免自杀和它杀。 　　所谓“主线程”，就是进程启动时，操作系统为该进程默认创建的【第一个】线程。通俗地说，可以把 main 函数看成是主线程的线程函数。 　　“主线程之死”是很有讲究的。由于前面已经阐述了非自然死亡的坏处，所以我们只讨论主线程自然死亡这一种情况。当主线程自然死亡时（也就是用 return 从 main 返回时），会导致 exit 函数被调用，然后 exit 函数就会开始清除当前进程的各种资源，为进程的死亡作准备。这时候，如果还有其它活着的线程，也会被一起干掉（其效果类似于它杀）。 　　为了防止出现上述情况，主线程一定要负责最终的善后工作——换句话说：务必等到其它线程都死了，主线程才能死。

　　Windows 平台上，有关线程的对象析构问题，就聊到这。[下一个帖子](https://program-think.blogspot.com/2009/03/cxx-object-destroy-with-thread-posix.html)，咱们来聊一下 pthread 相关的对象析构话题。

