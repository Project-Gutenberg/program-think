---
layout: default
title: 'C++ 的可移植性和跨平台开发[1]&#65306;编译器'
date: None
author:
    display_name: 
---

　　在跨平台的开发过程中，很多问题都和编译器有关。因此我们先来聊聊编译器相关的问题。 　　首先，GCC 是优先要考虑支持的，因为几乎所有操作系统平台都有 GCC 的实现。它基本上成了一个通用的编译器了。如果你的代码在 A 平台的 GCC 能够编译通过，之后拿到 B 平台用类似版本的 GCC 编译，一般也不会有太大问题。因此 GCC 是肯定要考虑支持的。 　　其次，要考虑是否支持本地编译器。所谓本地编译器就是操作系统厂商自产的编译器。 　　举例来说： 相对于 Windows 的本地编译器就是 Visual C++ 相对于 Solaris 的本地编译器就是 SUN 的 CC 　　如果你对性能比较敏感或者想用到某些本地编译器的高级功能，可能就得考虑在支持 GCC 的同时也支持本地编译器。 　　编译器是程序员的朋友，很多潜在的问题（包括可移植性），编译器都是可以发现并给出警告的。如果你平时注意这些警告信息，可以减少很多麻烦。 　　因此俺强烈建议： 1. 把编译器的警告级别调高； 2. 【不要】轻易忽略编译器的警告信息。  
　　从没听说过“交叉编译器”的同学，可以先看“[维基百科的介绍](https://en.wikipedia.org/wiki/Cross-compiling)”。  
　　通俗地说，就是在 A 平台上编译出运行在 B 平台上的二进制程序。假设你要开发的应用是运行在 Solaris上，但是你手头没有能够运行 Solaris的 SPARC 机器，这时候交叉编译器就可以派上用场了。一般情况下都使用 GCC 来制作一个交叉编译器，限于篇幅，这里就不深入聊了。有兴趣的同学可以参见“[这篇文档](http://www.nongnu.org/thug/cross.html)”。

　　关于编译器的话题，暂时聊到这，后面聊聊关于“[语法](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-2-language.html)”的问题。

[回到本系列的目录](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-0-overview.html#index)

