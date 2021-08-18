---
layout: default
title: 'C++ 的可移植性和跨平台开发[3]&#65306;异常处理'
date: None
author:
    display_name: 
---

　　上一个帖子“[语法](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-2-language.html)”由于篇幅有限，没来得及聊异常，现在把和异常相关的部分单独拿出来说一下。 　　早期的老式编译器生成的代码，如果 new 失败会返回空指针。俺当年用的 Borland C++ 3.1 似乎就是这样的。如今这种编译器应该不多见了，万一你在用的编译器还有这种行为，那你就惨了。碰到这种老式编译器，可以考虑重载 new 操作符来抛出 bad\_alloc 异常，便于进行异常处理。 　　稍微新式一点的编译器，就不是仅仅返回空指针了。当 new 操作符发现内存告急，按照标准的规定（参见 C++ 03 标准 18.4.2章节），它应该去调用 new\_handler 函数（原型为 typedef void (\*new\_handler)();）。标准建议 new\_handler 函数干如下三件事： 1. 设法去多搞点内存来 2. 抛出 bad\_alloc 异常 3. 调用 C++ 标准库的 abort() 或 exit() 来退出进程 　　由于 new\_handler 函数是可以被重新设置的（通过调用 set\_new\_handler），所以上述几种行为都可能出现。 　　综上所述，new 分配内存失败，有可能三种可能： 1. 返回空指针 2. 抛出异常 3. 进程立即终止 　　如果你希望你的代码具有较好的移植性，你就得把这三种情况都考虑到。  
　　异常规格在俺看来不是一个好东西，不信可以去看看《[C++ Coding Standards - 101 Rules, Guidelines & Best Practices](https://program-think.blogspot.com/2009/01/cxx-coding-standards-101-rules.html)》的第75条。（具体有哪些坏处以后专门开一个 C++ 异常和错误处理的帖子来聊） 　　言归正传，按照标准（参见 C++ 03 标准 18.6.2章节），如果一个函数抛到外面的异常没有包含在该函数的异常规范中，那么应该调用 unexcepted()。但是并非所有编译器生成的代码都遵守标准（比如某些版本的 VC 编译器）。如果你的需要支持的编译器在异常规范上的行为不一致，那就得考虑：从你的代码中去掉所有的异常规范声明。 　　（先声明：此处说的“模块”是指动态库） 　　如果你的工程中包含了动态库，【不要】把异常抛到模块的导出函数之外。 　　毕竟现在 C++ 还没有 ABI 标准（估计将来也未必会有），跨模块抛出异常会有很多不可预料的行为。 　　如果你从来没有听说过 SEH，那就当俺没说，跳过这段。 　　如果你以前习惯于用 SEH，在你打算写跨平台代码之前，要改掉这个习惯。包含有 SEH 的代码只能在 Windows 平台上编译通过（肯定无法跨平台的）。 　　照理说，catch(...) 语句只能够捕获 C++ 的异常类型，对于访问违例、除零错等非 C++ 异常是无能为力的。但是某些情况下（比如某些 VC 编译器），诸如“访问违例、除零错”之类的异常，也可以被 catch(...) 所捕获。 　　所以，你如果希望代码的可移植性好，就不能在程序逻辑中依赖上述 catch(...) 的行为——换句话说：你【不能】指望 catch(...) 来捕获“访问违例、除零错”之类的非 C++ 异常。

　　下一个帖子，准备聊一下和“[硬件有关的跨平台问题](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-4-hardware.html)”。

[回到本系列的目录](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-0-overview.html#index)

