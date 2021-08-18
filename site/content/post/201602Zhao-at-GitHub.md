---
layout: default
title: '&#12304;太子党关系网络&#12305;开源到 GitHub&#8212;&#8212;大伙儿一起来曝光赵国权贵'
date: None
author:
    display_name: 
---

　　春节前承诺的事情，今天兑现了，赶在二月份结束前——还好今年是闰年 :) 　　简而言之，俺把这几年整理的《太子党关系网络》的原始数据开放到 GitHub 上，以便今后进行多人协作。 　　顺便说一下：赶在二月底之前完成此事还有一个重大意义——马上要开两会了，这是俺为“两会”提供的献礼 :) 　　俺在 GitHub 创建了一个名叫 zhao 的项目——大伙儿应该明白这是啥意思 :) 　　感兴趣的同学，请猛击如下链接：

**[https://github.com/programthink/zhao](https://github.com/programthink/zhao)**

　　截止发本篇博文时，俺已经把所有的文本数据文件都上传了（累计700多个文件，对应700多人）。这几年，俺花了不少时间整理这些，可辛苦啦 :(

　　另外还有200多张头像，因为图片比较大，批量提交总是传到一半就断线（貌似用 SSH 操作 GitHub 是【没有】断点续传的）。  
　　所以，今天估计来不及上传了。接下来两天，俺找个网速快的时候，上传一下。

  
　　**发博文的次日上午，俺已经把所有图片（头像）也成功上传到 GitHub** 　　不得不说，GitHub 是如今全球最好的多人协作平台——关于这点，有空的话可以来聊一下。 　　更难能可贵的是——至今依然是【免翻墙】可以访问。而且 GitHub 的管理层还是有点骨气——至少目前为止没有向咱们朝廷献媚或妥协。

　　所以很自然地，当 Google Code 关闭之后，俺就改用 GitHub 来托管本人整理的一些资源（比如：“[电子书清单](https://github.com/programthink/books)”和“[开源项目清单](https://github.com/programthink/opensource)”）

  
（参见：《[俺的 GitHub 开张——原 Google Code 的 wiki 页面已迁移至此](https://program-think.blogspot.com/2015/06/My-GitHub.html)》） 　　这次开源《太子党关系网络》，就更加要用 GitHub 了——俺希望利用 GitHub 的多人协作功能。 　　如果你也想帮忙，非常欢迎参与这个项目！！！ 　　但是一定要注意个人安全。因为参与这个项目相当于——恶毒攻击党和国家领导人——这是有政治风险滴。

　　想要参与此项目的同学，一定要做好匿名工作——强烈建议你先看完俺写的系列《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》。然后再看一下《[使用 GitHub 的几种方式——兼谈安全性和隐匿性的经验](https://program-think.blogspot.com/2016/03/GitHub-Security-Tips.html)》

　　原先俺制作《太子党关系网络》用的是 dot 来生成 PDF。之前也有读者建议俺直接把 dot 脚本开源。但是俺没有这么干。

　　俺这次开源的是基于 [YAML 格式](https://zh.wikipedia.org/wiki/YAML)的原始数据（在该项目的“data”目录下），然后俺提供一个 python 脚本来自动生成 dot 脚本，最后再调用 Graphviz 导出各种格式（比如：pdf、jpeg、svg 等等）。

　　为啥俺选择用 yaml 格式捏？因为这种格式非常通俗易懂、非常简洁明了，这有利于完全不懂技术的网民，参与编辑这些数据文件。 　　而且俺还在每一个 yaml 格式的数据文件中写了很详细的注释，便于其他网友修改。

　　更多的介绍，请参见[项目首页](https://github.com/programthink/zhao)。

　　刚才提到了 dot 和 Graphviz，关于这两个玩意儿，俺在上周已经专门写了一篇扫盲教程，参见：

《[开源项目：【自动】绘图工具 Graphviz——《太子党关系网络》就是用它制作](https://program-think.blogspot.com/2016/02/opensource-review-graphviz.html)》

　　看完这篇教程，你大概就能玩转 Graphviz。 　　如果你懒得折腾，也没关系。

　　俺在本项目中放了一个 **download** 目录，把制作好的格式（主要是 jpg 和 pdf）放在上面让大伙儿下载。

　　再次唠叨一下：GitHub 是【免翻墙】的，你可以帮忙俺传播这个项目的网址（如下），让更多人了解权贵家族的嘴脸。

**[https://github.com/programthink/zhao](https://github.com/programthink/zhao)**

　　初步考虑制作一个《太子党关系网络》的 Web 版本，也放在 GitHub 上。关于这方面，大伙儿可以集思广益（欢迎到本文留言，提出你的建议）。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[【太子党关系网络】开源到 GitHub——大伙儿一起来曝光赵国权贵](https://program-think.blogspot.com/2016/02/Zhao-at-GitHub.html)》  
《[曝光天朝权贵——【太子党关系网络】2.2 版本发布](https://program-think.blogspot.com/2015/02/Princelings.html)》  
《[曝光天朝权贵——【太子党关系网络】2.0 版本发布](https://program-think.blogspot.com/2013/03/princelings.html)》  
《[曝光天朝权贵——【太子党关系网络】1.0 版本发布](https://program-think.blogspot.com/2012/11/princelings.html)》  
《[聊聊“赵家人”走红网络的重要意义](https://program-think.blogspot.com/2016/01/Zhao-Family.html)》  
《[分析“制度性腐败”——为啥天朝的贪官屡禁不止？](https://program-think.blogspot.com/2014/07/corruption-and-form-of-government.html)》  
《[点评中国社会九大阶层——没有公平、难以流动、无法稳定](https://program-think.blogspot.com/2013/12/chinese-social-stratification.html)》  
《[相当奇葩的天朝，【劫贫济富】的国度](https://program-think.blogspot.com/2018/07/Robbing-the-Poor-Funding-the-Rich.html)》  
《[开源项目：【自动】绘图工具 Graphviz——【太子党关系网络】就是用它制作](https://program-think.blogspot.com/2016/02/opensource-review-graphviz.html)》  
《[使用 GitHub 的几种方式——兼谈安全性和隐匿性的经验](https://program-think.blogspot.com/2016/03/GitHub-Security-Tips.html)》  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》（系列）

