---
layout: default
title: 'C++ 的可移植性和跨平台开发[4]&#65306;硬件体系'
date: None
author:
    display_name: 
---

　　这次聊的话题主要是和硬件体系有关的。比如你的程序需要支持不同类型的 CPU（x86、SPARC、PowerPC），或者是同种类型不同字长的 CPU（比如 x86、amd64），这时候你就需要关心一下硬件体系的问题。 　　C++ 中基本类型的大小（占用的字节数）会随着 CPU 字长的变化而变化。

　　所以，假如你要表示一个 int 占用的字节数，千万不要直接写“**4**”（顺便说一下，直接写“**4**”还犯了 Magic Number 的大忌，详见[这篇](https://program-think.blogspot.com/2009/02/defect-of-java-beginner-3-code-style.html#magic_number)），而应该写“**sizeof(int)**”；

  
　　反过来，如果你要定义一个大小【必须】为4字节的有符号整数，也不要直接用 int，而要用预先 typedef 好的【定长】类型（比如 [boost](http://www.boost.org/) 库提供的 int32\_t、[ACE](http://www.cs.wustl.edu/%7Eschmidt/ACE.html) 库提供的 ACE\_INT32 ...）。 　　差点忘了，指针的大小也有上述的问题，也要小心。  
　　如果你没听说过“字节序”这玩意儿，请看“[维基百科](https://en.wikipedia.org/wiki/Endianness)”。 　　通俗地打个比方，在一个大尾序的机器上有一个4字节的整数 0x01020304，通过网络或者文件传到一台小尾序的机器上就会变成 0x04030201；据说还有一种中尾序的机器（不过我没接触过），上述整数会变成 0x02010403。 　　如果你编写的应用程序中涉及网络通讯，一定要在记得进行主机序和网络序的翻译；如果涉及跨机器传输二进制文件，也要记得进行类似的转换。  
　　如果你不晓得“内存对齐”是什么东东，请看“[维基百科](https://en.wikipedia.org/wiki/Data_structure_alignment)”。 　　简单来说，出于 CPU 处理上的性能考虑，结构体中的数据不是紧挨着的，而是要空开一些间隔。这样的话，结构体中每个数据的地址正好都是某个字长的整数倍。 　　由于 C++ 标准中没有定义内存对齐的细节，因此，你的代码也不能依赖对齐的细节。凡是计算结构体大小的地方，都老老实实写上 sizeof()。 　　有些编译器支持 #pragma pack 预处理语句（可以用来修改对齐字长），不过这种语法【不是】所有编译器都支持，要慎用。 　　对于有符号整数的右移操作，有些系统默认使用算数右移（最高的符号位不变），有些默认使用逻辑右移（最高的符号位补0）。所以，【不要】对【有符号】整数进行【右移】操作。 　　顺便说一下，即使没有移植性问题，代码中也尽量少用移位运算符。那些企图用移位运算来提高性能的同学更要注意了，这么干不但可读性很差，而且吃力不讨好——如今的编译器，只要不太弱智，都会自动帮你搞定这种优化，无须程序员来操心。

　　下一个帖子，准备聊一下“[操作系统相关的跨平台问题](https://program-think.blogspot.com/2009/02/cxx-cross-platform-develop-5-os.html)”。

[回到本系列的目录](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-0-overview.html#index)

