---
layout: default
title: '2012年9月翻墙快报&#65288;兼谈复活 TOR 的方法&#65289;'
date: None
author:
    display_name: 
---

**翻墙的普及需要大家一起努力，希望有更多网友早日呼吸到互联网上自由的空气！** 　　据说朝廷的18大马上要召开了。按照惯例，GFW 又加强了封锁的力度。根据网友们的反馈，最新版的 无界 和 自由门 都不灵了。赛风的最新版本比较奇怪——有些网友能用，有些不能（貌似跟地域或宽带提供商有关）。另外，世界通的 Skype 通道依然可用。

　　所有新版本的翻墙软件，都汇总到“[微软网盘](https://onedrive.live.com/?id=F5B0090663FEEADA!730)”（墙外）。考虑到某些网友尚无法翻墙，俺特地准备了**墙内可用**的下载链接。注意：下载后是个 BMP 图片，其实是个压缩包。把文件扩展名从 bmp 改为 7z，即可用 7zip 或者 WinRAR 打开，把翻墙工具解压出来。。有些翻墙软件支持邮件方式获取，俺也一并列入下述表格。

软件名称

版本号

墙内下载链接

邮件获取

世界通

4.1.0

[这里](http://img610.ph.126.net/jimNYb8Ngf6SHxl1RIHlsA==/1949777163676558355.bmp)

（暂无）

赛风

3.42

[这里](http://blob-s-docs.googlegroups.com/docs/OgAAAC2lwM6EJ9y1bqDORxV3N8VWb0JtWsDszPFUtzHiHnLD6vLl6VhRmdBSPuWJ4OBU_tw1UhR-qKrqSvfq0Y04y3kA15jOjCDaWrziHp-7Gll2v1NsBmnK5Fs8)

get@psiphon3.com

TOR

0.2.2.38

（暂无）

gettor@torproject.org

　　由于这次封锁的力度比较大。赛风、无界、自由门 这三款常用翻墙工具受到不同程度的影响。世界通的 Skype 通道虽然能用，但速度似乎不够快。所以，俺再给大伙儿支个招。 　　TOR 作为老牌的翻墙代理，最近两年来被 GFW 彻底封杀。几乎所有 TOR 的目录服务器和网桥中继，都被 GFW 列入 IP黑名单。但是依然有办法让 TOR 复活。 　　可以通过邮件的方式，直接拿到 TOR 的软件包。具体操作如下：

发送主题为“help”的纯文本邮件到**[gettor@torproject.org](mailto:gettor@torproject.org)**，收到回复后根据邮件的提示再回复一次，即可在你的邮箱中收取 TOR 的软件包。记得要用 HTTPS 方式上 **Gmail**，以确保最佳效果。切记要用**纯文本**的邮件格式。

　　公共代理，全称是“公共的代理服务器”。这是互联网上的一些好心人架设的代理服务器。所谓“公共”，就是说任何人都能使用这些代理，无需额外费用。 　　常见的公共代理有如下类型：SOCKS 和 HTTP。其中，SOCKS 代理又细分为两种：SOCKS4 和 SOCKS5（SOCKS5 比 SOCKS4 高级）。 　　从协议的层次而言，SOCKS 代理位于网络的第5层（OSI 模型的会话层），而 HTTP 代理位于网络的第7层（OSI 模型的应用层）。从协议的角度来说，SOCKS 代理的性能会高于 HTTP 代理。 　　其实俺手头有几个能用的 SOCKS 公共代理。但是捏，因为朝廷的爪牙们也在关注俺博客。如果把这几个 SOCKS 代理公布出来，不出几天就会被封掉。而且俺信奉“授人以鱼不如授人以渔”。所以捏，就多费点口水，介绍一下公共代理的获取方式。 　　要找到公共代理，简而言之，就是用 Google 搜！ 　　互联网上有成千上万的免费代理可以使用。而且有很多专门的代理网站。这些网站会帮你收集汇总速度快的，运行稳定的代理服务器。有些网站还能做到每日更新。

　　所以，你只需要通过 Google 搜索 **SOCKS proxy** 或搜索 **HTTP proxy**，就能找到很多的代理网站。

　　找到代理网站之后，上面往往列出几十个代理，该用哪个捏？

**首先，不要选天朝之内的代理**

因为咱们找代理是为了翻墙。你找一个墙内的代理，那属于白忙活。 做得好的代理网站，会列出每一个代理所在的国家。假如没有列出国家信息，你可以找一个查 IP 归属地的网站或软件，很容易就能判断某个代理位于哪国。

**其次，选一个速度快的**

很多代理网站做得很人性化，它们会列出每一个代理服务器的延时。延时越小，说明速度越快。

**最后，测试连通性**

公共代理也是 GFW 封杀的目标。你在代理网站上找到的公共代理，其中有些没准已经被封了。

那么，如何判断某个代理是否还能用？很简单，用操作系统自带的 ping 命令测试一下。【假设】你找到的代理，其 IP 是 `1.2.3.4` 那么你可以用如下命令测试：

  

ping 1.2.3.4

  
如果显示超时 `Request time out` 说明这个代理很可能被 GFW 封了——那你就只好再选另一个代理了；如果显示 `reply from 1.2.3.4` 那就说明这个代理可用。 对于熟悉IT技术的网友，也可以用操作系统自带的 telnet 命令，直接测试代理的端口是否能连得上。telnet 命令比 ping 命令更准确，可惜的是，Win7 默认不带此命令 :( 　　找到好用的公共代理之后，如何配置 TOR 让它通过公共代理联网？具体教程可以参见之前的博文：

《[戴“套”翻墻的方法](https://program-think.blogspot.com/2009/09/break-through-gfw-with-tor.html)》

  
　　下面这些教程都在俺博客上（墙外）。不会翻墙的网友，可以先用【墙外的】RSS 阅读器订阅俺博客（订阅地址：[http://feeds2.feedburner.com/programthink](http://feeds2.feedburner.com/programthink)），就可以看到所有教程。  
[如何翻墙](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)（传说中的扫盲教程，定期更新）  
[常见翻墙问题答疑](https://program-think.blogspot.com/2011/09/gfw-faq.html)（传说中的 FAQ，定期更新）  
[获取翻墙软件方法大全](https://program-think.blogspot.com/2011/03/how-to-get-gfw-tools.html)（教你在无法翻墙的情况下拿到翻墙软件）  
[多台电脑如何共享翻墙通道](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)  
[扫盲 VPN Gate——分布式的 VPN 服务器](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)  
[关于 TOR 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)  
[双管齐下的赛风3](https://program-think.blogspot.com/2011/10/gfw-psiphon.html)  
[自由門——TOR 被封之后的另一个选择](https://program-think.blogspot.com/2010/03/choose-free-gate.html)  
[新版本无界——赛风3失效后的另一个选择](https://program-think.blogspot.com/2011/12/gfw-wujie.html)  
[扫盲 VPN 翻墙——以 Hotspot Shield 为例](https://program-think.blogspot.com/2011/09/gfw-vpn-hotspot-shield.html)  
[戴“套”翻墻的方法](https://program-think.blogspot.com/2009/09/break-through-gfw-with-tor.html)  
[简单扫盲 I2P 的使用](https://program-think.blogspot.com/2012/06/gfw-i2p.html)  
[基于 Skype 翻墙](https://program-think.blogspot.com/2011/05/through-gfw-with-skype.html)  
　　如果碰到翻墙的问题，或者想给俺提意见/建议，欢迎来信（ `program.think@gmail.com` ）。**给俺写信最好用 Gmail 或 Hotmail，国内的邮箱很可能会被墙，导致俺收不到。**

