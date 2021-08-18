---
layout: default
title: '三种主流 RIA 技术之争&#65292;你该如何选型&#65311;'
date: None
author:
    display_name: 
---

　　前几天听说 Adobe 发布了用于 Flash Player 的 RTMP（实时消息协议），在“[这里](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200901/012009RTMP.html)”。乍一看，好像是一个不错的东东。号称有如下优点：支持高性能地把数据（主要是音频、视频）PUSH 给 Flash Player；支持 over HTTP 和 HTTPS。再联想到最近1-2年，微软在 Silverlight（详细介绍看“[这里](https://en.wikipedia.org/wiki/Silverlight)”）上也是频频出击。而 Sun 也不甘寂寞，搞出了一个 JavaFX（2个月前刚发布，详细介绍见“[这里](https://en.wikipedia.org/wiki/JavaFX)”）。看来RIA领域的竞争有白热化的趋势。干脆今天就来八卦一下这三个技术。 　　有同学可能会问了，为啥不顺便提一下 AJAX 捏？主要是因为 AJAX 和那三个玩意儿有很大的差别，不属于同一个维度，没有可比性（绝没有贬低 AJAX 的意思）。所以今天暂且抛开不谈（下次如果有空再聊 AJAX）。 　　Flash/Flex 早先是由 Macromedia 搞出来的。Adobe 目光独到，在2005年把 Macromedia 吞并了。于是 Flash/Flex 就成了 Adobe 的如意法宝。其实当初收购 Macromedia 的价格并不高，也就34亿美金。这个数字对微软来说是小意思，可惜当初微软真是瞎了眼，没有先下手。否则现在 RIA 市场的格局就是另外一番景象了。话说回来，Adobe 买下 Macromedia 后，对 Flash 也是下了大本钱，再加上那几年没有直接的竞争对手。因此到了2007年，Flash/Flex 已经成为 RIA 市场的事实标准，当时的 PC 占有率少说也有70%。而且开始进入手机市场。 　　目前 Flash/Flex 主要的优势一个是用户群大，还有一个是跨平台（包括操作系统、浏览器、移动设备）。 　　不过我这2-3年用下来，感觉 Flash/Flex 也有不少问题。一个主要的问题是语言的兼容性不够好，当初从 ActionScript2 迁移到 ActionScript3，团队里的人怨声载道（很多代码几乎要重写）。还有一个问题是功能不够强，让人感觉很不爽。比如至今不能够很好地支持多线程（仅支持异步回调）；比如不能很好地整合 PDF（照理说都是自家公司产品，整合应该不难）。 　　估计是到了2006年后，微软发觉苗头不对，赶紧下大力气自己搞。在2007年底和2008年底分别发布了 Silverlight 1.0 和 Silverlight 2.0（3.0据说2009年也有望推出）。然后商务层面也接连出手：先是2008奥运期间与 NBC（美国国家广播公司）合作，用 Silverlight 进行赛事直播；接着在上个月美国总统就职典礼，也用上了 Silverlight。微软的意图非常明显，就是市场方面利用各种机会争夺用户占有率，弥补对 Flash 的劣势；技术方面不断强化功能，力图甩开 Flex，吸引开发人员加入。

　　要说 Silverlight 的优点，我觉得依托于 dotNET 是主要优势。借着 dotNET 这个靠山，Silverlight 能整合现有的某些语言（据说已能支持 JScript、[IronPython](https://en.wikipedia.org/wiki/IronPython)、[IronRuby](https://en.wikipedia.org/wiki/IronRuby)、VB）和库；还能够方便原有的 dotNET 程序员上手。Silverlight 在功能上也显得比 Flex 更强大（比如多线程和 3D 方面）。

　　不过依托于 dotNET 也导致了 Silverlight 的主要缺点：跨平台不够好。虽说现在有 Moonlight 的帮忙，但依然不够理想（尤其是对 Linux 的支持）。  
　　坦白讲，JavaFX 实在是乏善可陈。Sun 的一个主要失策就在于后知后觉，跟进太慢。微软下手已经慢了，结果 Sun 比它还慢。而 Sun 在财力上又比微软差了很多（Sun 现在自身难保，根本没法像微软那样烧钱搞推广），做 IDE 也不如微软拿手。真是天时、地利、人和皆无。难怪连 Java 社区对它也热情不高（有 Java 大牛[Bruce Eckel](https://en.wikipedia.org/wiki/Bruce_Eckel)的文章“[Does Anyone Really Care About Desktop Java?](http://www.artima.com/weblogs/viewpost.jsp?thread=234900)”为证）。  
　　假如你要开发一个 Web 系统，打算从上述三种 RIA 技术中挑选一个。那么你先要评估一下你的 Web 应用对跨平台的需求如何？如果你需要同时支持各种各样的客户端操作系统和浏览器，那强烈建议你选择 Flex（我的部门现在面临的就是这种情况）；反之，如果你铁定**只要**支持 Windows，或许也可以考虑 Silverlight。至于说 JavaFX，短期内就先不要考虑啦。

