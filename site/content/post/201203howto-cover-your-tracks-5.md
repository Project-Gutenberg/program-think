---
layout: default
title: '如何隐藏你的踪迹&#65292;避免跨省追捕[5]&#65306;用多重代理隐匿公网 IP'
date: None
author:
    display_name: 
---

　　最近，天朝的两会即将通过新版本的刑事诉讼法（在新条款中，党国的爪牙可以【**合法地**】进行秘密拘捕——太阴险啦，良心大大滴坏！）所以，俺要继续完善[“如何隐藏踪迹”系列](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)，帮助大伙儿躲避朝廷的网络追捕。  
　　关于多重代理，在前几个月的翻墙贴《[扫盲 VPN 翻墙——以 Hotspot Shield 为例](https://program-think.blogspot.com/2011/09/gfw-vpn-hotspot-shield.html)》中，稍微提到过。今天来完整地介绍一下。  
　　先声明一下：本文所说的“代理”是广义滴——既包括“传统意义上的代理”，也包括“VPN”。 　　平时咱们用代理来翻墙，大部分属于【单重】代理（如下图）。也就是说，不论你用的是 VPN 还是 HTTP Proxy 还是 SOCKS Proxy，当中都只有【一个】服务器进行中转。

![不见图 请翻墙](https://lh3.googleusercontent.com/Rgn4KkxdyjmPB38AzrpvSsbN4fipGKcQ1H0ZuoerIncEbSCABXF23FGZ5xY2qw4RZ24dQv0Dq3gqGnn-pMNXbfb4AyXV1sOht7JCc6Q8hqatkUwaSg)

  
　　单重代理可以（在一定程度上）保护你的隐私，防范跨省追捕。关于这点，俺在本系列的第1篇《[网络方面的防范](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-1.html)》已经介绍过了。但如果你对隐私的防范，要求比较高（比如说，你是六扇门的重点关注对象），那单重代理的安全性就【不够】啦！为了进一步增加安全性（隐匿性），你需要使用【多重】代理。 　　那“多重代理”是啥样的捏？ 　　严格来讲，中转次数【超过1次】的，都可以算“多重代理”。为了简单起见，俺画了下面这幅“双重代理”的示意图。

![不见图 请翻墙](https://lh3.googleusercontent.com/3ISXywMCtIOfvEZv9FKqIvqGaRRAHaK0qTUxLGMGzK0_zorEGwwL_bqunsnfwYaTJrbOtLtTvaBzONtO4GuXcIwFTBszoDVO8Bwm3jIPOpIW3cfviA)

  
　　理论上，你可以随便挑选两款翻墙工具，然后搞出一个二级代理。但是这样的效果未必理想。 　　根据俺的经验，最佳组合是：用 Tor（俗称“套”）搭配其它的翻墙工具（比如：赛风、无界、自由门、VPN...），组合出多重代理。 　　这种玩法称之为【戴套的多重代理】，与 Tor 配合的另一个翻墙工具，称作“Tor 的【前置代理】”。 　　俺要强调一点：作为 Tor 的“前置代理”，本身必须是【加密】代理（有助于提高安全性）。  
　　长期翻墙的网友，应该都听说过 Tor 这个老牌的翻墙工具（俺曾经扫盲过“[戴套翻墙](https://program-think.blogspot.com/2009/09/break-through-gfw-with-tor.html)”的技术）。那些从来没听说过 Tor 的网友，可以看维基百科的“[这个页面](https://zh.wikipedia.org/wiki/Tor)”。  
　　其实拿 Tor 来翻墙，颇有杀鸡用牛刀的嫌疑。Tor 的主要强项在于：**提供匿名的网络访问，保护你的隐私**。比如名气很大的[维基解密](https://zh.wikipedia.org/wiki/%E7%B6%AD%E5%9F%BA%E8%A7%A3%E5%AF%86)（WikiLeaks），还有名气很大且很牛逼的[匿名黑客组织](https://en.wikipedia.org/wiki/Anonymous_%28group%29)（洋文叫“Anonymous”，最近连续黑掉多个大公司及美国政府部门），他们的成员都是用 Tor 来确保自己的匿名。 　　为啥 Tor 能确保匿名捏？ 　　其一， 　　Tor 在全球有很多节点，当你利用 Tor 上网的时候，从你的电脑到某个网站，需要经过若干个 Tor 节点（通常是3个节点，俗称“三级跳”）。 　　其二， 　　第1个节点虽然知道你的公网 IP，但【不】知道你访问了啥网站；第3个节点虽然知道你访问了啥网站，但【不】知道你的公网 IP；至于第2个节点，既【不】知道你的公网 IP，也【不】知道你访问了啥网站。 　　其三， 　　上述的“三级跳”线路是【动态变化】滴（通常每隔10分钟变化一次），这就使得警方难以逆向追溯。

![不见图 请翻墙](https://lh4.googleusercontent.com/GJSTx_KBgpvLFpFY5qNc_gkWuMA_KDAmoVBCOXgqTEdoXJsVnsXZRQBPvKTX2_gnJkjzJWZP7D3HcuiqYLAqcuE7VnRuZKQQ9ufP_1GpDpOTtmsqDw)  
（Tor 网络的示意图）

  
　　假如你有些悟性，看完上述示意图之后就会发现：Tor 本身就是一个多重代理！既然这样，为啥还要拿 Tor 跟其它翻墙工具搭配捏？如下有如下几个原因—— 　　其一， 　　因为万恶的 GFW 把全球大部分的 Tor 节点都列入“IP 黑名单”。因此，如果你不幸身处天朝，是很难直接访问到 Tor 节点滴！【前置代理】可以帮助你本机的 Tor 客户端接入全球的 Tor 网络。 　　其二， 　　即使你身处【墙外】，俺依然建议：使用【Tor ＋ 前置代理】。因为你还要考虑到——万一 Tor 软件出现某个致命的安全漏洞，可能会导致 Tor 的“匿名化措施”失效。而使用“Tor ＋ 前置代理”，就类似于【双保险】。 　　其三， 　　对于安全性要求很高的用户，你还要做到——既使用 Tor，又不要让 ISP 及警方发现你在使用 Tor。因为 Tor 用户毕竟还很【小众】，更容易引起怀疑。当你采用【Tor ＋ 前置代理】的方式，即使 ISP 或警方监视了你的流量，看到的是【前置代理】的流量，看【不】到 Tor 的流量。 　　（注：前面说过——“前置代理”必须是“加密代理”。因此，“Tor 流量”被包裹在“前置代理”的【加密】流量内部）  
　　为了让大伙儿有个直观的印象，放一张示意图（如下）。这张图来自俺的另一篇博文《[如何用 Tor 访问对 Tor 不友好的网站——扫盲“三重代理”及其它招数](https://program-think.blogspot.com/2020/08/Tor-Triple-Proxy.html)》。

![不见图 请翻墙](https://lh6.googleusercontent.com/dHNXCMA2uZddawgGk3kUkQFmq6sFe3ETElYWOLyvVp4p7zf6FDvq2nZnuRgZ5wrey9ajv87GlbaOW1QWVFACsw8S-sE9VxSpDAu22WVq_CjrkOJf5ffopJsrKxYXYpJSys0BBAAAeCE)  
（【双重代理】数据流示意图）

　　其实配置并不难，只需如下几步：  
　　首先，你需要准备好一个【能用的】翻墙工具——可以是 HTTP 代理（比如：[无界](https://program-think.blogspot.com/2011/12/gfw-wujie.html)、[自由门](https://program-think.blogspot.com/2010/03/choose-free-gate.html)、[赛风](https://program-think.blogspot.com/2011/10/gfw-psiphon.html)），也可以是 SOCKS 代理，还可以是 VPN（比如 [VPN Gate](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)）。先把这个翻墙工具运行起来，它用作 Tor 的【前置代理】。 　　如果你使用 Linux 并且发行版的官方仓库已经包含了 Tor，那么就从官方仓库直接安装。

　　否则的话，请【翻墙】到 Tor 的官方网站，下载一个 Tor 的软件包（下载页面在“[这里](https://www.torproject.org/download/)”）。

　　目前官网上提供两种软件包，分别是： “Tor Browser Bundle”（面向傻瓜用户） “Expert Bundle”（俗称“裸 Tor”，面向高级用户） 　　如果你下载了“Tor Browser”，参见如下这篇教程：

《[“如何翻墙”系列：扫盲 Tor Browser 7.5——关于 meek 插件的配置、优化、原理](https://program-think.blogspot.com/2018/04/gfw-tor-browser-7.5-meek.html)》

　　如果你下载了“Expert Bundle”，并且你的操作系统是 Linux/UNIX，参见如下这篇教程：

《[扫盲 Arm——Tor 的界面前端（替代已死亡的 Vidalia）](https://program-think.blogspot.com/2015/03/Tor-Arm.html)》

　　（刚才说了）Tor 有两种软件包（Bundle）。这两者的【监听端口号】略有差异。因此在配置浏览器时，也略有差异。分别说明如下：

　　**Tor Browser Bundle**

  
　　Tor 的监听端口为 `9150` 　　由于这种软件包已经内置了 Firefox，且内置的 Firefox 已经绑定到 Tor。因此，你【无需任何设置】。

　　**Expert Bundle**（裸 Tor）

  
　　Tor 的监听端口为 `9050`  
　　对于这种软件包，你要把浏览器的【SOCKS 代理】指向 Tor（地址 `127.0.0.1` 端口 `9050`），就可以通过 Tor 匿名上网了。  
　　如果你想让其它的第三方网络软件（比如：聊天软件、下载工具）通过 Tor 来隐藏你的公网 IP，也很容易。参见刚才浏览器的代理设置——SOCKS 代理，地址 `127.0.0.1`，端口号使用 `9050`（裸 Tor）或 `9150`（Tor Browser）。以 MSN 为例，你只需在 MSN 的网络设置界面填写 Tor 的 SOCKS 代理即可。 　　为了保险起见，你还需要做一些测试，验证一下你是否真的通过 Tor 上网。

　　**对于浏览器**

  
　　用浏览器访问 Tor 官网的“检查页面”（在“[这里](https://check.torproject.org/)”）；这个页面会告诉你，当前是否已经通过 Tor 访问。

　　**对于【其它】上网软件**

　　需要到“Tor 的管理界面”观察一下 Tor 的网络流量【变化】。当你使用这些第三方软件的时候，Tor 的管理界面如果显示有流量，就说明这些网络软件已经通过 Tor 联网了；反之（如果使用第三方软件时，Tor 的管理界面没有显示流量），则说明你配置有误——第三方软件【没】通过 Tor 联网。  
　　举个例子： 　　假设你用【单重】的 VPN 翻墙并发表一些抨击党国的言论。万一 VPN 提供商在 VPN 服务器上保存了你的上网日志，而党国又逼迫该 VPN 供应商交出这些日志。那么，党国的爪牙就【有可能】分析出你的上网行为。 　　用了多重代理之后，任何一个代理服务器记录你的网络流量，都无法对你的流量进行分析。 　　举例如下： 　　假设你用的是“Tor ＋ 赛风”。虽然“赛风服务器”知道你的真实公网 IP，但是无法知道你访问哪个网站，也不知道你访问的的内容（因为 Tor 的流量是加密滴）；而 Tor 的“最后一个节点”（出口节点）虽然知道你访问了哪个网站以及访问的内容，但是它不知道你来自哪里（不清楚你的真实公网 IP）。 　　除了上述好处，使用 Tor 还有另一个好处——伪装国籍。比方说，你想让自己看起来像是美国的用户，只需要修改 Tor 的配置文件，使用美国境内的【出口节点】。这种情况下，你访问的网站就会以为你来自美国。 　　当然啦，有利就有弊。以下是多重代理的一些缺点： 　　跟“单重代理”比起来，“多重代理”显然需要更多的设置。很多网友属于技术门外汉，多半对它望而却步。所以，俺才会专门写这么一篇博文，扫盲多重代理。 　　通常来说，多重代理的性能会比单重代理要差一些。 　　根据俺近几年的经验——只要【前置代理】的速度足够快，“前置代理 ＋ Tor”的速度也慢不到哪里去。以下是俺电脑上的 Tor 流量截图（基于“赛风+Tor”）。

![不见图 请翻墙](https://lh5.googleusercontent.com/99PJcrFDw0ooSRN-JikBLgbK0OTvXMVMV2qcJbkRY3HoJWKKiob6Dt6JApixCjwXTX7HsO5B4-pFRTFiyJKLpKL_umZRDnLC83df4U8Cabs1kI33Pw)

  
**[回到本系列的目录](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html#index)**

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[关于 Tor 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)》  
《[“如何翻墙”系列：扫盲 Tor Browser 7.5——关于 meek 插件的配置、优化、原理](https://program-think.blogspot.com/2018/04/gfw-tor-browser-7.5-meek.html)》  
《[扫盲 Arm——Tor 的界面前端（替代已死亡的 Vidalia）](https://program-think.blogspot.com/2015/03/Tor-Arm.html)》  
《[如何用 Tor 访问对 Tor 不友好的网站——扫盲“三重代理”及其它招数](https://program-think.blogspot.com/2020/08/Tor-Triple-Proxy.html)》

