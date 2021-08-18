---
layout: default
title: '2013年7月翻墙快报&#65288;补充介绍 VPN Gate 经验&#65289;'
date: None
author:
    display_name: 
---

　　上一次发布《翻墙快报》还是1月份的事情。之所以这么长时间没有发布《翻墙快报》，主要是因为 GFW 近期不给力啊 :) 看来方滨兴要好好检讨一下。说不定这位前校长正忙于跟病魔作战，无暇顾及 GFW :)

　　4月中旬的时候，俺写了一篇 VPN Gate 的教程《[扫盲 VPN Gate——分布式的 VPN 服务器](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)》。当时 VPN Gate 国内用户数只有58万。刚才俺又去 VPN Gate 官网看了一下，天朝用户数已经超过两百万（2235961），全球排名第一。（俺不清楚 VPN Gate 官网是如何统计的，不知道这个用户数是否准确）另外，天朝的 VPN Gate 流量（119376 GB），全球排名第二（仅次于南韩）

  
　　如今翻墙形势一片大好。但依然有少数网友抱怨说，VPN Gate 的服务器总是连不上。今天就来介绍一下这方面的经验。 　　手头已经有 VPN Gate 安装包的同学，请跳过本小节。  
　　[VPN Gate 的官网](http://www.vpngate.net/cn/)早就被 GFW 封锁了。你可以先用其它翻墙工具来下载（本文后后半部分有其它翻墙工具的获取方式）。  
　　如果你搞不到其它翻墙工具，也可以通过 [VPN Gate 官方提供的镜像站点](http://www.vpngate.net/cn/sites.aspx)下载（镜像网站如下，**无需翻墙**）。为了防止被封杀，这些镜像站点每天都会有变化。  
　　下面列出的镜像站点，更新时间是：北京时间7月12日11点31分（有可能1-2天之后就失效了，**下载要趁早**） http://pl888.nas93m.p-tokyo.nttpc.ne.jp:51259/cn/ http://p57c666.tokynt01.ap.so-net.ne.jp:17510/cn/ http://p4b0e77.tokynt01.ap.so-net.ne.jp:5222/cn/ http://pl074.nas93y.p-tokyo.nttpc.ne.jp:36503/cn/ http://pl1647.nas827.p-tokyo.nttpc.ne.jp:36513/cn/  
　　从来没用过 VPN Gate 的同学，请先看扫盲教程《[扫盲 VPN Gate——分布式的 VPN 服务器](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)》（需翻墙）。 　　无法翻墙的同学，可以通过博客阅读器看到这篇博文。这篇博文发布的时间不长，在某些博客阅读器（比如 Digg Reader 或 Feedly）的历史缓存中可以找到。 　　前面都是准备工作，现在开始说重点——连接 VPN Gate 服务器的经验。 　　VPN Gate 在运行时会定期刷新服务器列表，并保存在本地。这样就可以确保你本地的服务器列表始终是最新的。

　　俺建议每天至少运行一次。如果你有虚拟机的话，可以考虑把 VPN Gate 装到虚拟机中，就可以长期开着。即使装在虚拟机中，VPN Gate 也可以共享翻墙通道给实体机或其它电脑使用。具体请参见《[多台电脑如何共享翻墙通道](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)》

  
　　如果你经常运行 VPN Gate，通常不会出现此情况。万一你因为某些原因，连续好几天没有使用 VPN Gate，**有可能**会导致它再也无法获取服务器列表。  
　　关于这种情况的处理，俺在4月份的教程《[扫盲 VPN Gate——分布式的 VPN 服务器](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)》里，已经提到了解决办法。这里再啰嗦一下。  
　　你需要先临时运行另一个**可用的**翻墙工具（比如：自由门、无界、世界通...）。运行好了之后，在 VPN Gate 界面的服务器列表左下方有一个"**代理设置**"的按钮，点击之后会出现一个设置代理的界面。  
　　然后你就填写另外一个翻墙工具的代理。（无界默认端口是`9666`、自由门默认端口是`8580`、世界通默认端口是`8000`）填好之后，点确定。VPN Gate 就可以利用另一个翻墙工具联网。 　　这时候再点 "刷新列表" 按钮，服务器列表应该就会正常更新了。

　　**更新完之后，要记得把刚才修改过的代理设置恢复原状。**

　　如果你手头没有其它翻墙工具可用，也可以到 VPN Gate 官方提供的镜像站点，（免翻墙）重新下载一个。VPN Gate 官网每天都会更新安装包。最新的安装包里面，内置了最新的服务器列表。 　　很多同学碰到的情况是：服务器列表已经刷新了，但是无法连接到列表中的服务器。这可能有如下几种原因：

　　**1\. 该服务器已经关机 或 该服务器已经换 IP**

　　因为 VPN Gate 的服务器，大都是由各个国家的志愿者维护的。有些服务器说不定就是外国网友的家用电脑。如果是家用电脑贡献出来当 VPN Server，就无法确保长期在线。即使能长期在线，IP 地址也不会是固定的。 　　如果你的 VPN Gate，服务器列表已经有好几个小时没有刷新，那么该列表上的服务器信息就不够新鲜（某些服务器可能已经下线或改过IP了）

　　**2\. 该服务器的 IP 已被封杀**

  
　　第二种情况就是，该服务器已经被 GFW 列入“IP黑名单”。俺写的[翻墙入门教程](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)中，有介绍 GFW 常用的招数，其中之一就是“IP黑名单”。

　　**3\. 你的公网 IP 已被封杀**

　　这种情况，大伙儿可能没有注意到。

　　比如说，俺连不上某个服务器，但是俺切换了自己的公网IP之后，**同一个服务器**又可以连上了。这种情况说明，VPN Server 本身没有进入黑名单，而是自己的公网IP进入了黑名单。

  
　　俺猜测，GFW 会对国内的公网IP进行某种统计。如果发现某个公网IP频繁连接某些国外的 VPN，并且这些连接具有某些特征，那么就会在一段时间内（具体多长，俺不清楚）封锁该IP对这些 VPN 的连接。在《[2013年1月翻墙快报](https://program-think.blogspot.com/2013/01/gfw-news.html)》中，俺有提到过，GFW 开始引入"基于行为特征的检测技术"。虽然 GFW 无法破解 VPN 的加密，但或许能根据特征来判断某个 VPN 连接是否用于翻墙。 　　刚才分析了连不上服务器的三种原因。下面分别说说应对方法。

　　**1\. 先判断服务器是否在线**

  
　　很简单，你要经常刷新服务器列表，确保服务器列表经常处于最新状态。另外，要留意服务器列表中的“**登录数**”。登录数越大的，说明该服务器越活跃。

　　**2\. 判断“VPN 服务器”或“自己的公网 IP”是否被屏蔽**

　　据俺观察，GFW 对 VPN Gate 连接的阻断，不是很及时。如果你眼神好，可以看出蛛丝马迹。 　　当你双击服务器列表上的某个服务器时，VPN Gate 首先显示“连接到某某服务器”，如果服务器能连上，会接着显示“正在验证证书”和“正在验证用户信息”（后面这两个一闪而过，眼神好能分辨出） 　　如果 VPN Gate 已经显示了“正在验证证书”或者“正在验证用户信息”，这时候突然断线，那么十有八九是被 GFW 阻断的。

　　**3\. 先切换服务器，不行再切换自己的公网IP**

　　如果你仔细观察，感觉到有 GFW 阻断的迹象。那么你可以先尝试服务器列表上的其它服务器（尽量找登录数比较大的）。如果你连续尝试了很多服务器，都发现被 GFW 阻断，那么有可能是你的公网 IP 被屏蔽了。这时候就要考虑切换自己的公网 IP。 　　对于在家上网，切换公网 IP 比较容易。如果你用的是 ADSL 或 光猫 或 3G 上网卡，只要把上网设备断开（拔出或断电），稍等片刻，然后再连上。这时候你的公网 IP 应该就不同了。为了验证公网 IP 是否确实改了，可以用浏览器访问那些专门显示 IP 地址的网站。提醒一下：不同的宽带提供商，分配公网 IP 的方式不同。对于某些 ISP，这招可能不行（把上网设备重启动之后，得到的还是原来的 IP） 　　如果是在公司上网，你的公网 IP 也就是你公司的互联网出口 IP。这种情况下，你【难以】改变自己的公网 IP :(  
　　以下这些翻墙软件，都汇总到“[微软网盘](https://onedrive.live.com/?id=F5B0090663FEEADA!730)”（墙外）。  
　　很多翻墙软件都支持邮件方式获取，俺整理了如下表格；没有提供邮件获取的，俺放上了**墙内下载链接**。

软件名称

版本号

墙内下载链接

官方邮件获取

备注

世界通

4.1.0

[这里](http://img610.ph.126.net/jimNYb8Ngf6SHxl1RIHlsA==/1949777163676558355.bmp)。**下载的文件表面上是图片，其实是压缩包。  
把文件扩展名改为 7z，用 7zip 或 WinRAR 解压出内嵌的世界通。**

（暂无）

必须用 Skype 通道

无界

13.01

（暂无）

wj@wujie.net

速度和稳定性不够

自由门

7.4.0

（暂无）

freeget.one@gmail.com

速度和稳定性不够

赛风

3.59

（暂无）

get@psiphon3.com

有些网友能用，有些不行

TOR

0.2.3.25

（暂无）

gettor@torproject.org

须结合公共代理或其它翻墙工具，组合成"双重代理"

　　下面这些教程都在俺博客上（需翻墙）。因为 Google Reader 近期关闭了，大伙儿今后就没法再用 Google Reader （免翻墙）阅读俺过去的博文。实在是一大遗憾 :( 　　如果你目前能翻墙，可以先把这些教程保存到本地。万一哪天 GFW 加强封锁，说不定用得着。  
[如何翻墙](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)（传说中的全方位扫盲教程，定期更新）  
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
　　如果碰到翻墙的问题，或者想给俺提意见/建议，欢迎来信（ `program.think@gmail.com` ）。给俺写信最好用 Gmail、Hotmail、Outlook 等邮箱，**国内的邮箱很可能会撞墙，导致俺收不到。**

