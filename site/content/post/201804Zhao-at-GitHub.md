---
layout: default
title: '曝光天朝权贵家族&#8212;&#8212;新鲜出炉的&#12304;太子党关系网络&#12305;'
date: None
author:
    display_name: 
---

　　开篇先吟诗一首 :) 这诗描写的就是咱们天朝的权贵们。  

> 办好护照绿卡，子女送到国外， 赃款洗钱转移，欧美购买豪宅； 打仗要有后路，进退百战不殆， 如有风吹草动，登机咱就拜拜； 嘴上高喊坚持，心里知道好坏，
> 
> 不去古巴朝鲜，谁去谁是痴呆。

　　话说今年是朝廷换届的年份（5年一次），所以俺必须在今年两会结束后，升级一下《太子党关系网络》，以便跟上时代的潮流。

　　前段时间比较忙，一直到最近10天才抽出时间，终于完成《太子党关系网络》的升级版本。

　　2年前（2016），俺已经把《太子党关系网络》开源到 GitHub 上——创建了一个名叫 zhao 的项目（大伙儿应该明白这名儿是啥意思） 　　这几天的更新，内容还比较丰富——增加了20多个家族（累计达到159个家族），增加了上百个自然人（累积达到826人）。 　　想先睹为快的同学，请猛击如下链接：

**[https://github.com/programthink/zhao](https://github.com/programthink/zhao)**

　　不得不说，GitHub 是如今全球最好的多人协作平台——关于这点，有空的话可以来聊一下。

　　更难能可贵的是——**至今依然是【免翻墙】可以访问**。而且 GitHub 公司的管理层还是有点骨气——至少目前为止没有向咱们朝廷献媚或妥协。

　　所以很自然地，俺就决定用 GitHub 来托管开源的《太子党关系网络》，顺便还可以利用 GitHub 的多人协作功能。  
　　考虑到大部分同学都比较懒，俺在本项目中放了一个 **download** 目录，把制作好的格式（主要是 jpg 和 pdf）放在上面供大伙儿下载。 　　由于 jpg 是图片格式，即使不下载，也可以在浏览器中直接看；至于 pdf 格式，俺用 firefox 测试了一下，也是可以【在线浏览】（其它浏览器是否可以，俺不清楚）。 　　（有件事情忘记了说明。本文发出之后，看到某些读者的留言反馈，俺才想起来，赶紧补上这段）

　　话说2016年这个项目上线之后，引发朝廷的恐慌。于是，朝廷方面利用某个新成立的【半官方】组织（中国网络空间安全协会）向 GitHub 的网管发去一份“删除令”（其内容参见[这个链接](https://github.com/github/gov-takedowns/blob/master/China/2016/2016-06-08-programthink-zhao.md)）。目前 GitHub 网管的做法是——把俺这个项目进行【选择性屏蔽】。也就是说：**当你从墙内访问俺这个项目，会看到一段洋文，说该项目暂时不可用；但如果你通过【翻墙的方式】，从墙外访问这个项目，依然可以正常访问，正常下载。**

  
　　**针对俺项目的政府删除令，是 GitHub 历史上的第6个，也是来自中国政府的【第一个】**。（前面5个删除令都是来自俄罗斯政府，详情参见 GitHub 官方的[这个链接](https://github.com/github/gov-takedowns)）。  
　　关于此事的更多介绍，请看：《[热烈庆贺“太子党关系网络”开源项目率先获得朝廷认证](https://program-think.blogspot.com/2016/06/github-take-down-zhao-repository.html)》 　　如果你也想帮忙揭露权贵家族，欢迎参与这个项目！！！ 　　前提是——你要有 GitHub 帐号，并且了解其基本功能（比如 Pull Request 的使用）。  
　　**首先，一定要注意个人安全。**因为参与这个项目相当于——恶毒攻击党和国家领导人——这是有政治风险滴。  
　　想要参与此项目的同学，一定要做好匿名工作——强烈建议你先看完俺写的系列《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》。然后再看一下《[使用 GitHub 的几种方式——兼谈安全性和隐匿性的经验](https://program-think.blogspot.com/2016/03/GitHub-Security-Tips.html)》 　　原先俺制作《太子党关系网络》用的是 dot 来生成 PDF。之前也有读者建议俺直接把 dot 脚本开源。但是俺没有这么干。

　　俺这次开源的是基于 [YAML 格式](https://zh.wikipedia.org/wiki/YAML)的原始数据（在该项目的“data”目录下），然后俺提供一个 python 脚本来自动生成 dot 脚本，最后再调用 Graphviz 导出各种格式（比如：pdf、jpeg、svg 等等）。

　　为啥俺选择用 yaml 格式捏？因为这种格式非常通俗易懂、非常简洁明了，这有利于完全不懂技术的网民，参与编辑这些数据文件。 　　而且俺还在每一个 yaml 格式的数据文件中写了很详细的注释，便于其他网友修改。

　　更多的介绍，请参见[项目首页](https://github.com/programthink/zhao)。

　　刚才提到了 dot 和 Graphviz，关于这两个玩意儿，俺专门写了一篇扫盲教程，参见：

《[开源项目：【自动】绘图工具 Graphviz——《太子党关系网络》就是用它制作](https://program-think.blogspot.com/2016/02/opensource-review-graphviz.html)》

　　看完这篇教程，你大概就能玩转 Graphviz 了。 　　当年曾经设想过：制作一个《太子党关系网络》的 Web 版本，也放在 GitHub 上。可惜俺比较懒，一直没动手开干 :( 　　关于“后续的计划”，大伙儿可以集思广益（欢迎到本文留言，提出你的建议）。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[热烈庆贺【太子党关系网络】开源项目率先获得朝廷认证](https://program-think.blogspot.com/2016/06/github-take-down-zhao-repository.html)》  
《[【太子党关系网络】开源到 GitHub——大伙儿一起来曝光赵国权贵](https://program-think.blogspot.com/2016/02/Zhao-at-GitHub.html)》  
《[曝光天朝权贵——【太子党关系网络】2.2 版本发布](https://program-think.blogspot.com/2015/02/Princelings.html)》  
《[曝光天朝权贵——【太子党关系网络】2.0 版本发布](https://program-think.blogspot.com/2013/03/princelings.html)》  
《[曝光天朝权贵——【太子党关系网络】1.0 版本发布](https://program-think.blogspot.com/2012/11/princelings.html)》  
《[分析“制度性腐败”——为啥天朝的贪官屡禁不止？](https://program-think.blogspot.com/2014/07/corruption-and-form-of-government.html)》  
《[相当奇葩的天朝，【劫贫济富】的国度](https://program-think.blogspot.com/2018/07/Robbing-the-Poor-Funding-the-Rich.html)》  
《[点评中国社会九大阶层——没有公平、难以流动、无法稳定](https://program-think.blogspot.com/2013/12/chinese-social-stratification.html)》  
《[聊聊“赵家人”走红网络的重要意义](https://program-think.blogspot.com/2016/01/Zhao-Family.html)》

