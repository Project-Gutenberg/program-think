---
layout: default
title: '扫盲 BTSync&#65288;Resilio Sync&#65289;&#8212;&#8212;不仅是同步利器&#65292;而且是&#12304;分布式&#12305;网盘'
date: None
author:
    display_name: 
---

  
　　几周前（2014年末），俺发了一篇《[博客开通【免翻墙】镜像，另通告网盘电子书的问题](https://program-think.blogspot.com/2014/12/blog-mirror.html)》，其中提到了：俺的【Dropbox 网盘】连续几个月总是处于“流量超限”的状态，基本上【没法】用来下载电子书了。当时就提到了俺的备选计划——用 BT sync 来作为“第三网盘”。  
　　（发本文之前不久）**经过多位热心读者的大力支持，经过几天的不懈努力，已经完成了“微软网盘”到“BitTorrent Sync”的迁移工作。**再次向这批热心读者表示感谢。可惜俺不能说出他们的名字/网名，以免给他们带来不必要的麻烦——他们只能作为“幕后无名英雄”。 　　既然迁移工作已经完成，今天就发一篇教程，向大伙儿简单扫盲一下 BitTorrent Sync 的使用。 　　GFW 从2017年7月开始封锁 BTsync 官方的追踪服务器（Tracker Server），导致墙内大部分 BTsync 客户端无法正常工作。对此，俺专门写了一篇博文（如下），介绍应对的招数。

《[聊聊 GFW 如何封杀 Resilio Sync（BTSync）？以及如何【免翻墙】继续使用？](https://program-think.blogspot.com/2017/08/GFW-Resilio-Sync.html)》

　　另外，“BitTorrent Sync”从2016年开始改用新的名称——“Resilio Sync”，不过俺还是习惯于原来的名称。为了打字省力，本文使用简称“BT Sync”这个名称。  
　　BT 下载，相信大伙儿都知道的。今儿个要介绍的 BT Sync，跟 BT 下载一样，都是 [BitTorrent 公司](https://en.wikipedia.org/wiki/BitTorrent_(company))发明滴玩意儿，都是采用 P2P 协议来进行传输。 　　简而言之，BT sync 是一个文件同步工具，让你在几台不同的设备之间，同步文件。 　　既然是“文件同步工具”，那么最基本的“增量同步”功能，当然是必不可少的。另外，据俺测试：同步完成之后，如果在“发起端”对文件改名，但是文件内容不变，BT Sync【不会】重传文件内容——这算是比较智能的。  
　　首先来说说 BT Sync 作为同步工具的优点。至少有如下几个： 1. 不需要有自己的服务器 2. 不需要有公网 IP——如果两台设备都在【内网】，只要这两台设备都能访问到公网，就可以相互同步 3. 文件数量【无】限制，文件大小【无】限制 4. 支持多种网络形态——可以“公网上互相同步”，也可以是“局域网内相互同步”。 5. 支持各种操作系统（以下列表摘自洋文维基百科）

> Microsoft Windows (XP SP3 or later) Mac OS X (10.6 or later) Linux FreeBSD NAS Devices Android Amazon Kindle Fire iOS
> 
> Windows Phone

  
　　再来说说 BT Sync 作为“分布式网盘”的优点——这也就是为啥，俺决定用它来分享“电子图书馆”和“翻墙工具”。 1. 【没有】存储空间的限制——真要说空间限制，那就是参与节点的硬盘容量（如今【TB 级】的硬盘已经不稀奇了） 2. 【没有】下载流量的限制——与之对比，大部分商业网盘都有这个限制。就是因为这个限制，俺的 Dropbox 网盘才会瘫痪。 3. 【没有】文件大小限制——与之对比，大部分商业网盘对“单个文件大小”都作了限制。 4. 【没有】审查——俺想在上面分享啥，就分享啥——咱们朝廷管不了，美国的版权法也管不了（一想到这点，心里那个爽啊）。 5. 【没有】费用——老读者都明白，俺是很讨厌付费服务的——其实俺不缺钱，俺是担心身份暴露（即使“比特币”支付，也【不是】彻底“匿名”的） 6. 【很难】被封杀——与之对比，国外的商业网盘，GFW 说封杀就封杀（比如俺用来分享电子书的“微软网盘”和“Dropbox 网盘”都撞墙了） 　　（看完这些优点，或许你就明白——为啥 BTSync 被称为“Dropbox 终结者”） 　　不同的 BT Sync 节点之间进行数据传输时，会采用“强加密”的方式，以防止数据传输流量被嗅探（偷窥）。 　　只有参与同步的节点，才能解密；而那些帮你中转的“中转服务器”，是没有办法解密的。因此，即使你的 ISP（电信运营商）监视你的流量，也【无法】知道你通过 BT Sync 传输了啥文件。  
　　BT Sync 流行之后，开源的 BT Sync 替代品也已经出现了——名叫 [Syncthing](https://en.wikipedia.org/wiki/Syncthing)。可惜这款工具【不】适合用来做【大范围】分享。 　　考虑到有很多读者建议俺使用 Syncthing 同步电子书，专门说一下俺的顾虑—— 用 Syncthing 进行同步，必须进行【双向确认】。如果是少数几个人，“双向确认”没啥关系。但俺提供的电子书，有成千上万的读者进行同步，如果采用 Syncthing 的话，单单“双向确认”这个操作，就会把俺累死 :(  
　　要下载 BT Sync，请猛击它的官网链接 [https://www.getsync.com/](https://www.getsync.com/)，就可以看到下载链接。  
　　如果你下载的是 Windows 上运行的 exe，会自带“数字签名”。为了保险起见，校验一下。（如何校验 exe 的数字签名，请看《[扫盲文件完整性校验——关于散列值和数字签名](https://program-think.blogspot.com/2013/02/file-integrity-check.html)》） 　　（考虑到大部分人用的是 Windows，俺就以这个系统为例） 　　你下载的 exe 文件是【绿色】滴，可以直接双击运行。启动的时候，如果系统弹出一个“登录对话框”让你输入管理员密码，你直接取消掉——因为 BT Sync 在普通用户的权限下，也可以运行。

　　（在《[如何防止黑客入侵](https://program-think.blogspot.com/2010/06/howto-prevent-hacker-attack-0.html)》系列中，俺专门强调过——**能不用管理员权限，就尽量别用**）

　　运行之后，有两种可能： 1. 如果系统的 IE 版本足够高，BT Sync 会显示出客户端界面。

2\. 如果系统的 IE 版本比较低，BT Sync 会自动弹出系统中的默认浏览器，并打开 BT Sync 的 Web 管理界面（如下图）。万一没有自动弹出浏览器，你可以自己打开浏览器，访问 `http://127.0.0.1:8888/` 就可以看到 BT Sync 的管理界面。

![不见图 请翻墙](https://lh5.googleusercontent.com/OTTO6Mbho-sztDO4dRNKW0nExo2alOVxbXiPmUgaEAqZaJIA4xaM63krRDBE6wn6IYcdTzA8KrueruU4h0K6tust4WGku1bTFOgspyRe9WO7ITQFoZhRrZcglWhK8zDCP93m)

　　前面说了好多屁话，现在终于说到重点部分啦。

　　（**本文下面的使用说明，采用是的 BTSync 1.4 版本的截图。后来 BTSync 又出了好几个新版本，界面会有变化。大伙儿只需抓住关键点，无需在意界面的差别**）

　　要使用 BT Sync 的功能，首先要了解“同步密钥”的概念。 　　每个参与同步的目录，都有其密钥。你只有拿到这个密钥，才能同步该目录的文件。 　　对于普通的使用场景，每个同步目录对应两个密钥：一个是“读写密钥”，另一个是“只读密钥”。顾名思义，拥有“读写密钥”的节点，可以修改同步目录的内容；反之，拥有“只读密钥”的节点，只能读取，无法修改——所谓的“无法修改”，就是说：即使你修改了同步目录的内容，修改结果也【不会】同步给其它节点（所以这种修改是【无】意义的）。 　　对于目前的 1.4.XXX 版本，这两种密钥的长度都是【33 个字符】。“读写密钥”总是以 A 开头；“只读密钥”总是以 B 开头。因此，密钥的有效长度是 32 个字符（有兴趣的同学可以去算一下，此密钥包含多少比特）。这么长的密钥，基本上不用担心被暴力猜解（至少10年之内不用担心）。 　　至于如何得到密钥，请看下面的介绍。 　　考虑到大部分同学，不喜欢（或者看不懂）洋文界面。所以第一次启动之后，先把“洋文”改为“天朝文”。配置界面的截图如下。

![不见图 请翻墙](https://lh6.googleusercontent.com/7uv0nEZiOZh192w4tMxjP3QqpOb40xdgji_VDnPQPMv5iILZM1WWdJcp1yYEDHo1y6Bj36rBN4ChZI5yUK28e5iZypHxS1WfQbxsJGmFo_aD2YHbMYuY2gLTSPT7MT-Wx119)

  

![不见图 请翻墙](https://lh5.googleusercontent.com/uFWX42M6YMtiFCM8wyRlpK1J1jHGWlkjI9QMVsZc_8xaEvgZYSASgy_WQOevk2_g5tGrBQOQ7SloajXEda64lGvdGdhx50Gs_cf50wvPlVXrAHMmJAE6IraWW8sbB1eYWBKi)

  

![不见图 请翻墙](https://lh5.googleusercontent.com/99AESZ3S4PebuhvOmo8lN9aCPuM7fqZQs_NpwcFoa38RXosjpUL3zvB_wdwEGUpNNhCvOHwrM7EZQG-4Q6cO_TAiqIJ9_liROJaWnV46BGZ1UYG3bjc_kvrf8EIb48kACiFw)

  
　　先从比较简单的“接受同步”说起。 　　比如说，俺已经共享了一个“翻墙软件”的同步目录，然后俺把只读密钥公布如下：

BTLZ4A4UD3PEWKPLLWEOKH3W7OQJKFPLG

　　当你拿到这个密钥之后，可以通过如下步骤，导入密钥，并在你本机创建一个同步目录。（截图如下）

![不见图 请翻墙](https://lh5.googleusercontent.com/UfsCqxhuVFHDq45M9TwoUqpP7ca62VH1PLZVIwc3Vetau7BycCEb-YGZO4rUqsCSds1rwuqeCGuHh6j1dxUTIBogPgxFjjH1cJeUa4boJ8-4z-Yg8Z5iuo2Q9cPbfbDC5Wa6)

  

![不见图 请翻墙](https://lh4.googleusercontent.com/CEeyC7gy2j1DEcM0NXSQ15fkp9YkQAGEIxKuk81VwbJ2V_3kLnCHeYuz69FbYjModhrG8gjEmsbKiTXil_gq1GwKWna-G4Dp81FKEoc2AqKEXOGhSqMEZx0mWJAMAc8CCLjG)

  

![不见图 请翻墙](https://lh3.googleusercontent.com/mkJTCJl62BX-7hK-aNyzkotNEmSiWkbmFyEy5TyzltHEKA9kyHoDpfb-OMihvrRN3BuIPzsiWxF0aqKiylSc0hcUMLdtZo-MxsoXFq0-B6HAhbtbooAj1g4c0j-KSqn2eMpy)

　　完成上述步骤之后，BT Sync 就把你选择的目录作为同步目录。今后俺如果往自己的“翻墙工具”目录增加了新的软件，你的 BT Sync 会自动同步并保存到你的这个目录。

　　在这个同步目录里面会创建一个名为 `.sync` 的子目录。这个 `.sync` 目录会包含 BT Sync 的一些配置信息（可能该目录的密钥也在里面），你【可别】把它给删喽。

　　接受了某个同步目录之后，在 BT Sync 的主界面上，会显示该目录的信息。 　　这时候，你可以修改该“同步目录”的“选项参数”。（截图如下）

![不见图 请翻墙](https://lh4.googleusercontent.com/Hw_E-okAzE2ZO0Fqs8Ma2QULKW6EUFInShHix-gXY7S5L1oN2G-nXwmNDpEsW1Ab-vX1jmBJXv8oXKBi3rCyaSsP7U9z1EZcMRxvSBlwd82O7sBhJuZoW9t2lo5q019XqkM0)

  

![不见图 请翻墙](https://lh4.googleusercontent.com/ISuyiZM6BJ6H61dKQYevvvPYFVKKuNoe53q7WgGAa3GiYm5_PaX4c018ECebQDmCSq4CGll79pt1g56Dh5cuF3UrIVvYoL-L-9LI2AJaJ5drsC61U6TnIKDL99nNdMuLaZR6)

  
　　说完“接受同步”，再来说说“发起同步”。

![不见图 请翻墙](https://lh3.googleusercontent.com/6XW97K3p8tAgtd5L1090kOiIQAum69hrYCr-_1FEr54Q8iWfr9P_wKoIjKHATUBUkH7nHkBBlo5yCLcQdLmK-ksO5pe8A3ubMDlnWi_aNpgVabXfiYseA9-Z5l02KL0KRoiV)

![不见图 请翻墙](https://lh3.googleusercontent.com/mkJTCJl62BX-7hK-aNyzkotNEmSiWkbmFyEy5TyzltHEKA9kyHoDpfb-OMihvrRN3BuIPzsiWxF0aqKiylSc0hcUMLdtZo-MxsoXFq0-B6HAhbtbooAj1g4c0j-KSqn2eMpy)

　　跟前面一样，你可以修改该“同步目录”的“选项参数”。（截图如下）

　　由于你是发起方，所以你默认就具有了“读写密钥”。这个“读写密钥”很重要，【**不可轻易泄露**】。一旦泄露，得到读写密钥的节点，就可以修改这个目录的内容。

  
　　前面提到，同步目录下的 `.sync` 目录会包含一些配置文件（可能也含有密钥，俺不太确定）。所以，为了保险起见，当你发起【多个】同步目录的时候，这几个目录相互之间【不要】嵌套包含。

![不见图 请翻墙](https://lh4.googleusercontent.com/Hw_E-okAzE2ZO0Fqs8Ma2QULKW6EUFInShHix-gXY7S5L1oN2G-nXwmNDpEsW1Ab-vX1jmBJXv8oXKBi3rCyaSsP7U9z1EZcMRxvSBlwd82O7sBhJuZoW9t2lo5q019XqkM0)

  

![不见图 请翻墙](https://lh6.googleusercontent.com/4Jox_NS5FcSnYYdX6EWJrvWFyWRaC63UwVZs72JK1_E64HCIU5Z0kcOBZw94nRytOFZhiB_xxjEmV0iCjDRL0YpwEPYIi6PBrCetctemL3T8p8oMxXzUi7qcgFlfI6w_yddr)

  
　　最后，来说说全局的“选项”——也就是一开始修改“语言”的地方。 　　全局选项有几个地方，俺需要提醒一下。 　　1 　　如果你的 BT Sync 使用 SOCKS 代理联网，【强烈建议】勾选“使用代理服务器用于主机名解析”这个复选框。 　　2 　　BT Sync 默认会使用当前系统的主机名，作为它的节点名（也叫“设备名”）。 如果你对隐私比较在意，建议到全局选项的界面中，把 BT Sync 的设备名修改掉，改成一个跟你本人真实身份无关的名称。 　　本章节专门汇总使用过程中碰到的奇奇怪怪的问题。 　　如果找不到节点，可以尝试如下操作，或许就可以找到了（有时候要看运气）： 1. 先把已经添加的同步目录删除（在界面上选中，点菜单中的“断开连接”） 2. 重新导入密钥 　　运行 BT Sync 的系统，最好是开启自动时间同步。否则的话，如果系统时间严重不准，会导致 BT Sync 无法正常工作。 　　因为今天是扫盲，就先聊最基本的功能使用。以后有空再聊高级话题——其实俺也是刚上手不久，没啥高级话题可说 :( 　　在刚才示范的时候，已经提到——俺用 BT Sync 来分享翻墙工具，密钥如下：

BTLZ4A4UD3PEWKPLLWEOKH3W7OQJKFPLG

　　用 BT Sync 分享翻墙工具，最大的好处是——可以绕过 GFW。只要有一个【墙内的】BT Sync 节点拿到翻墙工具，那么其它的【墙内节点】也可以同步并得到。而 GFW 是部署在天朝的国际出口。【墙内】两台电脑之间的传输，【不会】经过 GFW。 　　经过前几篇博文的铺垫，很多电子书爱好者估计已经跃跃欲试了。 　　下面就是俺用 BT Sync 分享的电子书目录的密钥。每个目录的结构，跟俺的微软网盘上的目录结构，是基本一致的。

B7P64IMWOCXWEYOXIMBX6HN5MHEULFS4V    俺博客的“离线浏览页面”和“博客电子书制作脚本”
BRSSYZTSAC6UGYTUOJ22L4GCO7QESPPBD    政治（含大量禁书）
BNZ6DOA6W577O6GUNH7C3MY6DWC6FTDQB    心理学
BSH7FXJFVWJTKWGSX5GTWX7PHZZ2D2M7Q    历史
B2FRYA6AXCDW6CF4YJVFWKH2HAXOFICOX    经济
B3WNBTAAFFAODFR6FQ3E3L5BBSJAFNBSJ    管理
BZR4TTYHT25QWUIE6YNMAKWUGBHKSGLC6    社会学
BMBB5YLBIJJAE5H6TP27OS7YCEUKCYHZK    文艺
B6WWVBXPMZDI5IL4KED6AAHA5FO4UNKQF    哲学
BMWWZALG4P56LREF47EE2WSWHZEM4E6BL    军事
BUPSDXFA3TP7KCMLHALRHLIX2FEJEUJFE    IT（信息技术）

　　**后续更新：** 　　本文发布后又过了5年（2020），俺在电子书网盘上又增加了一个【科普大类】，同步密钥如下：

BKKORLE67ZDUHGHVWAVSRK3N5I7BXLCED    科普

  
　　大伙儿可以猛击如下链接，就可以看到【所有】电子书的列表（全都按学科进行分类了）。该清单也包含了上述密钥及相关说明。

**[https://github.com/programthink/books](https://github.com/programthink/books)**

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[计算机网络通讯的【系统性】扫盲——从“基本概念”到“OSI 模型”](https://program-think.blogspot.com/2021/03/Computer-Networks-Overview.html)》  
《[聊聊 GFW 如何封杀 Resilio Sync（BTSync）？以及如何【免翻墙】继续使用？](https://program-think.blogspot.com/2017/08/GFW-Resilio-Sync.html)》  
《[聊聊分布式散列表（DHT）的原理——以 Kademlia（Kad） 和 Chord 为例](https://program-think.blogspot.com/2017/09/Introduction-DHT-Kademlia-Chord.html)》  
《 [提供“博客离线浏览”和“电子书制作脚本”——用 BT Sync【免翻墙】自动同步](https://program-think.blogspot.com/2015/03/blog-sync.html)》  
《[多台电脑如何【共享】翻墙通道——兼谈【端口转发】的几种方法](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)》  
《[如何让【不支持】代理的网络软件，通过代理进行联网（不同平台的 N 种方法）](https://program-think.blogspot.com/2019/04/Proxy-Tricks.html)》

