---
layout: default
title: '&#8220;如何翻墙&#8221;系列&#65306;戴&#8220;套&#8221;翻墻的方法'
date: None
author:
    display_name: 
---

　　1. 　　本文最早写于党国的六十大寿临近之际（2009）。当时 GFW 发飚，很多翻墙工具纷纷落马。只有 Tor 还比较坚挺，依靠网桥模式，突破封锁。所以当时俺写了此文，顺便普及了一把网桥中继的知识。 　　2. 　　后来，网桥中继的模式已经不灵光了（大部分中继都被 GFW 封杀了）。 　　3. 　　所以，俺把本文的后半部分重写了，介绍了一种新的方法——利用互联网上的公共代理，让 Tor 复活。 　　4. 　　再后来，用公共代理的方式，也不灵了（很难找到合适的公共代理，估计也是因为 GFW 的屏蔽） 　　5.

　　2014年10月，Tor 官方推出了基于 meek 的插件，Tor 又复活啦（具体配置参见《[Tor 已复活——meek 流量混淆插件的安装、优化、原理](https://program-think.blogspot.com/2014/10/gfw-tor-meek.html)》）

　　另外，俺在2013年补充了一篇《[关于 Tor 的常见问题解答](https://program-think.blogspot.ro/2013/11/tor-faq.html)》，有兴趣的同学也可以参考。

  
　　先说明一下：本文提及的 Tor，是指“Tor Browser”，其中包含了“Tor、vidalia、polipo、Firefox”等软件，非常适合傻瓜用户。 　　另外，考虑到本文的大多数读者是一些非 IT 专业的电脑用户，俺尽量用通俗的大白话且讲得比较啰嗦，请那些懂行的同学不要嫌烦。不懂行的同学，一定要耐心看完全文哦！  
　　通过**加密**的 Web 网页代理，访问 Tor 的官方站点（在“[这里](https://www.torproject.org/)”），下载最新的软件包。记住，一定要用**加密的**（也就是 **HTTPS** 协议）网页代理。 　　这个方法的缺点是：在非常时期，可能很难找到好用的加密 Web 网页代理。 　　这个方式在封锁加剧的时期，比较合适。除非我党把所有国外的 Email 提供商都和谐掉，否则咱们总是有机可趁。具体操作如下：

　　发送标题为 `help` 的【纯文本】邮件到 `[gettor@torproject.org](mailto:gettor@torproject.org)`，收到回复后根据邮件的提示再回复一次，即可在你的邮箱中收取 Tor 的软件包。

　　提醒几个注意事项： 1. 要使用【国外】的邮箱； 2. 如果使用 Web 界面操作邮箱，记得要用加密的【HTTPS】方式访问；

3\. 切记要用【**纯文本**】的邮件格式。

  
　　先介绍一下 Tor 的基本用法。那些已经安装了 Tor 还是上不了网的同学，直接看后面的一节：如何使用网桥中继 　　事先声明：考虑到大多数网民都在用 Windows，下面以 Windows 系统的 Tor 来作介绍。使用苹果系统或利牛克斯系统的用户，不要怪俺歧视哦 :) 　　首先，把 Tor 软件包解压缩到某个目录下。 　　如果你连“解压缩”也不会，那你不需要再看这个帖子了，先去普及完电脑使用常识再回来学翻墙。 　　在上述目录下有一个名叫“Start Tor Browser.exe”的程序，双击启动之。然后，会跳出一个“Vidalia Control Panel”的窗口。

![不见图 请翻墙](https://lh3.googleusercontent.com/ViCha45zPwh79e4Bom2epEQBR7Y-11jAQ5Kzu_7x4CwLhWG8Iu0PMwMrR1RMaZ5Z7L5DGHzphvy12Ol7h48dfZdpm1OfixB-cksDFoStacSv8cd_tFrNdXHdTn-Z700pqjODLLZe)

　　假如你不喜欢/不习惯洋文的界面，可以点控制面板中的“Settings”按钮，进入到“Apperance”标签页，选择你喜欢的语言（比如中文）。

![不见图 请翻墙](https://lh4.googleusercontent.com/4tKTw4FSUJOyZhUWMoWGtELaVb69qSFayai64zmueVCbl5KD7_mubMkGfDNjUjf7wbjOygnkiDu6q2DJDYwFdi3pLGyJngisxwjWS3AJp5bD1y6HC_KbGovDyq7pnTAjR8w8DNrm)

　　设置好之后，控制面板立马变为中文的，效果如下图所示：

![不见图 请翻墙](https://lh6.googleusercontent.com/I3p7KryEc9q9kC5KfPZAj3cgrN46GuJHZLYQ0FC9whzele9Wq3dr3gtb4NphB0knfyZNJoZMBBv5D0oapiVS9xAZN-lrV_cCzG0QRBjzCWwaQWfPfNkibsmLs_YNeomfTsVNhTYO)

  
　　如果能够正常连接到互联网，则该程序会自动运行内置的一个 Firefox 浏览器。如果这个内置浏览器直接能访问被墙的网站，那恭喜你，翻墙成功啦！ 　　但是别高兴得太早。从2010年之后，在天朝之内运行 Tor 是很难直接联网的。因为 Tor 的目录服务器和大部分的网桥中继都被 GFW 封掉了。在本文的后续章节，会告诉你如何应对。  
　　有很多网友不喜欢它内置的 Firefox，想用自己的浏览器翻墙，也没有关系。直接在你自个的浏览器中设置 **HTTP 代理**。代理的地址设置为：`127.0.0.1`；代理的端口设置为：`8118` 即可。  
　　大约从2013年开始，**Tor 官网提供的 Vidalia 套件默认【不】提供 HTTP 代理了，但仍提供 SOCKS 代理**。你可以在自个儿的浏览器中设置 **SOCKS代理**，代理的地址设置为：`127.0.0.1`；代理的端口设置为：`9050` 或 `9150`  
（补充说明：对于 2.3.25 之后的 Tor Browser Bundle，SOCKS 端口号修改为 `9150`，其它的 Bundle 依然使用 `9050`） 　　Firefox 的代理设置如下图（至于 Chrome、IE、或其它浏览器，列位看官请依样画葫芦）：

![不见图 请翻墙](https://lh6.googleusercontent.com/chrmCSXntveQ-Ht6JWGJVUfxBx2N-Qs_TVxXo5bkYTju8kH8ZTaulunqAc7Ao_Tz9EdbGeH4igsgmbobNl0h2IQ_JYNf9Gll-jeNdZ76iagxp9rTtSaeW46R71WcMAHk70gONPTz)

  
　　如果你嫌那个内置的 Firefox 碍手碍脚，想把它去掉，可以修改 Tor 软件包的配置文件。该文件在 Tor 所在目录下的 `Data\Vidalia\vidalia.conf` 把里面如下的配置项

> BrowserDirectory=FirefoxPortable  
> BrowserExecutable=tbb-firefox.exe

修改为  

> BrowserDirectory=  
> BrowserExecutable=

　　Tor 除了可以帮助你访问 Web 页面，还可以干更多事情。

　　因为 Tor 既可以当 HTTP 代理，也可以当 **SOCKS代理**，具体的配置是本机（IP 地址 `127.0.0.1`）的 `9050` 或 `9150` 端口（补充说明：对于 2.3.25 之后的 Tor Browser Bundle，SOCKS 端口号修改为 `9150`，其它的 Bundle 依然使用 `9050`）。凡是支持 SOCKS 代理的网络应用程序（比如：QQ、MSN Messener ...），都可以通过 Tor 的 SOCKS 代理来联网。

  
　　顺便提醒一个小细节：Tor 的 `9051` 端口，是控制端口，别跟 SOCKS 端口搞混了。  
　　**从2010年开始，GFW 逐步地封杀 Tor 的网桥中继（bridge）。如今，大部分“网桥中继”都已经被 GFW 屏蔽掉了。用“网桥中继”来复活 Tor，已经很难成功了。所以，请跳过本章节的内容，直接看下一节。**  
　　所谓的“双重代理”就是——用其它翻墙工具（可以是翻墙代理，也可以是翻墙 VPN）组合 Tor。如此一来，Tor 就可以用其它翻墙工具的通道进行联网，实现复活。具体的配置方式请看《[如何隐藏你的踪迹，避免跨省追捕\[5\]：用多重代理隐匿公网 IP](https://program-think.blogspot.com/2012/03/howto-cover-your-tracks-5.html)》。  
　　可能有的同学会问，既然已经有其它翻墙工具可用，为啥还要用 Tor 来搞双重代理捏？这么干的原因在于：双重代理可以提高很好的隐匿性。具体的好处请参见《[关于 Tor 的常见问题解答](https://program-think.blogspot.ro/2013/11/tor-faq.html)》，这里就不再罗嗦。  
　　“公共代理”全称是“公共的代理服务器”。这是互联网上的一些好心人架设的代理服务器。所谓“公共”，就是说任何人都能使用这些代理，无需额外费用。 　　常见的公共代理有如下类型：SOCKS 和 HTTP。其中，SOCKS 代理又细分为两种：SOCKS4 和 SOCKS5（SOCKS5 比 SOCKS4 高级）。 　　从协议的层次而言，SOCKS 代理位于网络的第5层（OSI 模型的会话层），而 HTTP 代理位于网络的第7层（OSI 模型的应用层）。从协议的角度来说，SOCKS 代理的性能会高于 HTTP 代理。 　　其实俺手头有几个能用的 SOCKS 公共代理。但是捏，因为朝廷的爪牙们也在关注俺博客。如果把这几个 SOCKS 代理公布出来，不出几天就会被封掉。而且俺信奉“授人以鱼不如授人以渔”。所以捏，就多费点口水，介绍一下公共代理的获取方式。 　　要找到公共代理，简而言之，就是用 Google 搜！ 　　互联网上有成千上万的免费代理可以使用。而且有很多专门的代理网站。这些网站会帮你收集汇总速度快的，运行稳定的代理服务器。有些网站还能做到每日更新。

　　所以，你只需要通过 Google 搜索 `SOCKS proxy` 或搜索 `HTTP proxy`，就能找到很多的代理网站。

　　找到代理网站之后，上面往往列出几十个代理，该用哪个捏？

　　**首先，不要选天朝之内的代理**

因为咱们找代理是为了翻墙。你找一个墙内的代理，那属于白忙活。

　　**其次，选一个速度快的**

很多代理网站做得很人性化，它们会列出每一个代理服务器的延时。延时越小，说明速度越快。

　　**最后，测试连通性**

公共代理也是 GFW 封杀的目标。你在代理网站上找到的公共代理，其中有些没准已经被封了。 那么，如何判断某个代理是否还能用？很简单，用操作系统自带的 ping 命令测试一下。假如你找到的代理，IP 是 xx.xx.xx.xx 那么你可以用如下命令测试。

ping xx.xx.xx.xx

　　如果显示超时 Request time out 说明这个代理很可能被 GFW 封了——那你就只好再选另一个代理了；如果显示 reply from xx.xx.xx.xx 那就说明这个代理可用。  
　　（注：用 `ping` 命令测试公共代理，不太精准。因为 ping 使用的是 ICMP 协议，而“HTTP 代理”或“SOCKS 代理”使用的是 TCP 协议。有时候，ping 某个 IP 正常，但这个 IP 的代理端口还是无法联上）  
　　为了解决上述“不够精准”的弊端，还可以用操作系统自带的 `telnet` 命令，直接测试代理的端口是否能连得上。`telnet` 命令比 `ping` 命令更准确，可惜的是，Win7 默认不带此命令 :(  
　　另外，也可以使用赫赫有名的“网猫”（netcat）来帮你测试。具体参见教程《[扫盲 netcat（网猫）的 N 种用法——从“网络诊断”到“系统入侵”](https://program-think.blogspot.com/2019/09/Netcat-Tricks.html)》 　　因为有好几个网友询问此类问题，俺补充了这个小节。 　　互联网上的公共代理服务器有好多种，支持的协议也不同。对 Tor 的客户端而言，“公共代理服务器”需要支持“HTTP 代理”或“SOCKS 代理”，Tor 客户端才能通过它联网。 　　容易出问题的是“HTTP 代理”。因为有些“公共代理”虽然支持“HTTP 代理”，但它只能转发【明文】的 HTTP 协议，而无法转发【加密】的 HTTPS 协议。而 Tor 客户端的流量恰恰是【加密】的 HTTPS 协议。对这种“公共代理”，Tor 就没法用。 　　到“Vidalia 控制面板”中，点击“设定”按钮；进入“网络”标签页；在里面勾选“我使用代理服务器连接到网络”。如下图所示：

![不见图 请翻墙](https://lh4.googleusercontent.com/_8-IJG3K9KUOLXo0sVZHEiB3Adsfn-O56fbGJ1SmSiBYsJD_hWscu0Cajb0vUEeaJ-ayAyHy340LTeRQbrH8R2j22eA4y4P0gtvK1YKXdg5-3uQLEO2qK-9YnxBt-WCFisUmKbFY)

  
　　勾选之后，会出现如下界面；把你找来的公共代理的“地址”、“端口”、“类型”设置好。提醒一下，**代理的类型别选错了**！  

![不见图 请翻墙](https://lh6.googleusercontent.com/up_Bce_3-KA_5fBGIsnaIfNKh_66qWkwguqnBXF8UuSD1Ct0-QyQXmifaEYxCxb3UdQ8SiUIeyuKcMKy6cIkv1Q5iVrZvvi12-l0ouxXERpxnl8ERpxcKCmXd1BNkH39f9sP-NRd)

　　完成上述步骤之后，重启一下 Tor 并稍等片刻，洋葱头应该就变绿了。  
　　这是2014年才出现的新招数，**由 Tor 官方提供**。  
　　该招数的具体教程，请参见《[Tor 已复活——meek 流量混淆插件的安装、优化、原理](https://program-think.blogspot.com/2014/10/gfw-tor-meek.html)》。 　　如果碰到翻墙的问题，或者想给俺提意见/建议，欢迎到俺博客留言。 　　最后，希望大家都能够传播翻墙姿势，帮助周围的人重新呼吸到互联网上自由的空气！！！

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[关于 Tor 的常见问题解答](https://program-think.blogspot.ro/2013/11/tor-faq.html)》  
《[Tor 已复活——meek 流量混淆插件的安装、优化、原理](https://program-think.blogspot.com/2014/10/gfw-tor-meek.html)》  
《[如何用 Tor 访问对 Tor 不友好的网站——扫盲“三重代理”及其它招数](https://program-think.blogspot.com/2020/08/Tor-Triple-Proxy.html)》  
《[如何翻墙](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)》（传说中的扫盲教程，定期更新）  
《[获取翻墙软件方法大全](https://program-think.blogspot.com/2011/03/how-to-get-gfw-tools.html)》（教你在无法翻墙的情况下拿到翻墙软件）  
《[扫盲 VPN Gate——分布式的 VPN 服务器](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)》  
《[双管齐下的赛风3](https://program-think.blogspot.com/2011/10/gfw-psiphon.html)》  
《[新版本无界——赛风3失效后的另一个选择](https://program-think.blogspot.com/2011/12/gfw-wujie.html)》  
《[自由門——Tor 被封之后的另一个选择](https://program-think.blogspot.com/2010/03/choose-free-gate.html)》  
《[扫盲 VPN 翻墙——以 Hotspot Shield 为例](https://program-think.blogspot.com/2011/09/gfw-vpn-hotspot-shield.html)》  
《[简单扫盲 I2P 的使用](https://program-think.blogspot.com/2012/06/gfw-i2p.html)》

