---
layout: default
title: 'CNNIC 证书的危害及各种清除方法'
date: None
author:
    display_name: 
---

　　前几天已经写了2个帖子（分别是[扫盲数字证书的基本知识](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)，[CNNIC 干过的那些破事](https://program-think.blogspot.com/2010/02/about-cnnic.html)）作铺垫，终于开始来说正题——关于 CNNIC 的 CA 证书。  
  
　　从[前面的帖子](https://program-think.blogspot.com/2010/02/about-cnnic.html)，大伙应该都看出来，CNNIC 这个老流氓可是坏事做尽啊。最近这段时间，CNNIC 不甘寂寞，又在 CA 领域，搞了点小动作。今天先来说一下，这个老流氓又坑蒙拐骗了哪些主？ 　　可能某些IT圈外的同学会问，Mozilla是嘛玩意？简单地说，“Mozilla 和 Firefox 的关系”就好比“微软和 Windows 的关系”。因此，Firefox 自带哪些 CA 根证书，是由 Mozilla 组织决定滴。

　　话说2009年初那会儿，CNNIC 里面的某个员工（liu\_yan@cinic.cn）到 Mozilla 网站提交了一个申请：要求将 CNNIC 加入 Mozilla 的 CA 列表。此申请经过几个月的讨论。到了2009年底，审批获得通过。至此，CNNIC 正式成为 Mozilla 的 CA 之一（请看“[Mozilla官方的CA列表](https://www.mozilla.org/projects/security/certs/included/)”）。懂洋文的同学，请自行到“[这里](https://bugzilla.mozilla.org/show_bug.cgi?id=476766)”看详细的申请过程。

　　因此，从 Firefox 的3.6版本开始，其内置的诸多根证书中，将会包含 CNNIC 这个老流氓提供的根证书。  
　　说实在的，俺不清楚老流氓 CNNIC 是如何忽悠微软，让微软把它也加入到 Windows 内置的 CA 列表中的。不过这已经不重要了。现在，老流氓已经把它脏兮兮的触角，伸到了微软那儿。列位看官如若不信，可以去看“[微软的 CA 列表](http://download.microsoft.com/download/1/4/f/14f7067b-69d3-473a-ba5e-70d04aea5929/windows%20root%20certificate%20program%20members%20november%202009.pdf)”。 　　今后，如果你安装了微软新的操作系统，多半其已经包含了 CNNIC 的根证书；即便你一直使用老版本的 Windows，也可能在自动升级了某个 Windows 补丁之后，把 CNNIC 的根证书带到你的电脑中。 　　除了 Mozilla 和微软，还有一个组织也被 CNNIC 牵连了，那就是 Entrust ——国外一家比较老牌的 CA。正是由于该 CA 比较老牌，因此 Windows 系统（至少包括 Win2000 之后的版本）中以及 Firefox 中，都已经内置了它的根证书。

　　老流氓大概是花了些银子，于是该CA提供的根证书就信任了 CNNIC 制作的某个 SSL 证书（不明白证书间是如何信任的，请回顾一下[俺扫盲帖](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)中提到的“证书信任链”）。

　　到了2010年下半年，Entrust 大概也意识到 CNNIC 的名声太臭，就解除了跟 CNNIC 的信任关系。所以，如今【新的】Entrust 证书，已经不再信任 CNNIC 的 SSL 证书了。如果你的浏览器是新版本或者 Windows 系统更新过新的补丁，其内置的 Entrust 证书应该是安全的，不用清理了。如果你吃不准 Windows 系统或浏览器内置的 Entrust 证书是否安全，请根据本文后续章节“★如何确认门户已经清理干净”介绍的方法判断。 　　那电脑中有了 CNNIC 的证书，会出现啥鸟事捏？俺大概说一下。 　　所谓的“中间人攻击”，洋文叫做“Man-In-The-Middle attack”，按首字母缩写成 MITM。 　　在证书导致的各种风险里面，“中间人攻击”的风险，是【最大】的（没有之一），也是最经常被提及滴。

　　俺在[前面的帖子](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)已经讲了 CA 证书对于 HTTPS 协议的重要性（可以防止攻击者伪造虚假网站）。既然老流氓 CNNIC 已经成为合法的 CA，那它就能堂而皇之地制作并发布 CA 证书。然后捏，再配合 GFW 进行【域名污染】。那 GFW 就可以轻松搞定任何网站的 HTTPS 加密传输。

  
　　（如果你不清楚“域名污染”是咋回事儿，可以看俺的扫盲教程——《[扫盲 DNS 原理，兼谈“域名劫持”和“域名欺骗/域名污染”](https://program-think.blogspot.com/2014/01/dns.html)》）  
　　可能有些小朋友心里会犯嘀咕：GFW 会有这么坏吗？俺想篡改鲁迅他老人家的一句话来回答：**俺向来是不惮以最坏的恶意，来推测党国**。GFW 和 CNNIC 作为党国的2条走狗，一起进行中间人攻击（一个负责在 DNS 上做手脚、另一个负责伪造 CA 证书），简直是“天生一对、黄金搭档”啊！ 　　另外一个大伙儿不太关注的风险，是关于 ActiveX 控件的问题。前几年，很多恶意软件（包括流氓软件、木马）都是通过 IE 控件的技术，安装到大伙儿的电脑上。后来微软加强了对 ActiveX 控件的验证：在 IE 的默认设置下，对于【没有】数字签名的 ActiveX 控件，默认是拒绝安装滴；而对于有数字签名的控件，则会给出提示。 　　因此，老流氓 CNNIC 可以很轻松地给自己的 ActiveX 控件制作数字证书。然后把控件放到网上。某些粗心的电脑用户看到IE跳出的安装控件提示，多半没细看，直接就点了“确定”按钮。 　　其实网上关于如何去掉证书的操作指南，多如牛毛，所以俺就简单说一下，懒得再抓图了。 　　有些浏览器（IE、Chrome、Safari）使用的是操作系统的证书体系。这种情况下，你需要把 CNNIC 证书从操作系统的证书体系中去掉；还有些浏览器（比如：Firefox、Opera）是自己带了一套证书体系。你要进入该浏览器的配置界面，把不要的证书去除即可。 　　下面分不同的浏览器，不同的操作系统，分别介绍： 　　对于使用 Windows 下的 IE 或 Chrome 或 Safari 浏览器，则需要执行如下步骤：

1\. 运行 Windows 的证书管理器（到命令行执行`certmgr.msc`）。

2\. 选中“受信任的根证书颁发机构”=>“证书”。 3. 查看右边的证书列表。如果里面已经有 CNNIC 的证书，直接跳到第7步。

4\. 先翻墙到“[这个页面](https://code.google.com/p/program-think/downloads/detail?name=cnnic.7z)”下载现成的 CNNIC 证书。要把证书从 7z 压缩包中解压出来（**补充说明**：“Google Code 网站”已在2016年1月关闭，此下载页面已【失效】）。

5\. 鼠标在“受信任的根证书颁发机构”=>“证书”上点右键。在右键菜单中点“所有任务”=>“导入”。 6. 出现一个导入向导，根据先导一步步的提示，把上述 CNNIC 证书导入到证书列表中。 7. 选中 CNNIC 证书，点右键。在右键菜单中点“属性”。 8. 在跳出的属性对话框中，选中“停用这个证书的所有目的”，然后确定。 9. 最后，为了保险起见，再把这三个证书，导入到“不信任的证书”中（方法和上述类似）。 　　（注：上述操作仅对当前用户生效。如果你的 Windows 系统中有多个常用的用户帐号，要对每一个用户进行上述设置） 　　对于使用 Mac OS X 下的 Safari 或 Chrome 浏览器，则需要执行如下步骤： 请到“实用工具”=>“钥匙串访问”=>“系统根证书”=>“证书”，找到 CNNIC 的证书并双击，改为“永不信任”。 　　（注：如果你的界面是洋文，其操作方式也八九不离十。俺就不再啰嗦了） 　　对于 Debian 或 Ubuntu 系统，以管理员权限进行如下操作：

　　**方法1**

  
　　运行命令：`dpkg-reconfigure ca-certificates` 会出现一个图形界面，把 CNNIC 证书【不勾选】，并确认。  
　　**方法2**  
　　编辑 `/etc/ca-certificates.conf` 文件，把 CNNIC 证书对应的行删除或注释掉。然后用命令 `update-ca-certificates` 使之生效。 　　（注：对于其它 Linux 发行版本，也有类似操作，俺就不再啰嗦了） 　　不论是在哪个操作系统下，只要你用的是 Firefox 浏览器（它的证书体系独立于操作系统的），则需要执行如下步骤： 1. 从菜单“工具”=>“选项” ，打开选项对话框 2. 切换到“高级”部分，选中“加密”标签页，点“查看证书”按钮。 3. 在证书对话框中，切换到“证书机构”。 4. 里面的证书列表是按字母排序的。把 CNNIC 打头的都删除。

　　（**注：如果某个证书是 Firefox 自带的，则删除之后，下次再打开该对话框，此证书还在。不过不要紧，它的所有“信任设置”，都已经被清空了。**）

　　不论是在哪个操作系统下，只要你用的是 Opera 浏览器（它的证书体系独立于操作系统的），则需要执行如下步骤： 1. 从菜单“工具”=>“首选项” ，打开首选项对话框 2. 切换到“高级”标签页，在左边选择“安全性”这项。 3. 点“管理证书”按钮，出来一个证书的对话框。切换到“证书颁发机构”标签页。 4. 找到 CNNIC 的证书并选中，点“查看”按钮，在证书属性对话框中，把“允许连接到使用此证书的网站”的打勾去掉 　　（注：俺是基于 Opera 10.10 进行操作。新版本的界面可能略有差异）  

　　【补充说明】

　　本文发出之后，过了5年，包括微软、Google、苹果在内的几大操作系统和浏览器厂商开始把 CNNIC 的根证书从默认的信任列表中清除。从那之后，连 CNNIC 自己的官网也不得不使用国外的证书。所以，本小节的下述内容就作废了（俺标注了删除线）。

　　为了保险起见，在完成上述的清除工作之后，你需要用浏览器访问一下老流氓的一个网站，地址是 [**https**://www.cnnic.cn](https://www.cnnic.cn) （记得用 **HTTPS** 协议哦） 　　如果你的浏览器报告该网站的证书有问题，那恭喜你，你的门户清理干净了 :-)

　　如果该网站的页面顺利打开，那你就要重新检查一下，看上述操作是否出了差错。

　　有些国内网站已经开始使用 CNNIC 的证书，目前已经知道的有163邮箱（真鄙视网易）。但是甭担心。去除证书后，浏览器在访问上述网站时，会给出一个证书的安全警告。你只需添加一个安全例外即可。 　　另外列举一些相关的资料给大伙儿参考：

《[最最最严重安全警告](http://autoproxy.org/en/node/66)》

（此文是 AutoProxy 的作者 WCM 亲自写的。09年就已经在网上广为流传）

《[CNNIC 我不信任你——从受信任的根证书里赶走 CNNIC](http://felixcat.net/2010/01/throw-out-cnnic/)》

（这篇文章也被多处转贴）

《[noCNNIC](https://code.google.com/p/nocnnic/)》

  
（已经有热心网友在 Google Code 平台上搞了一个自动清除工具。**补充说明**：“Google Code 网站”已在2016年1月关闭，此项目已【失效】）

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[数字证书及 CA 的扫盲介绍](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)》  
《[CNNIC 干过的那些破事儿](https://program-think.blogspot.com/2010/02/about-cnnic.html)》  
《[老流氓 CNNIC 的接班人——聊聊“沃通/WoSign”的那些破事儿](https://program-think.blogspot.com/2016/09/About-WoSign.html)》  
《[扫盲 DNS 原理，兼谈“域名劫持”和“域名欺骗/域名污染”](https://program-think.blogspot.com/2014/01/dns.html)》  
《[扫盲 HTTPS 和 SSL/TLS 协议](https://program-think.blogspot.com/2014/11/https-ssl-tls-0.html)》（系列）

