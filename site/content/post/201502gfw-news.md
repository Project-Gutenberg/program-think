---
layout: default
title: '2015年2月翻墙快报&#65288;VPN Gate 和 fqrouter 双双复活&#65289;'
date: None
author:
    display_name: 
---

　　2月份的翻墙形势依然严峻，不过比1月份好多了。主要的变化是——VPN Gate 复活了。

　　其实春节前就有读者在博客评论中反馈了这个好消息。当时没有马上发博文通告大伙儿——因为俺想多考察一段时间，看看这次复活的情况如何。经过这两星期，感觉还可以。所以今天发一篇《翻墙快报》跟大伙儿说一下。

  
　　从来没用过 VPN Gate 的同学，先看之前那篇扫盲《[“如何翻墙”系列：扫盲 VPN Gate——分布式的 VPN 服务器](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)》。已经熟悉 VPN Gate 的同学，直接翻墙去它官网（[http://www.vpngate.net/cn/](http://www.vpngate.net/cn/)）下载安装包。如果你手头的翻墙通道比较慢，可以通过它官网提供的镜像网站下载（镜像网站【免翻墙】）。 　　目前还无法翻墙的同学，请看仔细看本文后面的一个章节——★不会翻墙的同学，如何获取翻墙工具？

　　友情提醒：**如果你曾经安装过旧版本的 VPN Gate，需要先把旧版本彻底卸载（包括旧版本 VPN Gate 的网络驱动）**

　　经读者反馈以及俺本人测试，【至少】有如下几款工具还是可用滴。

　　**VPN Gate**

　　（本文前面已经说过，此处不再罗嗦）

　　**TOR+meek**

　　从 TOR Browser 4.0 之后，开始内置 meek 插件。该插件可以利用知名 IT 公司（亚马逊、微软）的云计算平台来规避 GFW 的封杀。

　　（扫盲教程在“[这里](https://program-think.blogspot.com/2014/10/gfw-tor-meek.html)”）

　　**赛风3**

　　1月份发布的 3.81 版本（以及之后的版本）是可用的。但是 3.81 版本有点缺陷——较大的上行流量会导致赛风断线（因为俺要进行 P2P 分享，感觉特别明显）。后来的 3.83 版本解决了这个问题。 　　前段时间，有读者在博客评论中担心“赛风跟朝廷串通”。此人的理由是：1月份很多翻墙工具都沦陷，赛风却依然坚挺。 　　俺个人认为这种可能性很小。而且这个推理过程本身就不严密。因为 TOR+meek 的方式，至今也没沦陷，难道说 TOR 也是串通的？另外，根据俺刚才提到的现象，赛风同样受到 GFW 的干扰，升级版本之后才规避了干扰。

　　**fqrouter**

　　本文刚发出，就有读者提醒说，fqrouter 也复活了。 　　不过捏，它的复活跟 VPN Gate 不太一样。之前 fqrouter 死掉是因为作者停止开发。昨天的消息说，作者再度发布新版本啦 :)

　　没用过这款工具的同学，请看《[“如何翻墙”系列：fqrouter——安卓系统翻墙利器（免 ROOT）](https://program-think.blogspot.com/2014/07/gfw-fqrouter.html)》

　　**ShadowSocks（简称 SS）**

　　据网友们反馈，一直可用。当然，前提是你自己拥有墙外的 VPS（虚拟专用服务器）。然后把 SS 部署在墙外的 VPS 上，使之成为你的翻墙代理。 　　SS 的稳定性极好，速度也足够快。主要缺点是——需要你花点银子购买 VPS。

　　**无界**

　　目前最新的是 14.05 版本。虽然可用，但是非常不稳定。 　　再加上“无界”本身【不是】开源的。所以用无界，还不如用 TOR+meek 或者用复活之后的 VPN Gate。

　　**I2P**

　　1月份的时候，俺测试了 I2P 0.9.17 版本，是可用的。近期没有用 I2P，估计这个版本应该还能用。

　　I2P 的速度比较慢，建议只留作备份（当其它工具都失效之后，用 I2P 救急）。提醒一下：你拿到 I2P 之后，先要让它补种（reseed）并运行一段时间。至于如何补种，俺的教程有介绍（参见“[这里](https://program-think.blogspot.com/2012/06/gfw-i2p.html)”）。

　　因为本人的时间/精力有限，如有遗漏，大伙儿可以到博客评论中补充。  
　　俺在1月份已经开通了【基于 BT Sync 的分布式网盘】。**BT Sync 的一大优点是【免翻墙】**，所以俺已经用它来分享翻墙工具。 　　如果你暂时还无法翻墙，可以考虑先安装 BT Sync，然后使用如下密钥，【自动】同步俺分享的【多款翻墙软件】。

各种翻墙软件的同步密钥 BTLZ4A4UD3PEWKPLLWEOKH3W7OQJKFPLG

  
　　从来没用过 BT Sync 的同学，请先看《[扫盲 BT Sync——不仅是同步利器，而且是【分布式】网盘](https://program-think.blogspot.com/2015/01/BitTorrent-Sync.html)》。 　　（虽然俺博客已经被 GFW 彻底封杀，但是你可以通过博客阅读器，看到这篇教程） 　　今天看到新闻——小有名气的技术社区 V2EX 也被 GFW 封了。 　　以下引述 V2EX 创始人刘昕（@Livid ）的一段话（粗体是俺加的）

> 在听到这件事情的时候，我并没有觉得特别惊讶，因为类似的事情，在 2007 年 9 月时，其实已经经历了一次。 两次我都觉得挺莫名其妙的。 V2EX 二次上线之后，我确实在内容方面一直在尝试做一些平衡，比如 VPN 方面的内容很早就不会上首页，shadowsocks 相关的内容也在最近进了隐藏节点。我内心当然还是希望能够平静过一天算是一天，这些翻墙方面的内容，在我们整个流量中的比率其实不到 1%，我当然不想因为这些 1% 的内容而遇到今天这样的事情。
> 
> **这是一种自我审查吗？是，当然是。为此我也被不少人骂过。这些事情我自己也一直觉得挺恶心的。  
> 但是，该来的这一天还是来了。**

　　从这个事儿可以看出——在天朝，即使你愿意自我审查（直白地说，就是“自我阉割”），也【不能】保证你就没事儿。

　　俺经常引用一句话：“**你可以不关心政治，但是政治一定会来关心你**”。俺希望大伙儿明白——不推翻这个奇葩的政治体制，【每个墙内的人】都会受到伤害——差别只在于方式的不同和时间的早晚。

　　下面这些教程都在俺博客上（需翻墙）。

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

