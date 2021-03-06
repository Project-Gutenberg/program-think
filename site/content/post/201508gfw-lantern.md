---
layout: default
title: '&#8220;如何翻墙&#8221;系列&#65306;Lantern&#65288;蓝灯&#65289;&#8212;&#8212;开源且跨平台的翻墙代理'
date: None
author:
    display_name: 
---

　　本月初（8月7日），俺发了一篇《[翻墙快报](https://program-think.blogspot.com/2015/08/gfw-news.html)》。发完之后，就有几个热心读者在博客评论中提醒俺——Lantern 的2.0版本刚刚发布，效果不错。最近2周，俺尝试了一下，决定发一篇博文介绍给大伙儿。 　　顺便提醒一下： 　　党国正在热火朝天地筹备大阅兵。按照以往的惯例——每逢敏感时期，都会加大网络封锁。大伙儿手头多备几个翻墙工具，以防万一。 　　如标题所说，“Lantern”是一款开源并且跨平台的翻墙工具。“蓝灯”是它的中文名。 　　说到“跨平台”，它目前支持：Windows、Linux、Mac OS X

　　说到“开源”，其官方 GitHub 帐号在“[这里](https://github.com/getlantern)”。

　　顺便提一下：该开源项目受到美国政府的资助。

　　更多的介绍可以参见维基百科的词条（在“[这里](https://en.wikipedia.org/wiki/Lantern_%28software%29)”）。

　　“蓝灯”早在两年前（2013）就发布了初始版本，为啥俺到现在才写博文推荐捏？ 　　主要原因是：早期的蓝灯，不够易用，不够傻瓜化。比如很多人抱怨其“邀请机制”；比如早期版本需要依赖 Chrome 浏览器。比如早期版本经常登录失败。 　　相比之下，如今刚刚推出的 2.0 版本，已经很傻瓜化了，很易用了。所以俺才决定推荐它。  
  
　　它的官网是 [https://GetLantern.org/](https://getlantern.org/)，打开之后就会看到醒目的下载按钮。 　　提醒一下：其官网的页面依赖 JavaScript，你的浏览器要启用 JS 脚本。 　　一般来说，翻墙工具的官网都都会受到 GFW 的特别照顾，Lantern 的官网也不例外。所以俺再提供一个【免翻墙】的下载页面（如下）。

[https://github.com/getlantern/lantern-binaries](https://github.com/getlantern/lantern-binaries)

　　这个页面来自 Lantern 官方的 GitHub 帐号（到目前为止，GitHub 全站都可以【免翻墙】访问），该页面同时提供三大桌面操作系统（Windows、Linux、Mac）的安装包。 　　对于暂时无法翻墙的同学，你还可以考虑用 BT Sync 来获取。 　　首先安装 BT Sync，然后使用如下密钥，【自动】同步俺分享的【多款翻墙软件】。

各种翻墙软件的同步密钥  BTLZ4A4UD3PEWKPLLWEOKH3W7OQJKFPLG

　　BT Sync 客户端的[官方下载页面](https://getsync.com/)（这个链接是【页面】链接，【不要】直接“另存为”）  
　　从来没用过 BT Sync 的同学，请先看《[扫盲 BT Sync——不仅是同步利器，而且是【分布式】网盘](https://program-think.blogspot.com/2015/01/BitTorrent-Sync.html)》。  
　　（**虽然俺博客已经被 GFW 彻底封杀，但是你可以通过“RSS 博客阅读器”，看到这篇教程**） 　　（考虑到用 Windows 的读者比较多，本章节仅针对 Windows 平台）

　　Lantern 的安装文件自带“数字签名”。为了保险起见，照例先检查一下数字签名是否有效（如果你不懂得校验“数字签名”，先看“[这篇博文](https://program-think.blogspot.com/2013/02/file-integrity-check.html)”）。

　　安装很简单，双击这个 exe 既可（“一键式”安装）。

　　由于安装过程没有让你选“安装目录”，有些同学可能想知道“蓝灯安装在哪里”。很简单——你只需在“资源管理器”的地址栏输入 `%APPDATA%` 然后回车，就会进入“当前用户的 APPDATA 目录”，在该目录下，就可以看到有一个子目录叫做 lantern——这就是它的安装目录。

　　由于 Lantern 的安装【无需】管理员权限，以俺的习惯，使用【普通用户】来安装它。再次唠叨一下：能不使用管理员的场合，就尽量不要使用——可以降低一些安全风险。  
　　安装之后，你可以通过“开始菜单”或者“桌面上的图标”，来启动蓝灯。 　　然后在任务栏的“托盘区”会出现一个蓝灯的图标；同时，它还会自动弹出系统默认的浏览器，在浏览器上显示它的主界面。这个“主界面”很简单，大伙儿自己看一下就明白了。 　　如果你想退出，在任务栏的“托盘区图标”点右键，弹出的“快捷菜单”上会有退出的选项。 　　主界面的右下角有一个“配置按钮”，点击之后会弹出“Lantern 的配置界面”——这个界面同样很简单，目前只有3个复选框（选项）。 　　其中一个选项是“Proxy all traffic”，俺稍微说一下： 　　如果你勾选了这个选项，那么所有的 HTTP 请求都会走 Lantern 的翻墙通道；反之（没有勾选），那么只有那些“被墙的网站”才会走 Lantern 的线路。Lantern 内置了一个“被屏蔽的网站列表”，以此来判断那些是“被墙的”。 　　（本章节所说的“网络软件”指的是：浏览器、IM 工具、下载工具 ...） 　　蓝灯默认会在【本机地址】上开启一个 HTTP 代理的端口，端口号是 8787

　　如果你的网络软件跟它运行在【同一个操作系统】，那么你只需在网络软件的代理界面上设置 HTTP 代理——地址填写 `127.0.0.1` 端口号填写 `8787`（注：`127.0.0.1` 表示“本机地址”）

　　如果你想要【跨操作系统】共享蓝灯的翻墙通道，参见俺的另一篇博文：

《[多台电脑如何【共享】翻墙通道——兼谈【端口转发】的几种方法](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)》

　　本文发出后，经热心读者提醒，补充说一下： 　　蓝灯可以作为 Tor 的前置代理。对于那些看重【隐匿性】的网友，建议使用“Tor ove 蓝灯”的方式构造【双重代理】。

　　关于“双重代理”的原理及好处，请参见《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》系列的其中一篇。

　　这篇教程发布于2015年。之后若干年，蓝灯（Lantern）的运营模式出现了一些变化，经热心读者建议，补充说明如下： 　　前几年，有热心读者爆料说 Lantern 使用了“阿里云”。考虑到阿里巴巴是【国内】公司，而且口碑也不行。Lantern 使用阿里巴巴的云计算平台，未免让人生疑。 　　由于俺本人是【高危人士】，自从听说“Lantern 使用阿里云”，俺就【不再】使用 Lantern 作为 Tor 的前置代理。 　　蓝灯在2016年升级到【3.0】版本，开始区分为【付费】和【免费】两种模式： 付费版本——流量无限制 免费版本——有几百兆的流量限额。用完该限额之后，翻墙网速被限制为【20KB/秒】。 　　引入“付费模式”也招致诸多用户的吐槽。对于这种运营模式，俺表示可以理解（毕竟蓝灯的运营方以也需要资金来维持）。 　　但是对于像俺这样的【高危人士】，还是【不要】付费比较稳妥一些。因为任何【在线支付】的行为，都会增加身份暴露的风险。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[如何翻墙](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)》（传说中的翻墙入门教程，不定期更新）  
《[多台电脑如何【共享】翻墙通道——兼谈【端口转发】的几种方法](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)》  
《[如何让【不支持】代理的网络软件，通过代理进行联网（不同平台的 N 种方法）](https://program-think.blogspot.com/2019/04/Proxy-Tricks.html)》  
《[扫盲 VPN Gate——分布式的 VPN 服务器](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)》  
《[关于 TOR 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)》  
《[“如何翻墙”系列：扫盲 Tor Browser 7.5——关于 meek 插件的配置、优化、原理](https://program-think.blogspot.com/2018/04/gfw-tor-browser-7.5-meek.html)》  
《[“如何翻墙”系列：Tor 已复活——meek 流量混淆插件的安装、优化、原理](https://program-think.blogspot.com/2014/10/gfw-tor-meek.html)》  
《[双管齐下的赛风3](https://program-think.blogspot.com/2011/10/gfw-psiphon.html)》  
《[新版本无界——赛风3失效后的另一个选择](https://program-think.blogspot.com/2011/12/gfw-wujie.html)》  
《[自由門——TOR 被封之后的另一个选择](https://program-think.blogspot.com/2010/03/choose-free-gate.html)》  
《[扫盲 VPN 翻墙——以 Hotspot Shield 为例](https://program-think.blogspot.com/2011/09/gfw-vpn-hotspot-shield.html)》  
《[简单扫盲 I2P 的使用](https://program-think.blogspot.com/2012/06/gfw-i2p.html)》  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》（系列）

