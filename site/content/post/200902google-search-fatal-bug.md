---
layout: default
title: '从 Google 搜索的严重 bug 想开去'
date: None
author:
    display_name: 
---

　　昨天晚上用 Google 查资料，看到所有的搜索结果都注明是恶意站点。第一反应以为自己眼花了；然后开始怀疑我的浏览器出问题，换了几个浏览器都是老样子；后来又想，会不会是我的 ISP 在搞鬼。等了十多分钟没解决，只好换百度查资料...  
　　今天早上看新闻才知道居然是 Google 的【人为】失误，居然是全球性的，居然持续了40多分钟。以下是 Google 的官方说法（[原文连接](https://googleblog.blogspot.com/2009/01/this-site-may-harm-your-computer-on.html)）：  

> 谷歌表示他们一直在和一家非盈利组织 StopBadware.org 合作，通过这个组织给出的名单对各个URL进行存在恶意软件的信息标注。这个组织的恶意网站名单是人工审核并添加，所以这份名单是人为生成而不是算法生成的。谷歌昨晚进行列表更新时，在下载回来的名单里，错误的出现了"/"这个URL地址，所以错误的将所有地址判断为恶意网站。

　　比较有戏剧性的是，Google 提到的“非盈利组织 StopBadware.org”也发表声明：  
谷歌的恶意网站列表并非是我们提供的，而是其自己生成的。 　　这件事情改变了我对 Google 的几个看法。

　　第1点：虽然我很看不起中国谷歌，但是美国 Google 在我看来一直是一个**优秀**的公司。现在它居然出现这么低级的错误（开发过商业Web网站的，应该都知道这有多低级），而且持续40多分钟才搞定。看来 Google“**优秀**”的名声要打折扣了。

  
　　第2点：假如 StopBadware 的说法成立，那我就得怀疑 Google 的诚信了。是否 Google 有意推卸责任给其它组织机构？看来 Google“**不做恶**”的名声要打折扣了。  
　　第3点：Google 一直声称他的所有数据收集、处理、存储都是依靠程序进行的，不会涉及人工干预。我以前也一直猜测 Google 的恶意站点列表是依靠诸如神经网络、遗传算法、等等牛逼的算法来搞定的，现在 Google 居然承认是靠手工审核添加。看来 Google“**不采用人工干预**”的名声要打折扣了。 　　第4点：Google 一直在推动云计算，希望大伙儿尽可能地把桌面应用搬上云端。我本来觉得云计算这玩意也挺不错的（优点多多）。现在出了这档子事，我就得谨慎考虑一下了。假如我的个人数据都委托给 Google 代管，万一 Google 出个什么纰漏（比如被 Hacker 搞了），那可就悬了。
