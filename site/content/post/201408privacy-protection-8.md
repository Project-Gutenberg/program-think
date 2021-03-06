---
layout: default
title: '如何保护隐私[8]&#65306;流氓的桌面软件有哪些替代品&#65311;'
date: None
author:
    display_name: 
---

　　在本系列的[前一篇博文](https://program-think.blogspot.com/2014/08/privacy-protection-7.html)，已经介绍了各种桌面软件（尤其是国产商业软件）存在的隐私问题。今天这篇介绍一下这些软件的替代品。**有些软件比较难以替代，会在本系列的下一篇介绍应对措施。** 　　本文中推荐的每一款工具，都附有维基百科的链接。打开维基百科的链接，就可以看到该工具的【官网链接】。 　　在本文中，俺会介绍常见软件类型的各种替代品。针对每一个大类，会同时给出“首选替代品”和“次选替代品”。这两者的差异如下：

　　**首选替代品**

　　主要是【国外】非营利机构和组织开发的【开源】软件。 　　这类软件的特点是——通常情况下，既【没有】咱们朝廷植入的后门，也【没有】欧美政府（比如 NSA）的后门

　　**次选替代品**

　　主要是【国外】商业公司开发的【闭源】软件。

　　这类软件的特点是——通常情况下，【没有】咱们朝廷植入的后门，但【可能有】欧美政府的后门。另外，由于是商业公司开发的，在“隐私保护”方面不如“非营利组织开发的软件”（具体理由参见[本系列第1篇](https://program-think.blogspot.com/2013/06/privacy-protection-1.html)）。

  
　　各种国内商业公司的防病毒、防木马工具，至少包括“奇虎、瑞星、金山、江民、微点、腾讯、百度”等公司的产品。 　　（在首选替代品中列出的，全都是开源项目）

　　1. **改用 Linux，无需安装“防病毒/防木马”软件**

  
　　如果你还在用 Windows，并且饱受病毒和木马的困扰，是时候考虑换成 Linux 啦。如今的 Linux 已经很成熟了，主流的发行版对硬件的支持足够好，而且 Linux 上有一款神器——Wine——它可以让你在 Linux 下运行 Windows 的软件，估计 90% 以上的常用软件（包括“翻墙代理、游戏、媒体播放”等）它都支持。就算碰到少数不支持的，咱们还可以玩【操作系统虚拟机】嘛。没玩过“操作系统虚拟机”的同学，可以看俺博客上的系列扫盲教程，链接在“[这里](https://program-think.blogspot.com/2012/10/system-vm-0.html)”。 　　由于 Linux 在桌面系统还是小众的，所以病毒和木马的作者都不会考虑 Linux 平台。另外，如果你遵守一些安全规范（比如：不用 root 进行日常操作），基本上就不用担心中病毒和木马。

　　没用过 Linux 的同学可以看俺之前写的扫盲教程《[新手如何搞定 Linux 操作系统？](https://program-think.blogspot.com/2013/10/linux-newbie-guide.html)》。

　　2. **[ClamAV](https://en.wikipedia.org/wiki/Clam_AntiVirus) / [ClamWin](https://en.wikipedia.org/wiki/ClamWin)**

  
　　防病毒软件中，彻底开源的不多，今天给大伙儿天推荐的 ClamAV 就是一款【**彻底开源**】的防病毒软件。别看它是开源的，资历比某些商业杀毒软件还要老（诞生于1998年），而且查毒的功能毫不逊色。ClamAV 本身是命令行界面的，ClamWin 提供了 Windows 上的图形界面，内嵌 ClamAV 引擎。 　　下面列举它的几个特色。 特色1——ClamAV 和 ClamWin 性能开销很小，号称是最低功耗的“静音杀毒软件”。 特色2——ClamAV 支持的操作系统非常多，除了三大主流的桌面系统，还支持 BSD、Solaris、AIX、HP-UX、OpenVMS、OS/2 等。

特色3——ClamWin 支持“便携模式”（做成“绿色软件”），就可以放在“U盘或光盘”上即插即用。官网的说明在“[这里](http://www.clamwin.com/content/view/118/89/)”。

　　补充说明： 　　ClamAV 只有“查毒”功能，没有“杀毒”功能（对已发现的病毒文件，用户可以选择“删除”或“隔离”）。不过这无伤大雅。为啥捏？一旦某个软件感染了病毒，能否【彻底】杀掉，是一个问题？杀掉之后，这个软件是否还能正常工作，又是一个问题。所以俺的经验是：一旦某个系统查出病毒/木马，最安全的处理措施就是——重装系统。综上所述，“杀毒功能”对防病毒软件而言，简直就是鸡肋。而 ClamAV 只提供“查毒”，不提供“杀毒”，反而让它不至于太臃肿。 　　本文发布后，有热心读者反馈说：ClamAV 的误报率偏高。如果你担心“开源的防病毒”不够好，可以参考“次选替代品”中列举的免费商业软件。 　　（在“次选替代品”中列出的，【不是】开源项目） 　　下面再介绍几款【国外】的防病毒/防木马产品。因为这些安全产品【不开源】，所以放到“次选替代品”。 　　考虑到咱们天朝的网民都不喜欢花钱买正版，所以特地介绍几款免费的防病毒和防木马产品（别以为只有 360 是免费滴，国外免费的同类产品也不少哦）。

　　1. **[Avira / AntiVir（小红伞）](https://zh.wikipedia.org/wiki/Avira_AntiVir)**

　　这款工具来自德国，诞生于1988年，“AntiVir”是之前的名字。它面向家庭用户和非营利组织的版本是免费的。 　　免费版本支持：Windows、Android、Mac OS X 　　据俺所知，小红伞在国内用户的口碑不错，所以排第一。

　　2. **[Comodo（科摩多）](https://zh.wikipedia.org/wiki/%E7%A7%91%E6%91%A9%E5%A4%9A%E9%9B%86%E5%9B%A2)**

　　该公司1998年成立于英国，如今总部在美国。 　　免费版本支持：Windows、Android、Linux、Mac OS X 　　Comodo 提供的免费安全工具，种类挺多的（AV、FW、IPS、VPN），所以把它排在第二。

　　3. **[AVG](https://zh.wikipedia.org/wiki/AVG_Anti-Virus)**

　　这款工具来自捷克，诞生于1997。与小红伞类似，它面向家庭用户和非营利组织的版本是免费的。 　　免费版本支持：Windows、Android

　　4. **[avast（爱维士）](https://zh.wikipedia.org/wiki/Avast!)**

　　这款工具跟 AVG 是老乡（也是来自捷克），诞生于1988年。它的免费版本面向家庭用户。 　　免费版本支持：Windows、Mac OS X  
　　如果你对上述列出的防病毒/防木马软件不中意，可以去看维基百科的“[这个页面](https://en.wikipedia.org/wiki/Comparison_of_antivirus_software)”，里面列出了几十种防病毒/防木马产品的详细对比。  
　　各种国内商业公司的主机防火墙，至少包括“奇虎、瑞星、金山、江民”等。 　　对 Windows 用户而言，你直接用 Windows 自带的防火墙，基本上就能满足需求了。早在 WinXP，就内置了带图形配置界面的防火墙。到了 Vista 之后，内置防火墙的功能又增加了不少。如今，你可以通过 Windows 内置的防火墙实现如下功能： 1. 双向过滤（对内流量、对外流量） 2. 针对某些端口的过滤 3. 针对某些进程的过滤 4. ...... 　　对 Linux 用户而言，Linux 内核已经提供了 iptables / nftables，功能足够你用了。其中的 iptables 从 2.4 版本开始整合到 Linux kernel 中。而 nftables 是作为 iptables 的替代品，从今年（2014）1月份开始合并到内核主线。 　　首先，操作系统内置的防火墙在性能、稳定性、兼容性等方面，至少【不会】比第三方的防火墙更差。 　　其次，操作系统内置的防火墙，它的开发者也就是操作系统的开发者。所以，【不会】引入额外的隐私风险。 　　最后，很多商业安全公司（包括国外的），它们提供的“个人主机防火墙”，其宣传的功能大都是唬人的噱头，华而不实，说不定还影响系统的网络性能。  
　　关于“浏览器的选择”，已经在[本系列的第2篇](https://program-think.blogspot.com/2013/06/privacy-protection-2.html)分析过了，此处不再罗嗦。  
　　某些国内商业公司的输入法，至少包括“搜狗拼音、华宇拼音（原“紫光拼音”）、拼音加加、QQ拼音、QQ五笔”等输入法。 　　（在首选替代品中列出的，全都是开源项目）

　　1. **[Rime 输入法（中州韵、小狼毫、鼠须管）](https://zh.wikipedia.org/wiki/%E4%B8%AD%E5%B7%9E%E9%9F%BB%E8%BC%B8%E5%85%A5%E6%B3%95%E5%BC%95%E6%93%8E)**

　　这款输入法诞生没多久（2011年），原作者是天朝网友，网名“佛振”。 　　操作系统支持：Windows、Linux、Mac OS X。该输入法有三个中文名，分别对应这三个操作系统——Linux 下称为“中州韵”，Windows 下称为“小狼毫”；Mac OS X 下称为“鼠须管”。 　　输入方案：支持十多种输入方案（除了支持多种拼音方案，还包括两种“五笔”，另有一些俺从未听说过滴）。

　　2. **[Fcitx 输入法（小企鹅）](https://zh.wikipedia.org/wiki/FCITX)**

　　这是一个 X Window 下的输入法框架，诞生于2004年，原作者是天朝网友，网名“Yuking”。 　　操作系统支持：类 Unix（Linux、BSD 等） 　　输入方案：多种拼音、码表（五笔、郑码、仓颉 等）、日文、韩文、手写输入

　　3. **[iBus](https://zh.wikipedia.org/wiki/IBus)**

　　这也是一个输入法框架，诞生于2008年，原作者是黄鹏。 　　操作系统支持：类 Unix（Linux、BSD 等） 　　输入方案：多种拼音、码表（五笔、郑码、仓颉 等）、日文、韩文 　　（在“次选替代品”中列出的，【不是】开源项目）

　　1. **[谷歌拼音输入法](https://zh.wikipedia.org/zh/%E8%B0%B7%E6%AD%8C%E6%8B%BC%E9%9F%B3%E8%BE%93%E5%85%A5%E6%B3%95)**

　　这款是2007年诞生的，由谷歌中国开发的。 　　操作系统支持：Windows、Android 　　该输入法具有“云端同步词库”的功能。如果你担心 Google 偷窥你的个性化词库，可以禁用该功能。

　　2. **[微软必应输入法](https://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BD%AF%E5%BF%85%E5%BA%94%E8%BE%93%E5%85%A5%E6%B3%95)**

　　这款是2012年诞生的，由微软亚洲研究院开发。原先叫做“英库拼音输入法”。 　　据说整合了研究院的多项研究成果。至于效果如何，因为俺没用过，不好评价。虽然微软亚洲研究院在北京，不过俺估计：应该没被朝廷渗透 :) 　　操作系统支持：Windows、Android 　　该输入法具有“云端同步词库”的功能。如果你担心微软偷窥你的个性化词库，可以禁用该功能。 　　有些网友已经用惯了某个国产输入法，不愿意切换到其它输入法。对这种情况，俺会在本系列的下一篇介绍几种应对措施。  
　　某些国内商业公司的聊天工具，至少包括“腾讯QQ、网易泡泡、阿里旺旺”等。 　　（在首选替代品中列出的，全都是开源项目）

　　1. **[Pidgin](https://zh.wikipedia.org/wiki/Pidgin)**

　　这款是很老牌的开源 IM 软件，诞生于1998年，原先叫做“Gaim”。 　　操作系统支持：Windows、Linux、Mac OS X

　　协议支持：它支持的 IM 协议很多，分“官方支持”和“第三方插件支持”。对于“XMPP、SIP、MSN、AIM/ICQ、YIM、IRC、SILC”是官方支持，对于“Skype、QQ、飞信、Napster”是第三方插件支持。估计很多人对“支持 QQ 协议”比较感兴趣。原先 Pidgin 直接支持 QQ 协议，后来腾讯封杀了 Pidgin 客户端。目前对 QQ 的支持需要依靠“pidgin-lwqq”这个插件（此插件也是开源滴，代码库在“[这里](https://github.com/xiehuc/pidgin-lwqq)”）。据说这个插件利用的是 webQQ 的协议，所以疼逊比较难封杀。

  
　　加密支持：有一个 [OTR（Off-the-Record Messaging）](https://en.wikipedia.org/wiki/Off-the-Record_Messaging)插件，还有一个“[Pidgin-Encryption](http://pidgin-encrypt.sourceforge.net/)”插件。

　　2. **[Psi](https://zh.wikipedia.org/wiki/Psi_%28%E5%8D%B3%E6%99%82%E9%80%9A%E8%A8%8A%E8%BB%9F%E4%BB%B6%29)**

　　这款诞生于2001年，基于 C++ 开发，采用 Qt 的 GUI 库。 　　操作系统支持：Windows、Linux、Mac OS X 　　协议支持：它重点支持 XMPP 协议，可以通过 XMPP 网关跟其它的聊天服务（MSN、AIM/ICQ、Yahoo Messenger 等）互联

　　加密支持：内置 GnuPG 对消息进行加密；支持 [OTR（Off-the-Record Messaging）](https://en.wikipedia.org/wiki/Off-the-Record_Messaging)插件。

　　3. **[Gajim](https://zh.wikipedia.org/wiki/Gajim)**

　　这款诞生于2004年，基于 Python 开发。 　　操作系统支持：由于是采用 Python 语言开发，凡是能运行 Python 的系统都支持。 　　协议支持：情况跟 Psi 类似。

　　加密支持：支持 TLS/SSL 和 OpenPGP，支持 [OTR（Off-the-Record Messaging）](https://en.wikipedia.org/wiki/Off-the-Record_Messaging)插件。

　　4. **[Linphone](https://en.wikipedia.org/wiki/Linphone)**

　　这款诞生于2001年。一开始只是 Windows 桌面软件，后来陆续开发了各种手机版本。到了2013年开始支持浏览器，称为“Linphone Web”。 　　操作系统支持：Windows、Linux、Mac OS X、FreeBSD、Android、iOS、BlackBerry OS 　　协议支持：SIP 　　加密支持：支持 TLS、ZRTP、SRTP

　　5. **[Kopete](https://zh.wikipedia.org/wiki/Kopete)**

　　这款诞生于2001年，基于 C++ 开发。看名称就能猜到，它采用的是 KDE 的 GUI（基于 Qt 开发）。 　　操作系统支持：类 Unix 的操作系统（Linux、Mac OS X），貌似不支持 Windows。 　　协议支持：XMPP、Skype、MSN、AIM/ICQ、YIM（Yahoo）

　　加密支持：支持 [OTR（Off-the-Record Messaging）](https://en.wikipedia.org/wiki/Off-the-Record_Messaging)插件，还有个“kopete-cryptography”插件。

　　6. **[Jitsi](https://en.wikipedia.org/wiki/Jitsi)**

　　这款诞生于2003年，基于 Java 开发。 　　操作系统支持：由于是采用 Java 语言开发，凡是能运行 Java 的系统都支持。 　　协议支持：XMPP、SIP、MSN、AIM/ICQ、YIM（Yahoo）

　　加密支持：支持 [OTR（Off-the-Record Messaging）](https://en.wikipedia.org/wiki/Off-the-Record_Messaging)插件。

　　7. **[Tox](https://en.wikipedia.org/wiki/Tox_%28software%29)**

　　这款是后起之秀，去年（2013）才诞生的（“棱镜门丑闻”催生了它）。虽然刚诞生不久，但是很火。它的目标是——提供一个无法监控的 Skype 替代品——彻底的加密，没有后门，无需中间服务器。

　　严格来讲它只是一个开源的协议框架，不同的开发人员可以根据该协议开发出不同的客户端。比如 uTox 是 Windows 的客户端；Venom 是采用 GTK+ 界面库的 Linux 客户端；qTox 是采用 Qt 界面库的 Mac OS X 客户端；而 Antox 是 Android 上的 Tox 客户端......[这个页面](https://wiki.tox.im/Client)列出了各种各样的 Tox 客户端（十多种）。另外，还有一个“[Pidgin 插件](http://tox.dhs.org/)”，你可以用它在 Pidgin 上进行 Tox 聊天。

　　操作系统支持：Windows、Linux、Mac OS X、Android、iOS 　　协议支持：跟前面几款不同，它采用的是自己独有的“Tox protocol”。

　　加密支持：采用 [NaCl](https://en.wikipedia.org/wiki/NaCl_(software)) 库对所有通讯流量进行加密。

　　补充：Tox 出来的时间还很短（不到两年），俺估计成熟度还有待提高。先不要急着用它。

　　8. **[Bitmessage（比特信）](https://en.wikipedia.org/wiki/Bitmessage)**

　　这款跟 Tox 很类似，也是去年才诞生的，也是完全依赖于 P2P（无需中心服务器），也是强调加密，也是为了对抗政府的监控。从0.3.5版本开始，它提供了 Chans 功能——相当于匿名化的邮件列表（同样无需中心服务器）。 　　操作系统支持：基于 Python 编写，跨平台 　　协议支持：跟前面几款不同，它采用的是自己独有的通讯协议。 　　加密支持：基于公钥加密体系，对所有通讯流量进行加密 　　补充：Bitmessage 出来的时间还很短（不到两年），俺估计成熟度还有待提高。先不要急着用它。 　　（在“次选替代品”中列出的，【不是】开源项目）

　　1. **[Google Hangouts（环聊）](https://zh.wikipedia.org/wiki/Google%E7%8E%AF%E8%81%8A)**

　　这款是 Google 在2013年发布的 IM 工具，它用来取代 Google Talk 滴。 　　这玩意儿提供“纯网页版本”——这种情况下无需安装桌面客户端，于是就能避免桌面软件导致的隐私问题。但是服务端依然存在隐私问题——Google 会看到你的聊天内容。

　　2. **[Skype](https://zh.wikipedia.org/wiki/Skype) 国际版**

　　Skype 曾经是 eBay 旗下，2011年被转手卖给微软。 　　它的优点在于：用户数量众多，而且语音聊天的质量也挺好。缺点在于：据未经证实的传闻，Skype 的客户端可能有 NSA 的后门。退一步讲，就算客户端没有后门，但是服务端依然存在隐私问题。 　　另外再唠叨一下：如果想用 Skype，一定要用【国际版】的 Skype，千万【不要用】“TOM 版”和“光明版”。在2013年11月之前，Skype 的中方合作伙伴是 tom.com（李嘉诚旗下）。在过去几年，“TOM 版 Skype”已经被发现有严重的后门（会对聊天文本进行监控）。2013年11月之后，Skype 换了一个新的中国合作伙伴——光明方正（《光明日报》与北大方正的合资公司），于是有了一个新的“光明版 Skype”。考虑到《光明日报》是党国喉舌，这个“光明版 Skype”也不靠谱。 　　除非是纯 P2P 的 IM 软件（比如 Tox），否则的话，除了要考虑客户端的隐私问题，还要考虑服务端的隐私问题。 　　打个比方：如果你用 Pidgin 跟别人进行 QQ 聊天。虽然 Pidgin 作为桌面软件本身是靠谱，但腾讯的【服务器】是不靠谱滴。这种情况下，腾讯依然有可能偷窥到你的隐私。（在本系列后续博文，俺会介绍互联网服务的隐私问题）。  
　　某些国内商业公司的下载软件，至少包括“迅雷、FlashGet（快车）、QQ旋风、VeryCD”等。 　　（在首选替代品中列出的，全都是开源项目）

　　1. **[Free Download Manager（FDM）](https://en.wikipedia.org/wiki/Free_Download_Manager)**

　　这是一款多协议的下载工具，诞生于2004年。 　　操作系统支持：Windows 　　协议支持：HTTP、FTP、BT、RTSP/MMS 　　特色：能从视频网站（比如 YouTube）下载 Flash 视频；它的“HTML Spider”功能可以抓取整个网站的页面（类似搜索引擎爬虫）； 　　补充说明：如果安装之后碰到中文界面乱码，解决方法是——安装过程中先选择“English”，安装完成后选主菜单“View”再选“Language”切换成中文。

　　2. **[Shareaza](https://zh.wikipedia.org/wiki/Shareaza)**

　　这是一款老牌的 P2P 工具，诞生于2000年。它的原作者同时也是 Gnutella2（简称“G2”）协议的作者。 　　操作系统支持：Windows 　　协议支持：Gnutella、G2、eDonkey、BT、HTTP、FTP 　　特色：支持的协议算是比较全的，界面挺花哨

　　3. **[MLDonkey](https://zh.wikipedia.org/wiki/MLDonkey)**

　　这是一款支持多协议的下载工具，诞生于2001年。刚开始只是一个 Linux 工具，只支持 eD2k（电驴网络），后来扩展成跨平台并支持多种网络协议。

　　它本身是只有命令行界面。不习惯命令行的，可以去找第三方的图形界面前端（比如“[Sancho](http://sancho.awardspace.com/)”）。使用前需要先进行一些设置。总的来说，更适合懂技术的网友，而不适合新手。

　　操作系统支持：Windows、Linux、Mac OS X 　　协议支持：eDonkey、Kad、BT、HTTP、FTP 　　特色：下载 eD2k/Kad 资源时，可以同时连多个 emule 服务器

　　4. **[eMule（电骡）](https://zh.wikipedia.org/wiki/EMule)**

　　这款 P2P 工具诞生于2002年，一度是很受欢迎的开源下载工具（截止2009年9月，eMule 在 SourceForge 的下载数超过5亿）。不过最近几年的开发不活跃了。 　　操作系统支持：Windows 　　协议支持：eDonkey、Kad

　　5. **[Transmission](https://zh.wikipedia.org/wiki/Transmission)**

　　这款是 BT 的客户端，诞生于2005年。

　　操作系统支持：Linux、Mac OS X、BSD、Windows（对 Windows 的支持依靠“[Transmission-Qt for Windows](http://trqtw.sourceforge.net/blog/)”）

　　协议支持：BT 　　特色：被众多 Linux 发行版（包括 Ubuntu、Mandriva、Linux Mint、Fedora、Puppy Linux、openSUSE 选作默认 BT 下载工具）

　　6. **[aMule](https://zh.wikipedia.org/wiki/AMule)**

　　这款 P2P 工具诞生于2003年，看名字就知道它的功能跟 eMule 很像。 　　操作系统支持：Windows、Mac OS X、类 Unix 　　协议支持：eDonkey、Kad

　　7. **[qBittorrent](https://zh.wikipedia.org/wiki/QBittorrent)**

　　这款是 BT 客户端，诞生于2006年，支持的操作系统比较多，难得还能支持 Android。 　　操作系统支持：Windows、Linux、Mac OS X、FreeBSD、Android 　　协议支持：BT 　　（在“次选替代品”中列出的，【不是】开源项目）

　　1. **[μTorrent](https://zh.wikipedia.org/wiki/%CE%9CTorrent)**

　　看名称就知道，这是 BT 的客户端。诞生于2005年。 　　操作系统支持：Windows、Linux、Mac OS X、Android 　　协议支持：BT 　　特色：非常轻量级（Windows 下的3.4.2版本竟然只有1兆多）

　　2. **[Tixati](https://en.wikipedia.org/wiki/Tixati)**

　　这款是 BT 客户端，诞生于2009年，名气不大。 　　操作系统支持：Windows、Linux 　　协议支持：BT 　　特色：系统资源占用小，有丰富的图表展示界面 　　很多天朝的网友使用迅雷是为了下载迅雷协议（thunder://）的网址。迅雷协议不是开放的，暂时没有太好的替代品，你不得不继续使用迅雷客户端。在这种情况下，你需要采用一些安全措施来防止迅雷客户端。本系列的下一篇博文会介绍各种隐私方面的防范措施。 　　如果你对上述列出的下载软件不中意，可以去参考维基百科的如下几个页面：

[各种 BT 客户端比较](https://en.wikipedia.org/wiki/Comparison_of_BitTorrent_clients)

  
[各种电驴客户端比较](https://en.wikipedia.org/wiki/Comparison_of_eDonkey_software)  
[各种文件分享工具比较](https://en.wikipedia.org/wiki/Comparison_of_file_sharing_applications)  
[各种下载管理器比较](https://en.wikipedia.org/wiki/Comparison_of_download_managers)  
　　某些国内商业公司的媒体播放软件，至少包括“暴风影音、百度音乐（原“千千静听”）、QQ 音乐、射手影音”等。 　　（在首选替代品中列出的，全都是开源项目）

　　1. **[VLC](https://zh.wikipedia.org/wiki/VLC%E5%A4%9A%E5%AA%92%E9%AB%94%E6%92%AD%E6%94%BE%E5%99%A8)**

  
　　这款诞生于2001年，也算是比较老牌的。在开源播放器中，它估计是最受欢迎的，截止俺写本文时，累计下载量超过13亿人次（参见“[这个页面](https://videolan.org/vlc/stats/downloads.html)”）。另外，在所有的播放器中（包括开源和非开源），VLC 是支持操作系统最多的。所以俺把它排在第一位。 　　操作系统支持：Windows、Linux、Mac OS X、Android、iOS、BSD、BeOS、Solaris、OS/2、DOS、Syllable、QNX 　　格式支持：各种常见的视频、音频格式（你能想到的，应该都支持） 　　特色：除了支持的操作系统最多，VLC 估计还是兼容性最好的。比如俺在一个干净的 WinThinPC 系统中测试，VLC 可以正常播放视频，而 SMPlayer 和 MPC-HC 都出现错误提示。

　　2. **[MPlayer](https://zh.wikipedia.org/wiki/MPlayer) / [SMPlayer](https://zh.wikipedia.org/wiki/SMPlayer)**

　　MPlayer 诞生于2000年，是一个视频播放的后端（命令行界面）。它可以跟几种不同的 GUI 前端搭配，比较有名的是前端是 SMPlayer。SMPlayer 诞生于2006年，是比较轻量级的，它的安装包（内置 MPlayer）比 VLC 小，Windows 下大概10多兆。 　　操作系统支持：SMPlayer 支持 Windows、Linux、BSD 　　格式支持：各种常见的视频、音频格式（你能想到的，应该都支持）

　　3. **[Kodi（XBMC）](https://zh.wikipedia.org/wiki/XBMC)**

　　这款诞生于2002年。刚开始是打算做一个运行在 XBox 之上的播放器，所以原先名叫“XBMC”（XBox Media Center）。后来支持的平台越来越多了，XBox 反而不是重点了，于是改名叫 Kodi。 　　操作系统支持：Windows、Linux、Mac OS X、Android、iOS、Apple TV OS、BSD 　　格式支持：各种常见的视频、音频格式（你能想到的，应该都支持） 　　特色：它采用基于 Python 的插件来扩展功能，甚至可以在它上面运行 Python 写的小游戏。

　　4. **[MPC-HC](https://zh.wikipedia.org/wiki/Media_Player_Classic)**

　　先来说一下 MPC——这是某个老外在2003年打造的轻量级播放器，界面完全模仿 Windows Media Player 6.4 版本。一开始是闭源的，后来完全开源了。可惜在2006年停止开发。然后另一个老外根据 MPC 的源代码，衍生出一个新的开源项目 MPC-HC 并继续开发至今。 　　操作系统支持：Windows 　　格式支持：各种常见的视频、音频格式（你能想到的，应该都支持） 　　特色：界面风格是它的特色，继续保留原先 Windows Media Player 6.4版本的风格，适合喜欢复古的网友。 　　（在“次选替代品”中列出的，【不是】开源项目）

　　**[foobar2000](https://en.wikipedia.org/wiki/Foobar2000)**

　　这款诞生于2002年，是免费的音乐播放软件，而且很小巧（目前的1.3.3版本只有3兆多）。 　　操作系统支持：Windows（XP 或更高） 　　格式支持：各种常见的音频格式，至少包括：MP1、MP2、MP3、MPC、AAC、WMA、Ogg Vorbis、FLAC/Ogg FLAC、ALAC、WavPack、WAV、AIFF、AU、SND、CD、Speex、Opus 　　特色：可以直接播放压缩包里面的音频文件（无需解压）。  
　　如果你对上述列出的媒体播放软件不中意，可以去看维基百科的“[这个页面](https://en.wikipedia.org/wiki/Comparison_of_video_player_software)”，里面列出了几十种媒体播放软件的详细对比。  
　　某些国产的邮件客户端，比如 Foxmail。 　　（在首选替代品中列出的，全都是开源项目）

　　**[Mozilla Thunderbird（雷鸟）](https://en.wikipedia.org/wiki/Mozilla_Thunderbird)**

　　这款是 Firefox 的同门兄弟——它俩都出自大名鼎鼎的 Mozilla 门下。Mozilla 是个非盈利组织，而不是商业公司。所以 Mozilla 旗下的软件是比较靠谱滴。 　　它估计是名气最大的开源邮件客户端，功能齐全——基本上你能想到的，它都有了。而且具有很强的可定制性。 　　操作系统支持：Windows、Linux、Mac OS X

　　加密支持：支持 [S/MIME 标准](https://en.wikipedia.org/wiki/S/MIME)，可以通过 [Enigmail 插件](https://zh.wikipedia.org/wiki/Enigmail)进行公钥加密和签名（基于 OpenPGP）。

　　（在“次选替代品”中列出的，【不是】开源项目）

　　**微软的 Outlook 客户端**

　　（微软有两款 Outlook，此处泛指这两款）对于微软的 Outlook，大伙儿应该都比较熟悉，俺就不介绍了。 　　相比国产的邮件客户端，微软的 Outlook 可以避免被党国植入后门。但是微软的 Outlook 依然有可能被 NSA 植入后门。老实说，俺没觉得有啥理由可以让你“不选 Thunderbird 而去选 Outlook”。  
　　俺的见识很有限，所以本文介绍的替代品，肯定不全面。大伙儿如有其它补充，欢迎[到本文留言](https://program-think.blogspot.com/2014/08/privacy-protection-8.html)。

[回到本系列的目录](https://program-think.blogspot.com/2013/06/privacy-protection-0.html#index)

