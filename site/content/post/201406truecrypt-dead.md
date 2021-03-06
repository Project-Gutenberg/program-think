---
layout: default
title: '分析一下 TrueCrypt 之死&#65288;自杀 or 他杀&#65311;&#65289;&#8212;&#8212;兼谈应对措施'
date: None
author:
    display_name: 
---

　　前几天（5月28日），TrueCrypt 官网突然变脸。全球的安全社区纷纷表示震惊。已经有若干读者在博客留言，希望俺点评一下此事。因为上周恰逢“六四事件”25周年，俺发了[相关博文](https://program-think.blogspot.com/2014/06/weekly-share-68.html)表示纪念。相应地，TrueCrypt 的点评放到本周发布。  
　　先简单说一下 TC 官网的变脸。

　　首先是官网的域名 `truecrypt.org` 自动转向到 `truecrypt.sourceforge.net`。官网的页面上用醒目的红字警告说：TrueCrypt 已经不安全，**TC 项目已经停止开发**。然后建议 Windows 用户迁移到微软的 BitLocker。并给出图文并茂的教程，教你如何一步步迁移到 BitLocker 上。

　　官网给出的理由是：Windows 从 Vista 开始，已经集成了磁盘加密（也就是 BitLocker），而 Windows XP 已经在今年3月份停止支持。所以 TC 团队就不再维护这款产品了。 　　在变脸的同时，官网上发布了最新的 TC 版本（v7.2）。该版本是被阉割过的，只能用来【打开】加密卷，不能用来【创建】加密卷。官网上说：这个 7.2 版本是提供给大家进行数据迁移的。 　　要了解此事的来龙去脉，有必要先作一下 TrueCrypt 的背景介绍。 　　TC 是目前影响力最大的（没有之一）的磁盘加密工具，同时支持 Windows、Linux 和 Mac OS X 三大操作系统。

　　TC 开放了源代码，但它与其它开源软件的不同之处在于：它没有采用那些常见的 License（比如 GPL、BSD、MPL 之类）。它用的是 TC 开发团队自己定的 TrueCrypt License。而且，这个“TrueCrypt License”并没有完全符合 OSI（[Open Source Initiative](https://en.wikipedia.org/wiki/Open_Source_Initiative)）的规范。因此，严格来讲，TC【不】能称之为“开源软件”，只能称之为“公开了源代码的软件”。

　　这款软件诞生于2004年，截止俺写本文时，已经10年有余。

　　关于的更多介绍，可以看俺3年前的教程《[TrueCrypt——文件加密的法宝](https://program-think.blogspot.com/2011/05/recommend-truecrypt.html)》。

　　从 TC 诞生至今，外界一直不晓得它的开发团队是哪些人，甚至连开发团队有几人，都不晓得。 　　不过捏，像 TC 这种类型的项目，团队保持匿名是很正常的。说个小故事：

> 当年的 PGP 之父（Phil Zimmermann）因为发明了 PGP 这款文件/邮件加密工具，差点被美国政府抓去坐牢。当时（上世纪90年代初）的美国法律规定，“高强度加密技术”属于军用技术，不允许出口到海外。据说 Phil Zimmermann 后来想了个妙计——通过 MIT 出版社出了一本书，把 PGP 的全部源代码放到书中，然后援引“美国宪法第一修正案”（出版物受“言论自由”的保护），才推翻了对他的指控。

　　由于开发团队的神秘性，N年前就有人怀疑，TC 是 NSA（美国国安局）或者 CIA（美国中情局）制作的，并且预留了后门。但是这种说法仅仅是猜测，没有人给出证据来证明“TC 有后门”；同样也没有人给出证据来证明“TC 没有后门”。

　　去年斯诺登引爆了 NSA 的棱镜门丑闻。斯诺登曝光的 NSA 绝密材料中【**没有**】提及 TC 存在后门。

  
　　而且，斯诺登本人就是用 TC 来进行磁盘加密。他还曾经在一次“加密派对”（Crypto Party）上作了 TC 的主题演讲（参见[《连线》杂志的这篇报道](https://www.wired.com/2014/05/snowden-cryptoparty/)）。  
　　棱镜门丑闻曝光之后，某些安全社区的大牛开始担心 TC 的可靠性。于是在去年， Kenneth White 和 Matthew Green 发起了一个项目——专门针对 TC 的代码审计（所谓的“代码审计”就是找来一批资深的开发人员，仔细审查 TC 的全部源代码）。该项目的官网在“[这里](http://istruecryptauditedyet.com/)”。2个月前（2014-04-14），该项目完成了第一阶段的审计，【**没有发现**】明显的后门，只发现了几个小的瑕疵——比如密码迭代的轮数不是足够大（但也不是太小）。目前，该审计项目开始进行第二阶段的代码审查，大概需要几个月时间。  
　　从上述这几点可以看出——TC 至少【**没有明显的**】后门。 　　下面俺大致列举一下关于此事的几种解释（大都是网上流传的，少数是俺自己设想的）。这几种解释中，有的提及 NSA。俺注明一下，此处的 NSA 是“泛指”。既可能是 NSA，也可能是 CIA 之类的美国政府机构，甚至可能是其它国家政府。  
　　这个解释也就是[TC 官网](http://truecrypt.sourceforge.net/)给出的解释——Windows XP 已经停止支持，而 Vista 之后的 Windows 都内置了磁盘加密工具，所以 TC 团队就停止开发了。  
　　这个解释说的是——TC 的团队已经懈怠了。关于该介绍的出处，可以参考“[这里](https://it.slashdot.org/comments.pl?sid=5212985&cid=47115785)”。 　　此解释依据是——最近几年，TC 的版本发布周期变得很长（很久没有加入新功能）。另外，TC 的 Boot扇区代码（用于全盘加密）从 5.0 版本之后就没有变过（可能是没有人维护该代码了）。 　　这个解释说的是——TC 就是 NSA 的蜜罐。 　　此解释的理由是：去年开始，安全社区发起针对 TC 的代码审计（刚才说过）。NSA 觉得这个蜜罐迟早会被曝光，于是决定终止 TC 的开发。 　　这个解释说的是——整个事件只是 TC 开发团队的恶作剧。 　　这个说法没有任何理由和依据，纯属 YY。 　　这个解释说的是——TC 的官网被黑客入侵，然后入侵的黑客导演了这出戏。

　　这个说法的依据是：今年4月份，OpenSSL 发生了非常严重的 Heartbleed 漏洞（[俺4月份的博文](https://program-think.blogspot.com/2014/04/openssl-heartbleed.html)提到过此事）。该漏洞会导致网站服务器的内存被攻击者窃取。严重的话，攻击者可以拿到服务器上的重要信息（甚至包括 SSL 私钥）。

　　所以，有人猜测：某黑客利用了 Heartbleed 入侵了 TC 的官网，然后制造了此次“变脸事件”。 　　这个解释类似前一个，说的是 TC 官网被 NSA 入侵。 　　这个说法的依据如下： 依据之一： 如果普通黑客可以利用 Heartbleed 入侵 TC 官网，那么 NSA 这么牛逼的机构，当然也可以入侵它。 依据之二： TC 长期以来一直是 NSA 的眼中钉，NSA 自然有充足的动机和热情去干这事儿。 　　关于这个解释，先讲一个故事：

> 　　斯诺登当年用的两个工具：磁盘加密用的是 TrueCrypt，电子邮件用的是 [Lavabit](https://en.wikipedia.org/wiki/Lavabit)。Lavabit 是专门针对安全性要求较高的网民，所有往来的电子邮件内容都经过加密。斯诺登逃亡之后，美国联邦特工找到 Lavabit 的创始人 Ladar Levison，要求他交出 SSL 私钥。Ladar Levison 提起法律诉讼，被驳回。诉讼被驳回之后，他如果再不交出密钥，会被逮捕。 　　于是他先用最小号的字体，把密钥打印在小纸条上，交给联邦特工（这么干是为了拖延时间）；然后他把整个网站关闭（同时也断了自己的财路）。据传闻：他还把服务器的硬盘进行了物理粉碎，以防止联邦特工利用密钥解密用户的邮件内容。 　　从这个故事可以看出：Ladar Levison 跟斯诺登一样，是坚定的自由斗士，向他致敬。
> 
> 　　再顺便感叹一下：咱们天朝的商业公司——朝廷的走狗还没找上门，自己就主动凑上去舔菊了。同样是商业公司，差距咋就这么大捏？

　　如果结合 Lavabit 的故事，那么很容易就可以联想到——TrueCrypt 团队或许也是被胁迫，所以终止项目。 　　按照这个解释，整件事的发展过程【可能是】这样的： 一：NSA 利用4月份的 Heartbleed 漏洞入侵 TC 官网，然后通过官网服务器上的某些信息，定位到了 TC 开发团队的身份，并且发现团队成员是美国人； 二：NSA 直接找上门，向他们施加压力，要求团队在 TC 中植入后门； 三：TC 团队没法跟 NSA 抗衡，但是又不想植入后门，于是宣布项目终止。 　　这个解释说的是——TC 团队中出现内鬼，这个内鬼劫持了官网控制权，然后发布“项目终止”的声明。 　　这个解释说的是——TC 团队与微软达成幕后交易。微软给团队一笔钱，团队把 TC 项目终止，然后推荐用户迁移到微软的 BitLocker 加密工具。 　　上述这几种解释，每一种都有“破绽”——要么无法自圆其说，要么太牵强。下面俺点评一下每种解释。 　　官方说法的破绽很多。 破绽之一： 前面背景介绍中说了——TC 本身是跨平台的工具。而官网上的解释只是针对 Windows 操作系统。就算官网的解释能成立，那 TC 团队还可以继续维护 Linux 平台或 Mac OS 平台的 TC，没必要把整个项目终止。 破绽之二： 就算是微软已经在 Vista 之后的 Windows 中整合了 BitLocker，TC 作为最有影响力的磁盘加密工具，也未必会输给 BitLocker。BitLocker 的缺点很多——既不开源，又无法跨平台。 破绽之三：

除了 TC，还有其它开源的，面向 Windows 的磁盘加密工具（比如 [DiskCryptor](https://en.wikipedia.org/wiki/DiskCryptor)）。这些磁盘加密工具的名气不如 TC，用户数不如 TC，他们都还在继续开发。和他们一对比，TC 团队的理由就更加显得牵强。

　　这个解释稍微靠谱一些（至少比“解释1”靠谱）。 　　此说法的破绽在于——如果 TC 团队的成员真的懈怠了，他们可以把整个项目移交给开源界的其它安全社区，让其它安全社区继续维护/发展该项目。这样至少是更负责任的做法——照顾了现有 TC 用户的利益。 　　前面说了：TC 是全球最有影响力的磁盘加密工具，其历史已经超过10年。也就是说，TC 的开发团队不是一般的毛头小子，而是很资深的开发人员。作为资深的开发人员，没理由搞出这么鲁莽的举措。 　　这个说法也非常不靠谱。不靠谱的理由如下： 理由之一： 如果 TC 早已是 NSA 的蜜罐。在这种情况下，NSA 的首要任务就是让 TC 继续被更多人使用——这样政府才能够继续偷窥更多人的隐私。而 TC 官网的这次变脸，直接引发了全球安全界的种种猜疑，也导致了 TC 用户的锐减。如果 TC 真的是蜜罐，如今的局面对蜜罐的幕后操纵者是非常不利滴。 理由之二： 斯诺登曝光了 NSA 的大量机密，甚至包括 NSA 在全球顶尖的安全公司 RSA 的产品中植入后门（关于“随机数生成器”）。从最近一年美国媒体的报道来看，斯诺登爆料还是很彻底的。但是斯诺登的爆料中，压根儿没提及 TrueCrypt。而且前面俺也说了，斯诺登自己用的就是 TC 来进行加密。 　　所以，在 TC 官网变脸之前，TC 不太可能是政府的蜜罐。 　　此次 TC 官网变脸，引发了用户的猜忌，很多用户开始改用其它加密工具。 　　前面说了：TC 团队维护这个项目已经超过10年。把一个项目从默默无闻发展到全球知名，是很不容易滴。TC 团队的成员不可能如此愚蠢地砸自己招牌。 　　这个解释比前面几个稍微靠谱一些，但是依然有个破绽。 　　由于今年4月份，OpenSSL 发生了非常严重的 Heartbleed 漏洞。从理论上讲，某个攻击者可以利用该漏洞来侵入 TC 的官网，并获得官网的控制权。一旦获得控制权，自然可以让官网变脸。

　　但是，和此次官网变脸相配合的是，官网上提供了最新的 7.2 版本（前面提到的“阉割版”）。稍微了解 TC 的同学应该知道，TC 的 EXE 安装包和安装出来的“EXE 文件、SYS文件”都是自带数字签名的（啥是“数字签名”，可以参见俺之前的教程《[扫盲文件完整性校验——关于散列值和数字签名](https://program-think.blogspot.com/2013/02/file-integrity-check.html)》）。

　　官网变脸之后，立马就有热心网友对比了 7.2 版本和之前的 7.0、7.1 版本。经过对比，发现几个版本使用的是同一个私钥进行签名。 　　那么，入侵的黑客有没有可能拿到签名用的私钥捏？俺觉得不太可能，理由如下： 　　对安装包进行签名的私钥，跟网站 HTTPS/SSL 的私钥不是一回事。网站的 SSL 私钥通常必须跟 Web Server 部署在同一台服务器。而对文件进行数字签名的私钥，没必要放在 Web 服务器上。俺相信 TC 团队的人，安全素质肯定不差。以他们的安全素质，应该会把签名用的私钥【离线保存】。一旦使用“离线保存”的方案，即使整个网站被别人控制了，入侵者依然拿不到签名用的私钥。 　　基于前一个段落所说的理由，也不太可能是被 NSA 入侵。 　　这个解释是所有的解释里面，破绽最少，说服力最强的，可以解释大部分的“诡异之处”。 　　但这个解释依然有缺陷。主要缺陷就是——如果 TC 团队是受到 NSA 胁迫，所以才选择让项目自杀。那为啥要在官网界面上强力推荐微软的 BitLocker，而且还给出图文并茂的迁移教程。好像没有这个必要嘛。 　　有读者在本文的留言中猜测，是 NSA 迫使 TC 团队在官网上推荐 BitLocker。 　　俺个人认为这种可能性不大。假设 NSA 能迫使 TC 团队这么干。那么 NSA 已经接近于“完全控制 TC 团队”了。如果这是这样，那么对 NSA 最有利的局面应该是“悄无声息”。这样用户才会继续用 TC，NSA 才有利可图（参见对“解释3”的分析）。如今 TC 官网大变脸，足以说明 NSA 没有完全控制 TC 团队。 　　这个解释类似于“解释3——蜜罐”，也很不靠谱。 　　如果 TC 团队真的混入了政府的内鬼，那么根据俺对“解释3”的分析。这个内鬼应该悄无声息地在代码中植入后门，这样效果才最好。为啥这个内鬼要劫持整个官网，搞出这么大的动静？这不符合政府安插内鬼的动机和利益。 　　这个版本也能解释某些诡异之处。主要的破绽在于：像 TC 这种全球影响力的团队，如果他们真的缺钱，首先应该是在官网上发出募捐的呼吁（前2年维基百科资金短缺，就在官网上挂出募捐的横幅）。 　　另外，像微软这么大的公司，如果搞这种幕后交易，一旦穿帮，得不偿失。所以俺觉得微软也不太可能为了一点点眼球效应，去冒这种风险。  
  
　　**首先，不要慌，不要自乱阵脚。** 　　前面俺分析过，TC 在全球有这么大的用户群，这么大的影响力，这么好的口碑。所以俺猜测：TC 要么确实没有后门，要么是隐藏极深的后门（高级后门）。 　　如果是前者，大伙儿当然是高枕无忧；如果是后者，问题也不大。因为这种隐藏极深的高级后门，通常都是用来对付“高价值目标”滴。啥是“高价值目标”捏？比如说：政府的高级官员、军事系统的重要人员、顶级恐怖组织的重要人员、顶级犯罪组织的重要人员...... 　　俺博客的读者，99.99% 以上都【不是】“高价值目标”。所以你暂时不用太担心“高级后门”的问题。 　　接下来需要关注的几点是： 1. 针对 TC 的第二阶段代码审查（几个月之后出报告） 2. 最近这段时间可能还会曝出其它猛料，大伙儿稍微留意一下。 　　退一步讲，假设第二阶段的代码审查发现严重的后门，到时候俺会再发一篇教程，介绍“TrueCrypt 的替代品”。

　　**补充说明**

  
　　本文发出之后又过了一年（2015年4月），TrueCrypt 的代码审计结果出来了。参见【安全大牛 Bruce Schneier】的博客，链接在“[这里](https://www.schneier.com/blog/archives/2015/04/truecrypt_secur.html)”。 　　Bruce Schneier 在开篇写道：

> The security audit of the TrueCrypt code has been [completed](https://opencryptoaudit.org/reports/TrueCrypt_Phase_II_NCC_OCAP_final.pdf) (see [here](https://opencryptoaudit.org/reports/iSec_Final_Open_Crypto_Audit_Project_TrueCrypt_Security_Assessment.pdf) for the first phase of the audit), and the [results](http://arstechnica.com/security/2015/04/truecrypt-security-audit-is-good-news-so-why-all-the-glum-faces/) [are](http://www.theregister.co.uk/2015/04/02/truecrypt_security_audit/) [good](http://betanews.com/2015/04/03/truecrypt-doesnt-contain-nsa-backdoors/). Some issues were found, but nothing major.

  
　　如果你已经是 TC 的用户，在“第二阶段代码审查”结束之前，你还是继续用 TC 吧，不要急着迁移。 　　俺建议：【不要】用官网提供的那个 7.2 版本。因为此事很诡异，那个 7.2 版本会不会有啥猫腻，不得不防。最好是用【前一个】稳定发布版本——也就是【7.1a】版本。

　　由于 TC 的官网已经把老版本的下载链接撤掉了。想下载的同学，可以到 [https://truecrypt.ch/downloads/](https://truecrypt.ch/downloads/)，上面有各种平台的 7.1a 安装包和文档。

  
　　为了保险起见，俺附上 7.1a 版本的各种哈希散列校验值（参见“[这个页面](https://defuse.ca/truecrypt-7.1a-hashes.htm)”）。下载之后，记得再验证一下 HASH 校验值。  
　　不懂得验证 HASH 值的同学，请看俺之前的教程《[扫盲文件完整性校验——关于散列值和数字签名](https://program-think.blogspot.com/2013/02/file-integrity-check.html)》 　　这次官网提供的“7.2版本”是阉割版。换句话说，TC 的官网已经自绝后路了。俺个人感觉：TC 不太可能再“复活”了。但是依然有可能“重生/涅磐”。 　　因为 TC 的源代码是公开滴，任何人都可以拿它的代码克隆出一个新的磁盘加密工具。所以官网变脸之后，已经陆续出现了几个克隆（代码 fork）。假以时日，或许其中的某个克隆会再次成为主流。如果真这样的话，TC 就涅磐重生了。 　　提醒一下：如果你对安全性的要求比较高，短期内（至少1年之内）不要急着去用这些克隆的 TrueCrypt（这些克隆需要一定的时间才能成熟、稳定）。

　　**补充说明**

　　本文发布后，又过了一年（2015），俺写了篇教程（如下)，向大伙儿隆重推荐【VeraCrypt】。TrueCrypt 果然涅磐重生了 :)

《[扫盲 VeraCrypt——跨平台的 TrueCrypt 替代品](https://program-think.blogspot.com/2015/10/VeraCrypt.html)》

　　顺便附上各大网站对此事的点评和讨论（都是洋文）：

[Hacker News 上的讨论](https://news.ycombinator.com/item?id=7814725)

  
Reddit 上的讨论（[这里](https://www.reddit.com/r/technology/comments/26qbo5/truecrypt_is_not_secure_official_sourceforge_page/) ＆ [这里](https://www.reddit.com/r/netsec/comments/26pz9b/truecrypt_development_has_ended_052814/)）  
[Twitter 上的讨论](https://twitter.com/stevebarnhart/status/472193800874758144)  
[StackExchange 上的评论](https://security.stackexchange.com/questions/58940/is-truecrypt-not-secure-now-and-should-i-stop-using-it)  
[Slashdot 上的留言](https://it.slashdot.org/story/14/05/28/2126249/truecrypt-website-says-to-switch-to-bitlocker)  
[安全大牛 Bruce Schneier 的表态](https://www.schneier.com/blog/archives/2014/05/truecrypt_wtf.html)

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[如何用“磁盘加密”对抗警方的【取证软件】和【刑讯逼供】，兼谈数据删除技巧](https://program-think.blogspot.com/2019/02/Use-Disk-Encryption-Anti-Computer-Forensics.html)》  
《[TrueCrypt 使用经验](https://program-think.blogspot.com/2011/05/recommend-truecrypt.html#index)》（系列）  
《[扫盲 VeraCrypt——跨平台的 TrueCrypt 替代品](https://program-think.blogspot.com/2015/10/VeraCrypt.html)》  
《[扫盲 dm-crypt——多功能 Linux 磁盘加密工具（兼容 TrueCrypt 和 VeraCrypt）](https://program-think.blogspot.com/2015/10/dm-crypt-cryptsetup.html)》  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》（系列）  
《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》（系列）  
《[中美政府信息监控的差异——“棱镜门”丑闻随想](https://program-think.blogspot.com/2013/06/usa-vs-china.html)》  
《[每周转载：关于“棱镜门”丑闻的相关报道](https://program-think.blogspot.com/2013/06/weekly-share-54.html)》  
《[对 OpenSSL 高危漏洞 Heartbleed 的感慨、分析和建议](https://program-think.blogspot.com/2014/04/openssl-heartbleed.html)》

