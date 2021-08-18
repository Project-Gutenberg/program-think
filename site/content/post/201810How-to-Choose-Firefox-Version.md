---
layout: default
title: '基于安全性考虑&#65292;如何选择及切换 Firefox 版本&#65311;'
date: None
author:
    display_name: 
---

　　今天这篇，可以视作《[弃用 Chrome 改用 Firefox 的几点理由](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)》一文的后续和补充。  
　　为了避免歧义，也防止有人来抬杠，俺先界定一下： 　　本文以下内容提及的【安全性】，主要包括：“安全加固”和“隐私保护”，另外也会顺便谈到“隐匿性”。 　　有一句话，俺唠叨了很多年（今天再唠叨一次）：

**如果你很在意安全性，就【不要】基于移动设备（手机、平板）进行各种【敏感操作】**

　　具体的原因，可以参见俺之前写的三个系列：

《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》

  
《[如何防止黑客入侵](https://program-think.blogspot.com/2010/06/howto-prevent-hacker-attack-0.html)》  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》 　　有鉴于此，你应该把【所有的】敏感操作都放到桌面系统中进行。而本文也只讨论：【桌面环境】中如何选择 Firefox。  
　　对于天朝的读者而言，你首先要搞清楚：“国际版”与“中国版”是【完全不同】滴！ 　　“国际版”——由 Mozilla 官方开发并维护，面向【全球用户】。

　　“中国版”——由“[谋智中国](https://zh.wikipedia.org/wiki/%E8%B0%8B%E6%99%BA%E7%BD%91%E7%BB%9C)”在“国际版”的基础上进行定制（二次开发），面向【墙内用户】。

　　虽然这个“谋智公司”是 Mozilla 下属的公司，但由于它是在咱们天朝运营滴，多多少少会沾染上一些【中国特色】（说难听点叫“流氓习气”）。据俺所知，“谋智中国”搞过好几次不光彩的破事儿。比如下面这个新闻曝光了“中国版 Firefox 擅自篡改用户设定的书签”：

　　《[谋智中国被发现 “do some evil” @ solidot](https://www.solidot.org/story?sid=37355)》

　　关于这两个版本的差异，俺再随便聊几点：

　　**数据同步的差异**

　　“国际版”使用的是 Mozilla 官方的服务器；而“中国版”使用的是【国内服务器】。 　　“服务器放在国内”意味着什么，大伙儿心知肚明。

　　**插件与扩展的差异**

　　“中国版”内置了一些恶心的东西（比如“支付宝控件”之类的东西）。

　　**搜索引擎的差异**

　　“国际版”内置的搜索引擎是“Google、Bing、duckduckgo、Wikipedia”这些。 　　“中国版”内置的搜索引擎是“百度”这种非常人渣的公司。  
　　**下载 Firefox 的时候，要看清楚网站的【域名】**——  
如果域名是以【`firefox.com.cn`】结尾，那就是【流氓的】“谋智中国”网站；  
而 Mozilla 官网的域名，是以【`mozilla.org`】结尾滴。 　　注：聊完“中国版”的话题之后。本文后续部分的讨论，全都是针对【国际版】。 　　根据 Firefox 的开发流程，每个版本会经历如下几个阶段：

　　**Nightly（每夜构建阶段）**

　　在这个阶段，每天晚上会编译一个版本，包含当天加入的新代码（Nightly 由此得名）。

　　**Beta（β 测试阶段）**

　　在软件工程中，“β 测试”指的是——把软件提供给外部真实用户进行【试用】，以此来发现一些开发环境中未能发现的 bug。 　　那么，这些用于外部测试的 Beta 版本是从哪里来的捏？实际上是从 Nightly 版本中筛选出内部测试比较 OK 的，然后作为 Beta。 　　对这个阶段的版本，Mozilla 的软件工程师只进行 bug 修复，【不会】增加新功能。 　　如今，“Beta 版本”也被称做“开发者版本”（洋文叫“Developer Edition”）。 　　注： 　　历史上曾经有过一个叫“Aurora”的阶段（位于 Nightly 与 Beta 之间）。当时的“开发者版本”指的是 Aurora。从“54版本”之后，为了简化开发周期，这个 Aurora 就废除了。所以“54版本”之后，“Developer Edition”就是指 Beta。

　　**Release（发布阶段）**

　　经历了“β 测试”之后，就正式发布。 　　那么，这些用于发布的 Release 版本是从哪里来的捏？实际上是从 Beta 版本中挑选出外部测试比较 OK 的，然后用作发布。 　　对这个阶段的版本，Mozilla 的软件工程师只进行“大 bug”（关键 bug）的修复工作。对“小 bug”，会留到下一个版本。 　　Release 的版本号规则如下： 　　（截止俺写本文时）最新版本是【63.0】——这是刚发布时的版本号。 　　过了一段时间后，如果修复了一些关键 bug，会再出一个版本叫【63.0.1】，然后再下一个是【63.0.2】，以此类推...

　　**举例：**

　　在俺写这篇博文时，Firefox 的几个版本处于如下状态：

65

64

63

62

　　Nightly　　

　　Beta　　

　　Release　　

 

 

　　Nightly　　

　　Beta　　

　　Release　　

　　你可以通过如下几个链接，查看并下载 Firefox 历史上的【所有版本】。

[https://archive.mozilla.org/pub/firefox/releases/](https://archive.mozilla.org/pub/firefox/releases/)

  
[https://ftp.mozilla.org/pub/firefox/releases/](https://ftp.mozilla.org/pub/firefox/releases/) 　　如果你熟悉 Web 相关技术的话，还可以通过如下链接，查看历史上【每一个版本】的技术性发布说明（相当于写给程序猿看的 Release Notes）：

[https://developer.mozilla.org/docs/Mozilla/Firefox/Releases](https://developer.mozilla.org/docs/Mozilla/Firefox/Releases)

　　Firefox 的版本迭代周期大约是6~7星期。当下一个版本进入 Release 阶段，之前那个版本就不再维护了（不再修复 bug）。 　　但是为了照顾到【企业用户】，Mozilla 还搞了一个【长期支持版本】（洋文叫“Extended Support Release”，缩写为 ESR）。 　　每隔7到8个版本，就有一个版本被选作 ESR 版本。ESR 的维护周期比较长（一年左右）。只有当下一个 ESR 版本出现之后，才会结束对上一个 ESR 版本的维护。 　　下面是最新的 ESR 版本下载页面（包含：不同平台，多个语种）：

[https://www.mozilla.org/firefox/organizations/all/](https://www.mozilla.org/firefox/organizations/all/)

　　如果你理解了 Firefox 的开发流程和发布规则，自然也就理解了——为啥【不应该】使用“Nightly”和“Beta”。 　　因为这两个版本的质量【尚未】达到“可发布”的水平，会有比较多的 bug。有些 bug 可能会是【安全漏洞】。 　　如果你关注安全性，当然不应该用这两个版本。 　　对于 Firefox，每个新版本都会引入一些【新功能】。要增加新功能，就要增加软件代码（source code），也就增加了攻击面，也就【有可能】出现新的安全漏洞。 　　由于“普通 release”的维护周期比较短（6~7星期），过了这个时间段之后就变成【旧版本】，即使发现 bug 也不会再修复了。 　　相比之下，ESR 的好处就很明显。ESR 维护的时间长达一年左右，而且 ESR 是【只修复 bug，不增加新功能】。所以在 ESR 的维护周期内，它的代码质量会【越来越好】。 　　前面介绍了“普通发布版”的版本号规则。再来说一下 ESR 的版本号规则。 　　（俺敢说：即使是 Firefox 的发烧友，也不一定清楚 ESR 版本号的规则） 　　为了简明起见，俺以【52】这个 ESR 版本来举例。（因为 52 ESR 已经走完它的生命周期）。

时间

ESR  
版本号

普通发布  
版本号

备注

2017-03-07

52.0

52.0

ESR 与普通版同步发布

2017-03-17

52.0.1

52.0.1

同步修复 bug

2017-03-28

52.0.2

52.0.2

同步修复 bug

2017-04-19

52.1.0

53.0

52 结束，53 发布  
ESR 版本号跳到 52.1.0

2017-04-27

52.1.1

53.0.1

修复若干 bug，含 52 版本的【旧】bug

2017-05-05

52.1.2

53.0.2

修复若干 bug，含 52 版本的【旧】bug

2017-05-19

N/A

53.0.3

修复若干 53 版本的【新】bug  
由于【不含】52 版本的 bug，ESR 版本不变

2017-06-13

52.2.0

54.0

53 结束，54 发布  
ESR 版本号跳到 52.2.0

2017-06-29

52.2.1

54.0.1

修复若干 bug，含 52 版本的【旧】bug

2017-08-08

52.3.0

55.0

54 结束，55 发布  
ESR 版本号跳到 52.3.0

2017-08-10

N/A

55.0.1

修复若干 53 或 54 版本的【新】bug  
由于【不含】52 版本的 bug，ESR 版本不变

2017-08-16

N/A

55.0.2

修复若干 53 或 54 版本的【新】bug  
由于【不含】52 版本的 bug，ESR 版本不变

2017-08-25

N/A

55.0.3

修复若干 53 或 54 版本的【新】bug  
由于【不含】52 版本的 bug，ESR 版本不变

  
　　在聊这个话题之前，先简单说一下：“Bug 递减模型”。 　　对于正规的软件开发流程，在【正式发布】之后，就只是修复 bug，而不会再加新功能（要加也是加到下一个版本）。 　　在这种情况下，bug 通常是一个【递减】的过程（极少数情况会出现递增，这不在本文讨论之列）。而且这个“递减过程”并不是【匀速】的，而是一个【先快后慢】的过程（如果画一条“bug 数变化曲线”，其形状有点类似于倒数函数那样）。 　　为啥 bug 的递减过程是【先快后慢】捏？道理很简单—— 软件在刚刚发布时，会被大量使用（“实际用户数”远远多于软件公司的“测试人员数”）。所以，在刚发布的初始阶段，会有比较多的 bug 暴露出来。 但是随着时间的推移，容易发现的 bug 都已经被发现了，剩下的都是比较隐蔽的 bug（比较难发现）。所以 bug 递减的趋势会变慢。 　　为了增加说服力，俺稍微整理了一下 52 ESR 生命周期内的 bug 修复情况： （简洁起见，只列出那些修复了【高危安全漏洞】的 52 ESR 版本）。

时间

ESR  
版本号

CRITICAL 级别  
bug 数

HIGH 级别  
bug 数

2017-03-07

52.0

N/A

N/A

2017-03-17

52.0.1

2

0

2017-04-19

52.1.0

9

20

2017-04-27

52.1.1

0

2

2017-06-13

52.2.0

2

3

2017-08-08

52.3.0

4

10

2017-09-28

52.4.0

2

5

2017-11-14

52.5.0

3

1

2017-12-07

52.5.2

2

1

2018-01-23

52.6.0

3

8

2018-03-13

52.7.0

3

3

2018-03-16

52.7.2

3

0

2018-03-26

52.7.3

0

2

2018-05-09

52.8.0

2

5

2018-06-06

52.8.1

1

1

2018-06-26

52.9.0

3

4

　　（注：上表数据是从 Mozilla 官网的“[这个链接](https://www.mozilla.org/security/known-vulnerabilities/firefox-esr/)”整理的）

  
　　花了这么多口水来描述“bug 递减模型”。俺无非是想得出一个结论——**软件刚发布的时候，先不要急着用，稍等片刻再说。** 　　俺所说“片刻”是多长捏？取决于具体的“软件类型”和“用户群体”。对于 Firefox 的 ESR 而言，俺建议【至少】等一两个月。 　　以 52 ESR 为例： 　　当该版本刚发布时，先别用。等到 54（甚至 55）发布的时候，你再开始用 52 ESR。 　　说完了“滞后升级策略”，再来说说该策略的例外情况。 　　刚才说的是“滞后升级”的策略。但存在一种【例外情况】，需要你【立即】升级—— 如果前一个 ESR 结束维护之后，又发现了一个新的高危漏洞（该漏洞对你有显著影响，并且无法通过“配置项”进行规避）。在这种情况下，前一个 ESR（由于维护已结束）不会再修复了，那么你就应该立即升级到下一个 ESR。 　　刚才提到“通过配置项规避高危漏洞”，估计很多同学不明所以，俺简单解释一下。

　　Firefox 提供了很丰富、很全面的配置选项（Preference）。可以通过它，对 Firefox 进行【全方位】定制——这其中也包括“【禁用】某些功能模块”。这方面的介绍参见博文：《[扫盲 Firefox 定制——从“user.js”到“omni.ja”](https://program-think.blogspot.com/2019/07/Customize-Firefox.html)》

  
　　如果某个高危漏洞所在的模块，可以通过配置项禁用之；那么你就【不需要】升级 ESR 版本，只需通过“`about:config` 界面”或“`user.js` 文件”禁用这个有问题的模块。 　　根据俺的观察，相当比例的 Firefox 高危漏洞，对俺的 Firefox【毫无影响】。因为漏洞所在的模块，老早就已经被俺禁用了。 　　以俺的习惯，凡是“用不到”或“很少用”的功能，统统禁掉。套用信息安全的行话，叫做【降低攻击面】。 　　如果你很在意安全性，上网的时候应该【全程加密】（这又是俺唠叨了很多年的老话题）。 　　“全程加密”的好处【至少】包括： 1. 防止上网流量被嗅探（被第三方偷窥） 2. 防止上网流量被劫持（被第三方篡改） 　　上述所说【第三方】是指谁捏？稍微解释一下： 如果你通过公司的网络上网，“第三方”可能是你公司的网管； 如果你通过公共场合（比如：餐厅、酒吧）的 wifi 热点上网，“第三方”可能是 wifi 热点的管理员； 另外，不管你通过哪一种方式上网，电信运营商（ISP）都是潜在的“第三方”。  
　　如果你很在意安全性，光搞“全程加密”是【不够】滴！还需要更进一步，做到【全程走匿名网络】。 　　为啥捏？简单举2个例子：

　　**举例1——为啥“全程 HTTPS”是不够滴？**

　　假设你访问某个网站，该网站已经实现【全站 HTTPS】。那么你对该网站的访问，就可以算是【全程加密】了。这种情况下，刚才提到的“嗅探”和“劫持”的风险，基本上可以规避掉了。 　　但是（俺要开始说“但是”了），依然存在另外几个风险点： 　　其一， 　　在这种情况下，该网站还是可以看到你的【真实公网 IP】。如果网站把所有访问者的信息记了日志（web log），日后追查起来，还是可以查出，某年某月某日，某个公网 IP 访问了该网站。 　　其二， 　　如果你在公司里面上网，即便你全程 HTTPS；公司的网管虽然无法解密 HTTPS 的流量数据，但还是可以看出——你访问的是【哪个网站】。

　　**举例2——为啥“全程翻墙”是不够滴？**

　　全程走翻墙通道，可以避免“例1”中提到的两个弊端—— 1. 目标网站即便记录了访问者日志（web log），里面包含的公网 IP 也是翻墙服务器的 IP，而【不是】你个人的公网 IP。 2. 公司网管只知道你连接了某个服务器，但不知道你最终访问了哪个网站。 　　但这样依然是【不够】滴！为啥捏？因为翻墙工具的设计初衷是为了“突破 GFW”，而【不是】为了“匿名化”。 　　如果你非常在意“匿名化”（比如：想在网上发表敏感的政治言论），那么你还需要使用专门的【匿名网络】。 　　“匿名网络”，洋文叫做“anonymity network”。顾名思义，是用来帮助你实现【匿名化】的手段之一。通过匿名网络进行各种操作（比如在网上发布言论），可以让【网络层面】的【逆向追溯】变得极端困难。 　　注：很多人把“匿名网络”与“暗网”混为一谈，其实这是两个不同维度的概念。之所以会有这种混淆，是因为几个知名的工具（Tor、I2P）既是“暗网”，也是“匿名网络”。 　　如果你想了解“匿名网络的原理”，可以参见俺的几篇旧博文（里面包含若干示意图）：

《[“如何翻墙”系列：关于 Tor 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)》

  
《[“如何翻墙”系列：简单扫盲 I2P 的使用](https://program-think.blogspot.com/2012/06/gfw-i2p.html)》  

![不见图 请翻墙](https://lh4.googleusercontent.com/UEJSz_vaNCCnJZ0vFEbAM0P2etlEwSFOOC-dDI9_55uIKQElo0ewEUREdbLpGvULyr_ran6G0B8oVh2rJIy4NBaOnL9znEaDeNKh15geLSNe4CVCPlbxhSRY2oYz)

　　名气比较大的“匿名网络”有两个，分别是 Tor 与 I2P。俺个人推荐 Tor。原因至少包括如下：

1\. 在性能方面，I2P【严重不如】Tor——这与协议设计有关（参见“[这张对比图](https://lh3.googleusercontent.com/o-uTSq98Ia1XqkNO58OJ6dOCqnxgSQwKed9PgStwC23PMaDAzllmdS-ArOabeCtsbWY4aB4G3YvqK_V4_qVkAyGKgNljgt7XqHoKLIHluFGADBMo4CQ)”），也与【出口节点】的数量有关。

2\. I2P 客户端更适合用来访问它自己的暗网，而【不】适合用作访问公网的代理；而 Tor 两者都适合。 3. Tor 客户端可以完美地搭配 Firefox 浏览器（参见下面介绍的 Tor Browser） 　　Tor Browser，还有另一个叫法是 TBB（Tor Browser Bundle）。为了打字省力，以下都称之为 TBB。

　　之前没接触过 TBB 的同学，先看另一篇扫盲教程《[“如何翻墙”系列：扫盲 Tor Browser 7.5——关于 meek 插件的配置、优化、原理](https://program-think.blogspot.com/2018/04/gfw-tor-browser-7.5-meek.html)》，熟悉一下。

　　很多人对 TBB 有一个【误解】，以为它只是简单地把“Firefox ESR”与“Tor 客户端”拼凑在一起。其实不然！ 　　Tor 社区发布的 TBB 至少包括如下几项主要工作： 1. 对 Firefox ESR 的修改（代码层面） 2. 基于 Preference 对 Firefox 进行定制（这种定制方式，本文前面的章节已经提到过） 3. 内置了若干安全相关的扩展（比如：NoScript、HTTPS Everywhere ......） 4. 整合 Tor 客户端 　　通过上述这些工作，不光让 Firefox 可以走 Tor 的匿名网络，而且还把 Firefox 本身的“隐私保护”与“安全加固”提升到一个新的高度。

　　说到这里，再次夸奖一下 Tor 社区——在信息安全方面非常成熟且牛逼。比如在[上个月的博文](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)中，俺还提到了 Tor 社区对 Firefox 的很多改进（比如：第一方隔离、防范指纹追踪），已经被 Mozilla 官方接纳，成为 Firefox 的标准功能。

　　在本文的最后部分，聊一个比较阳春白雪的话题——自己组合“ESR 与 Tor”。 　　可能有些读者觉得：既然已经有了 TBB，为啥还要自己折腾“ESR + Tor”？所以俺先来谈一下必要性。 　　如果你是个技术能力和动手能力都比较强的极客，同时对安全性的要求【非常非常高】，那就可以考虑自己折腾一下“ESR + Tor”。这种玩法的好处包括如下：

　　**1\. 实现【更小颗粒度】的隔离**

　　对于使用 TBB 的场景，浏览器（Firefox）与 Tor 客户端运行在【同一个用户环境】中。但“浏览器”的重要性显然要高于“Tor 客户端”。 　　把两个重要程度【不同】的进程放在同一个环境中运行，这本身就违背了安全加固的原则。 　　打个比方： 　　假如某一天，Tor 客户端曝出某个高危的安全漏洞，使得攻击者可以利用该漏洞在本地执行代码；由于浏览器与 Tor 运行在同一个环境，那么攻击者就可以借助此漏洞，攻击浏览器。严重的话，可能导致你的 Web 帐号沦陷。 　　而如果是自己组合 ESR + TOR，就可以把这两者隔离在不同的环境（“不同的操作系统用户”或“不同的虚拟机”或“不同的物理机”）。如此一来，（相比 TBB 而言）安全性提升了一大截。

　　**2\. 满足个性化需求**

　　TBB 是面向大众用户的。很多时候，“大众的需求”与“极客的需求”是不太匹配滴。 　　之所以能够自己折腾 ESR + Tor，得益于——Firefox 本身是【高度可定制】的。

　　比如俺曾经写过一篇博文《[无需任何插件或扩展，定制 Firefox 外观](https://program-think.blogspot.com/2016/10/custom-firefox-theme-without-extension.html)》，介绍“如何折腾 `userChrome.css`”。类似 `userChrome.css` 和 `user.js` 之类的定制，还只是 Firefox 的【高层定制】。

  
　　另外，Firefox 还支持一些【底层定制】，可以实现比【高层定制】更多的效果。举个例子：你可以不安装任何插件或扩展，修改 Firefox【所有的】默认快捷键。具体的玩法参见博文：《[扫盲 Firefox 定制——从“user.js”到“omni.ja”](https://program-think.blogspot.com/2019/07/Customize-Firefox.html)》 　　有些同学可能会问：既然可以用扩展的方式定制快捷键，为啥还要折腾【无扩展方案】？ 　　因为，如果你对安全性的要求非常非常高，每增加一个额外的插件或扩展，都将被视作一个潜在的攻击面。而且你无法验证这些插件或扩展的作者，是否足够靠谱。所以，不用插件或扩展就能搞定的方案，总是让人心情愉悦 :) 　　最后俺还想说的是：

　　虽然折腾一些东西（比如本文所说的“ESR + Tor”）很花时间，但这些时间值得付出。具体原因请看：《[聊聊【折腾】的重要性](https://program-think.blogspot.com/2017/04/The-Importance-of-Zheteng.html)》。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》（系列）  
《[如何防止黑客入侵](https://program-think.blogspot.com/2010/06/howto-prevent-hacker-attack-0.html)》（系列）  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》（系列）  
《[弃用 Chrome 改用 Firefox 的几点理由](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)》  
《[扫盲 Firefox 定制——从“user.js”到“omni.ja”](https://program-think.blogspot.com/2019/07/Customize-Firefox.html)》  
《[“如何翻墙”系列：关于 Tor 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)》  
《[“如何翻墙”系列：扫盲 Tor Browser 7.5——关于 meek 插件的配置、优化、原理](https://program-think.blogspot.com/2018/04/gfw-tor-browser-7.5-meek.html)》  
《[“如何翻墙”系列：简单扫盲 I2P 的使用](https://program-think.blogspot.com/2012/06/gfw-i2p.html)》  
《[无需任何插件或扩展，定制 Firefox 外观](https://program-think.blogspot.com/2016/10/custom-firefox-theme-without-extension.html)》  
《[聊聊【折腾】的重要性](https://program-think.blogspot.com/2017/04/The-Importance-of-Zheteng.html)》

