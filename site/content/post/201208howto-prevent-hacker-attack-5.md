---
layout: default
title: '如何防止黑客入侵[5]&#65306;Web相关的防范&#65288;上&#65289;'
date: None
author:
    display_name: 
---

　　由于俺比较懒，导致本系列已经中断了2年之久。上星期有读者留言，希望俺尽快把本系列补上。再加上昨天看到新闻，说 Java 7 爆出全系列的高危漏洞。凡此种种，促使俺补上了本系列的第5篇，关于 Web 的防范。这部分的内容比较长，为了避免大伙儿阅读疲劳，俺把《Web相关的防范》分为上中下3个部分。  
　　在聊正题之前，先给大伙儿强调一下“Web 安全”的重要性。 　　如今互联网非常普及，大部分的家用电脑和商业电脑，都具备联网功能。而且大部分电脑只要一开机，就处于联网状态。作为电脑的使用者，有相当一部分时间是花在 Web 浏览（俗称网上冲浪）。在这样的环境中，Web 就成了恶意软件（病毒、木马、蠕虫、勒索软件......）最理想的一种传播媒介。据说如今大部分电脑中招，都与 Web 有关。 　　正因为如此，才把 Web 相关的内容，单独汇总一篇。接下来，俺先介绍一下攻击者常见的招数，然后再介绍一下各种应对措施。  
　　所谓的“嗅探”，就是攻击者利用某些技术手段，截获你的网络数据流并进行分析，从而获取某些有价值的信息。通常来说，“嗅探”只是入侵的初始阶段（准备阶段）。攻击者通过“嗅探”获取到的信息，通常用来进行辅助后续的入侵行动。 　　举例： 　　很多人喜欢通过公共场所的 WiFi 热点上网。假如你使用的 WiFi 热点没有设置为强加密。那么，某个攻击者就有可能利用 WiFi 嗅探工具，截获你的上网流量。如果你正好在收发 Web 邮件，而且没有通过 HTTPS 加密（好多国内的 Web 邮箱【不】支持全程 HTTPS 加密）。那么，攻击者就可以看到你的收发的邮件内容。

　　不过捏，关于嗅探的防范，不是本文的重点。因为俺之前写一个系列博文《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》，里面介绍的各种招数（比如加密代理的使用），已经足以帮你对抗“嗅探”了 :)

　　“钓鱼攻击”包括很多种，基于 Web 的网络钓鱼是其中之一。

　　由于“钓鱼攻击”属于[社会工程学](https://program-think.blogspot.com/2009/05/social-engineering-0-overview.html)的范畴，也不是本文的重点。今后有空的话，单独写一篇“关于钓鱼攻击的防范”。

  
　　在[本系列前一个帖子](https://program-think.blogspot.com/2010/08/howto-prevent-hacker-attack-4.html)里，俺已经扫盲了"漏洞"、"补丁"等概念以及相关的一些常识。健忘的同学，可以再去温习一下。 　　在软件行业中，几乎每一款软件都会有漏洞——浏览器自然也不例外。浏览器的漏洞有很多种，其中一类叫做"安全漏洞"。顾名思义，就是会导致安全问题的漏洞。 　　如果某款浏览器的安全漏洞被攻击者发现，而浏览器厂商自己还不知晓。那么攻击者就可以利用该漏洞，发起广泛的攻击。 　　举例： 　　假设某个黑客研究 IE 的内核，首先发现 IE 存在一个“渲染图片导致缓冲区溢出”的漏洞。由于该漏洞是独家发现，只要该黑客不公开漏洞的信息，连微软（也就是 IE 浏览器的厂商）也会蒙在鼓里。因此，也就【没有】针对该漏洞的补丁。那么，这个黑客会如何利用该漏洞捏？ 1. 首先挑选一张图片（为了吸引人，通常会选一张美女图之类的照片），然后精心地嵌入一段攻击代码在图片内部。 2. 把这张图片放到网上（比如张贴到某个大型论坛，再配上一个吸引人的标题）。 3. 过不了多久，就会吸引到很多网友来围观。如果围观的网友用的浏览器不是 IE，那么他仅仅是看到一张美女图而已，不会有啥异样。如果围观的网友用的正好是有漏洞的 IE 版本，当 IE 打开那张图片的瞬间，攻击代码就会被激活（被运行）。然后，攻击代码会悄悄地在这台电脑中安装一个木马（技术行话叫“植入木马”）。之后，这台电脑就成为攻击者的肉鸡了（攻击者可以远程控制肉鸡，为所欲为）。 4. 攻击者控制了肉鸡之后，既可以拿去卖钱（有专门的地下肉鸡交易市场），也可以偷窥机主的隐私（看看有没有网银、裸照、QQ 靓号）。如果控制的肉鸡数量巨大，还可以搞 DDOS 攻击...... 　　如今大部分浏览器上，都安装了插件。最常见的插件就是 Flash 插件。另外还有“PDF 插件、Java 插件”等等。 　　浏览器的插件也属于软件，也会存在安全漏洞，因此也可以被攻击者利用。一般来说，攻击者对插件漏洞的利用，类似于对浏览器漏洞的利用。 　　举例1： 　　2011年，美国大名鼎鼎的安全公司 RSA 遭到入侵并且被深度渗透，连看家产品 SecureID 的密钥也被偷了。

　　攻击者之所以能得手，就是利用了 Flash 插件的一个零日漏洞。洋文好的同学，可以看“[这里](http://blogs.gartner.com/avivah-litan/2011/04/01/rsa-securid-attack-details-unveiled-they-should-have-known-better/)”的详细报道。

　　举例2： 　　同样是在去年，有不少 Gmail 用户遭到入侵。但实际上，Gmail 本身并没有出问题。攻击者是利用 Flash 的漏洞，伪造跨站请求，然后在 Gmail 的转发列表中加入一个攻击者的邮箱。之后，被害人收到的所有邮件，都会自动转发给攻击者。 　　从最近几年的趋势来看，插件漏洞导致的安全问题，要多于浏览器漏洞导致的安全问题。 　　最后再来说说"跨站脚本"的问题。 　　大部分 XSS 攻击，都是利用网站本身的漏洞。所谓的网站，其实就是若干 Web 服务器，上面运行若干软件。前面说了，只要是软件，就可能存在漏洞（包括安全漏洞）。所以，Web 服务器上的软件自然也不例外。 　　基于 XSS 的攻击有很多种类型，具体的技术原理也有所差异。考虑到大部分读者不是搞技术的，俺就不深入展开了。仅举一例，让大伙儿有个感性的认识。 　　举例： 　　比如某个 BBS 论坛存在漏洞——【没有】对用户发布的帖子内容（此处的“内容”，不是指文字的内容，而是指特殊字符）进行严格的检查。如果某个攻击者发现了此漏洞，就可以精心构造一个帖子，在帖子的正文中包含一段攻击脚本（通常是 JavaScript）。接下来，攻击者把这个帖子发布到该论坛上。 　　然后捏，如果有人浏览了这篇帖子，这段攻击脚本就会被激活，然后干坏事...... 　　对于用户来说，浏览器是 Web 的根基。所以，谈 Web 的安全防范，首先得聊一聊如何选择浏览器。 　　挑选浏览器有如下几个指标供参考：

**1\. 浏览器的质量好不好**

评判安全方面的质量，最关键的一条是：看浏览器有没有经常出安全漏洞。

**2\. 浏览器的更新快不快**

  
爆出漏洞后，浏览器的开发团队是否及时出补丁或新版本。在《[安全漏洞的基本防范](https://program-think.blogspot.com/2010/08/howto-prevent-hacker-attack-4.html)》一文，俺介绍了【零日漏洞】的概念。浏览器修补漏洞越及时，网友暴露在“零日漏洞攻击”的时间就越短。  
**3\. 浏览器的功能强不强** 除了要看浏览器本身的功能，还要看其支持的扩展是否丰富。 　　根据上述指标，俺把市面上常见的浏览器，根据靠谱的程度，划分为如下三类： 　　俺个人强烈建议用 Firefox 或 Chrome 进行网上冲浪，因为这两款浏览器很符合上述指标。

**质量好**

本世纪初，浏览器市场被 IE 一统天下。但随着时间推移，IE 在全球的市场份额逐步被 Chrome ＆ Firefox 占去一半以上。这充分说明 Firefox 和 Chrome 的质量很好。另外，在安全漏洞方面，Firefox 和 Chrome 也优于 IE。

**更新快**

说到快速更新（快速迭代），这是 Chrome 的首创。从去年开始，Firefox 也学 Chrome 采用快速版本更新。

**功能强**

说到功能，Firefox 刚出道时，利用丰富的扩展吸引了足够多的用户。如今，无论是扩展的种类还是扩展的下载量，Firefox 是最多的；至于 Chrome，由于出道时间晚，这扩展方面不如 Firefox，但显然比 IE 强多了。 　　除了上述这几条，这两款浏览器还具有如下优点：

**支持的平台很多**

支持三大主流的桌面系统（Windows、Mac OS、Linux），支持两大主流的移动系统（Android、iOS）。

**开源项目**

由于开源而且参与的程序员也多，所以软件中的漏洞容易被及早发现。 （Chromium 是开源滴；Chrome 虽然基于 Chromium，但包含【闭源】模块） 　　以上就是俺推荐 Firefox 和 Chrome 的理由。在本文的后续章节，俺会以这两款浏览器为主，进行介绍。 　　先说 Safari 和 Opera。这两款的出道时间早于 Firefox 和 Chrome。忙活了这么多年，如今的市场份额依然很低，这已经说明某些问题。另外，俺个人觉得 Safari 和 Opera 的扩展和插件不够丰富，更新速度也不够快，所以俺不推荐。 　　至于 IE，曾经是市场份额最大的浏览器，而是集成（捆绑）在 Windows 系统中。为啥俺把它放到第二类捏？有如下几个原因： 1. IE 跟 Windows 集成得太紧密。IE 如果爆漏洞，通常要等微软发布 Windows 补丁来修复。而 Windows 补丁是按月发布的——太不及时啦。 2. 相比 Firefox 和 Chrome，IE 是闭源项目。由于源代码不公开，而且参与的人不够多，导致潜在的漏洞难以被发现。 3. IE 用户大都是菜鸟用户（很多菜鸟只知道用系统内置的浏览器）。由于菜鸟不太懂安全防范，有些【低级】骇客就喜欢盯着这个用户群。 　　说到这儿，可能有同学会问：天朝的好多网银都只能用 IE（很多网银客户端依赖于 IE 的 ActiveX 控件），咋办捏？别担心，在本系列的下一篇《Web相关的防范 (下)》会谈到此问题的解决方法。 　　说到【国产】的浏览器，有必要谈一下浏览器的内核（也就是浏览器的引擎）。绝大部分国产的浏览器，都不是自己开发内核，而是基于老外现成的内核。常见的浏览器内核有三款，分别是： Gecko 内核（来自于 Mozilla 开源组织，主要供 Firefox 使用） Trident 内核（来自于微软，主要供 IE 使用） WebKit 内核（独立的开源项目，Chrome 和 Safari 使用此内核） 　　几款常见的国产浏览器（360浏览器、傲游浏览器、QQ 浏览器），使用的是 Webkit + Trident 的双内核模式。 　　某些国产浏览器把双内核作为吹嘘的亮点。但在安全层面，双内核反而会带来安全问题。假如你手头的国产浏览器采用了 Webkit + Trident 双内核。只要这两款内核中，有一个爆出安全漏洞，你就有可能中招。也就是说：双内核会增加你中招的概率。 　　俺极力反对【国产】浏览器，还有另一个原因——政治层面的安全问题。朝廷为了监控屁民在互联网上的一言一行，会跟国产浏览器厂商合作，通过浏览器记录网民的行踪。 　　举例： 　　前几年腾讯搞的“TT浏览器”，会把用户上网行踪记录在某个文件中。 　　至于 360，名声更是臭不可闻。360 浏览器本身就存在收集用户隐私的问题，居然还好意思自称是“安全浏览器”。而且大伙儿别忘了，奇虎公司跟 GFW 一直保持着暧昧的关系哦。 　　综上所述，俺个人【非常反对】使用国产浏览器。 　　说完浏览器的选择，再来聊聊如何选择插件和扩展。 　　先来扫盲一下插件和扩展的区别（连很多 IT 技术人员都把这两者混为一谈）。所谓的插件，洋文叫“plugin”；所谓的扩展，洋文叫“extension”。两者的区别如下：

　　**插件**

  
　　在功能上，插件通常是用来渲染 HTML 页面中的 `<object>` 或 `<embed>` 标签。 　　插件通常实现比较【底层】的功能，通常以平台相关的代码（本地代码）编写，可以调用操作系统的 API。形式上，插件以动态库（Windows 上就是 DLL 文件）的方式，加载到浏览器的进程内。由于使用本地代码编写，插件通常依赖于特定的操作系统（不同系统的插件不能混用）。 举例： Flash 插件 媒体播放器插件 PDF 插件 Java 插件

　　**扩展**

　　扩展，顾名思义，是用来扩展浏览器自身的功能。所以，扩展可以调用浏览器自身的 API，但是大部分扩展【不能】调用操作系统的 API。 　　一般来说，扩展是跟操作系统无关的。比如 Firefox 的大部分扩展，既可以用于 Windows 平台的 Firefox，也可以用于 Linux 和 Mac 的 Firefox。 举例：

[俺曾经推荐的 GreaseMonkey](https://program-think.blogspot.com/2011/11/greasemonkey-scripts-for-google-reader.html)，就属于扩展。

　　由于插件比较底层，一旦出现高危漏洞（比如能够执行本地代码的漏洞），攻击者就可以在操作系统中植入木马。可以这么说，插件出现漏洞，其危险性类似于浏览器出现漏洞。 　　相对而言，扩展出现漏洞，其危险性往往不如插件严重，通常也不会导致攻击者植入木马。 　　虽然扩展出漏洞导致的危险性不如插件那么高，但也不能掉以轻心。 　　俺的经验是：尽量使用知名度高且评价好的扩展。这样的扩展通常成熟度也比较高——即使出了漏洞，更新也比较及时；这类扩展也会有更多安全研究人员对其进行研——即使有漏洞，也更容易被发现。 　　反之，对于某些很少人用的扩展，最好敬而远之。顺便提一下。某些层次低的入侵者，甚至会把木马伪装成浏览器扩展，再忽悠一个很花哨的功能，然后放到网上给大伙儿用。  
　　从上述对比可知，插件如果出现漏洞，危险性很高。所以，俺的建议是：**尽量避免使用【插件】**。 　　不过捏，避免使用插件，说起来简单，但是做起来有点难度。其它插件，说不用就不用了。但是 Flash 插件，实在是用得太广泛了（视频网站用到它，网页休闲小游戏也用到它），估计大伙儿难以割舍啊。

　　不幸的是，Flash 插件又最危险。一方面是因为 Adobe 的程序猿，安全意识太差；另一方面是因为 Flash 是用得最多的插件，成为攻击者的重点研究对象。根据2011年的统计数字，去年一年，光是【**高危漏洞**】，Flash 就爆了4次——当之无愧地坐上漏洞排行榜的头把交椅。

　　面对 Flash 插件，该咋办捏？列位看官，请听下回分解。（下一篇会尽快发布）

**[回到本系列的目录](https://program-think.blogspot.com/2010/06/howto-prevent-hacker-attack-0.html#index)**

