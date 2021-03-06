---
layout: default
title: '2015年8月翻墙快报'
date: None
author:
    display_name: 
---

  
　　春节之后的半年，翻墙形势还可以，所以俺就一直没有发《翻墙快报》。不过最近几周，GFW 好像采用了新的手段来干扰翻墙工具的线路。有不止一个读者反馈说，某某翻墙工具的可用性下降了。所以今天俺再发一篇《翻墙快报》，汇总一下近期可用的翻墙工具，并附上简要说明。 　　经读者反馈以及俺本人测试，【至少】有如下几款工具还是可用滴。 　　这是俺个人比较推荐的翻墙工具。免费、而且能提供比较高的翻墙速度。（当然啦，为了找到速度快的 Server，需要一点耐心和运气） 　　近期 GFW 似乎加大了对 VPN Gate 的干扰，可用的 Server 好像比原来少了。 　　关于 VPNGate 的使用经验，之前已经聊过好几次，今天再重复罗嗦一下：

　　**如何判断 Server 是否在线？是否被屏蔽？**

　　VPN Gate 界面上提供的“中继服务器列表”，其中的 server 并非每个都可以联通。无法联通主要有两种情况：其一是“Server 已经下线”；其二是“Server 虽然在线，但是被 GFW 屏蔽了”。 　　如果你连接某个 Server 出现如下现象之一，通常说明该 Server 在线，但是被屏蔽。 1. 建立连接的过程中弹出“验证服务器证书”的提示框，并且一直停留在这一步（超过半分钟）。 2. 建立连接的过程中弹出“用户身份验证”的提示框，并且一直停留在这一步（超过半分钟）。 3. 连接已经完成，但是过了几分钟之后，连接自行断掉。

　　**如何重新连接上被屏蔽的 Server？**

  
　　要重新连上已经被屏蔽的 Server，主要的办法是——**切换你的“公网 IP”**。这个办法不一定 100% 灵验，但是很多时候是可行的（俺经常这么干）。 　　对于“家用宽带”，通常只需要把你的宽带接入设备（比如光猫）重新启动一下，你的“公网 IP”就变了； 　　如果你使用公司的宽带，要想切换“公网 IP”就非常麻烦，甚至是不可行的。因为某些公司租用的是专线，ISP 会提供一个【固定的】公网 IP。 　　前几个月，TOR Browser 的大版本已经从 4.0 升级到 4.5（目前最新的是 4.5.3）升级之后，依然始内置 meek 插件。该插件可以利用知名 IT 公司（亚马逊、微软）的云计算平台来规避 GFW 的封杀。

　　（meek 的扫盲教程在“[这里](https://program-think.blogspot.com/2014/10/gfw-tor-meek.html)”）

　　近期，GFW 好像也加大了对 meek 方式的干扰——有时候 meek 插件始终无法联通。不过你可以采用俺刚才提到的“变换公网 IP”的方式，或许又可以重新联通。 　　目前最新的版本是 3.95，可用，速度一般。另外，近期的稳定性好像下降了（多半也是因为 GFW 的干扰）。 　　赛风除了提供 Windows 版本，还有 Android 版本。

　　（相关的教程是《[双管齐下的赛风3](https://program-think.blogspot.com/2011/10/gfw-psiphon.html)》）

　　这款主要是面向 Android 手机系统的翻墙工具。 　　今年年初，fqrouter 曾经短暂死亡（其作者宣布停止开发）；后来又复活——作者宣布继续发布新版本。目前最新版本是 2.12.7

　　没用过这款工具的同学，请看《[“如何翻墙”系列：fqrouter——安卓系统翻墙利器（免 ROOT）](https://program-think.blogspot.com/2014/07/gfw-fqrouter.html)》

　　据网友们反馈，一直可用。当然，前提是你自己拥有墙外的 VPS（虚拟专用服务器）。然后把 SS 部署在墙外的 VPS 上，使之成为你的翻墙代理。 　　SS 的稳定性极好，速度也足够快。主要缺点是——需要你花点银子购买 VPS。 　　自由门最新的版本是 7.5.4，可用，感觉速度不够快。 　　无界最新的版本是 15.01，虽然可用，但是非常不稳定（但也有读者用的是联通宽带，说无界很稳定）。 　　由于“无界和自由门”本身【不是】开源的。还不如用 VPN Gate 或 TOR+meek。 　　（凡是利用 Google 的 GAE 服务器进行翻墙方式，都称之为“GAE 翻墙”） 　　俺本人因为安全考虑，从来不用“GAE 翻墙”。所以俺也没法亲自验证。据读者反馈，目前 GAE 翻墙还是可用的，而且速度够快。 　　由于这类翻墙方式本身存在若干安全方面的隐患，【千万不要】使用这种翻墙方式来发布敏感的政治言论。如果只是用它来翻墙看看视频，问题倒不大。 　　本文发出后，有读者质疑俺对 GAE 安全性的判断。所以俺再稍微说明一下。 　　对于 GAE 的安全问题，俺举一个例子（其实前几年的博文已经聊过这个例子）： 　　用“GAE 翻墙”的方式访问网站，HTTP 请求的“User Agent”会包含你使用的 GAE 的 APP ID。通过这个，非常容易定位到访客的身份。而且这个 User Agent 是 GAE 服务器加入到 HTTP 头，好像没法除去。 　　I2P 最新的版本是 0.9.20，可用（当然，速度一如既往的慢）。

　　由于 I2P 的速度实在不敢恭维，建议只留作备份（当其它工具都失效之后，用 I2P 救急）。提醒一下：你拿到 I2P 之后，先要让它补种（reseed）并运行一段时间。至于如何补种，俺的教程有介绍（参见“[这里](https://program-think.blogspot.com/2012/06/gfw-i2p.html)”）。

　　因为本人的时间/精力有限，如有遗漏，大伙儿可以到博客评论中补充。  
　　俺在1月份已经开通了【基于 BT Sync 的分布式网盘】。**BT Sync 的一大优点是【免翻墙】**，所以俺已经用它来分享翻墙工具。 　　如果你暂时还无法翻墙，可以考虑先安装 BT Sync，然后使用如下密钥，【自动】同步俺分享的【多款翻墙软件】。

各种翻墙软件的同步密钥 BTLZ4A4UD3PEWKPLLWEOKH3W7OQJKFPLG

  
　　BT Sync 客户端的官方下载页面：[1.4 版本](http://syncapp.bittorrent.com/1.4.111/)、[最新版本](https://getsync.com/)（这两个链接是【页面】链接，【不要】直接“另存为”）

　　从来没用过 BT Sync 的同学，请先看《[扫盲 BT Sync——不仅是同步利器，而且是【分布式】网盘](https://program-think.blogspot.com/2015/01/BitTorrent-Sync.html)》。

  
　　（**虽然俺博客已经被 GFW 彻底封杀，但是你可以通过博客阅读器，看到这篇教程**） 　　下面这些教程都在俺博客上（需翻墙）。

　　从2014年4月开始，俺博客会定期提供打包下载（电子书形式），请看“[这篇博文](https://program-think.blogspot.com/2014/04/blog-ebook.html)”。**一旦你能够翻墙，强烈建议先把俺博客的打包电子书下载到自己硬盘上。一旦今后无法翻墙，至少手头还有一些翻墙教程可以参考。**

  
[如何翻墙](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)（传说中的全方位扫盲教程，定期更新）  
[获取翻墙软件方法大全](https://program-think.blogspot.com/2011/03/how-to-get-gfw-tools.html)（教你在无法翻墙的情况下拿到翻墙软件）  
[多台电脑如何共享翻墙通道](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)  
[“如何翻墙”系列：TOR 已复活——meek 流量混淆插件的安装、优化、原理](https://program-think.blogspot.com/2014/10/gfw-tor-meek.html)  
[关于 TOR 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)  
[扫盲 VPN Gate——分布式的 VPN 服务器](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)  
[双管齐下的赛风3](https://program-think.blogspot.com/2011/10/gfw-psiphon.html)  
[fqrouter——安卓系统翻墙利器（免 ROOT）](https://program-think.blogspot.com/2014/07/gfw-fqrouter.html)  
[戴“套”翻墻的方法](https://program-think.blogspot.com/2009/09/break-through-gfw-with-tor.html)  
[简单扫盲 I2P 的使用](https://program-think.blogspot.com/2012/06/gfw-i2p.html)  
[新版本无界——赛风3失效后的另一个选择](https://program-think.blogspot.com/2011/12/gfw-wujie.html)  
[自由門——TOR 被封之后的另一个选择](https://program-think.blogspot.com/2010/03/choose-free-gate.html)  
[扫盲 VPN 翻墙——以 Hotspot Shield 为例](https://program-think.blogspot.com/2011/09/gfw-vpn-hotspot-shield.html)

