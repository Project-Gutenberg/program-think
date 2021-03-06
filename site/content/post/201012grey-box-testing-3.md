---
layout: default
title: '如何开展灰盒测试[3]&#65306;模块接口类型概述'
date: None
author:
    display_name: 
---

　　经过前面几个帖子的铺垫（或许有些网友认为俺是卖关子:），今天开始介绍技术方面的话题。  
　　在[前面的帖子](https://program-think.blogspot.com/2010/11/grey-box-testing-1.html)里，俺提到过【基于脚本】的灰盒测试。后面聊具体的技术手段时，会侧重于 Python 脚本（这正好可以跟俺写的另一个系列《[为什么俺推荐 Python](https://program-think.blogspot.com/2009/08/why-choose-python-0-overview.html)》遥相呼应）。当然啦，为了照顾那些不用 Python 的同学，其它的技术手段，俺也会顺带提一下。 　　关于 Python 的版本，（截至到目前）有两个系列：2.x版本 和 3.x版本。这两种版本不但在语法上有一定的差异，而且内置的标准库也有不同。（截止俺写本文时）Python 的开源项目，还是以2.x版本居多，所以俺后续在介绍 Python 脚本实现时，也会侧重于2.x版本。 　　由于灰盒测试的技术实现，是一个比较大的话题，涉及面会比较宽。为了保持一定的条理性，避免大伙儿看着看着就迷糊了，俺打算根据模块的接口类型（也就是模块间的交互类型）来叙述。每种类型，单独开一个帖子来具体介绍。  
　　如果从进程的角度来看，交互双方的模块可能在同一个进程，也可能在不同的进程。因此，模块间的交互可以分为“进程内”、“跨进程”两大类（不知**进程**为何物，请看[这里](https://zh.wikipedia.org/wiki/%E8%A1%8C%E7%A8%8B)的介绍）。对于进程间的交互，还专门有一个洋文的缩写——[IPC](https://en.wikipedia.org/wiki/Inter-process_communication)。 　　如果从机器的角度看，交互的双方可能在同一个主机，也可能在不同的主机。因此，模块间的交互类型还可以分为“主机内”、“跨主机”两大类。“主机间”的交互，必定也是“跨进程”的。反之则【不然】。

　　顺便提一下：如果从耦合的角度来看，跨主机的交互比主机内的交互，耦合低；跨进程的交互比进程间的交互，耦合低。（不知“耦合”为何物的同学，请看[这里](https://zh.wikipedia.org/wiki/%E8%80%A6%E5%90%88%E6%80%A7_%28%E8%A8%88%E7%AE%97%E6%A9%9F%E7%A7%91%E5%AD%B8%29)的介绍）

　　由于不存在“跨主机不跨进程”的接口方式，所以上述两种分类维度排列组合之后，有3种可能。每种俺单独开一个帖子，请看：

[接口测试实战——跨主机的交互方式](https://program-think.blogspot.com/2010/12/grey-box-testing-4.html)

接口测试实战——主机内的跨进程交互方式 接口测试实战——进程内的交互方式

[回到本系列的目录](https://program-think.blogspot.com/2010/11/grey-box-testing-0.html#index)

