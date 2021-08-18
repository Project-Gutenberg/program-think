---
layout: default
title: '近期安全动态和点评&#65288;2019年2季度&#65289;'
date: None
author:
    display_name: 
---

　　最近好几篇博文都在谈“时政话题”，今天这篇换个口味。正好2季度已经结束，汇总一下上季度的信息安全动态。  
  
  
《[中国公司泄漏数亿简历 @ Solidot](https://www.solidot.org/story?sid=60159)》  

> 因为未加密或配置错误的 MongoDB 数据库和 ElasticSearch 服务器，中国公司泄漏了5.9亿简历。安全研究员 Sanyam Jain 仅在上个月就报告了7次数据外泄。他发现了一台 ElasticSearch 服务器包含了3300万用户简历。在报告给中国国家计算机应急响应小组四天后服务器才加了安全保护。另一台 ElasticSearch 服务器包含了8480万简历，同样是在举报给计算机应急响应小组之后下线的。  
> 他总共发现暴露的简历数量高达5.90497亿，许多简历包含了敏感的个人数据如电话号码、家庭住址，家庭和婚姻状况，某些还有身份证。

　　**编程随想注：** 　　文中提到的这个安全研究员，在3~4月份发现了这么多【裸奔】的数据库，不是因为他多么牛逼，而是因为—— 越来越多的企业在搞“大数据”，相关的程序猿/程序媛虽然懂得如何操作 MongoDB 和 ES，但其中的大部分人在信息安全方面完全是【菜鸟】，连基本的安全防范意识都非常缺乏。 　　再来说“测试人员”，绝大部分也【不】懂得如何进行【安全测试】。就算极少数测试人员，最终学会了这个，肯定转行去干“信息安全相关的工作”，怎么可能还在干“软件测试”？  
《[北京上海地铁检查乘客手机——1984社会全面实现 @ 中国数字时代](https://chinadigitaltimes.net/chinese/2019/06/%e3%80%90%e5%9b%be%e8%af%b4%e5%a4%a9%e6%9c%9d%e3%80%91%e5%8c%97%e4%ba%ac%e4%b8%8a%e6%b5%b7%e5%9c%b0%e9%93%81%e6%a3%80%e6%9f%a5%e4%b9%98%e5%ae%a2%e6%89%8b%e6%9c%ba%ef%bc%9a1984%e7%a4%be%e4%bc%9a/)》

　　**编程随想注：**

　　前些年，俺在博客评论区与读者交流时就提到过——新疆警方可以随意盘查路人手机（以“反恐”的名义）。从“中国数字时代”这篇报道来看，这种做法可能会推广到其它省份（目前【还没有】大范围盘查；未来是否会这么干，就不好说啦） 　　警方盘查路人的手机，采用的是专业的【手机取证软件】。这种软件可以在手机解锁之后，快速扫描整个存储空间，并把所有值得提取的数据都找出来（比如：通讯录、所有通话记录、全部上网历史、各种 App 的聊天记录、照片、视频......）。它甚至可以恢复出“你曾经删除过的通讯录联系人”或者“你曾经删除过的 IM 聊天记录”。 　　顺便插两句：

　　在取证领域有一个专门的术语叫做“删除恢复”。而绝大部分手机用户完全不懂得如何彻底删除手机数据。有关“彻底删除数据”的讨论参见：《[如何用“磁盘加密”对抗警方的【取证软件】和【刑讯逼供】，兼谈数据删除技巧](https://program-think.blogspot.com/2019/02/Use-Disk-Encryption-Anti-Computer-Forensics.html)》

　　某些比较牛的手机取证软件，可以【直接破解】手机（不需要让机主解锁）并收集手机中的信息。关于“破解手机”的话题，下面某个章节还会聊到。 　　目前警方常用的“取证软件”分为两大类—— 1、手机取证（含平板） 2、PC 取证 　　移动设备要【对抗】“手机取证软件”会比较难。因为移动设备上【缺乏】足够好的【磁盘加密工具】。 　　虽然目前的 Android 和 iOS 都能支持“全盘加密”。但“全盘加密”是【不够】滴。因为当警方要求你解锁手机时，（除非你足够牛逼，否则）你只能乖乖配合。而一旦你交出了手机的解锁方式（“解锁密码”或“解锁图案”），操作系统自带的“全盘加密”就【没有意义】啦。 　　相比之下，【PC】上可以做到很多手机上无法实现（或难以实现）的技巧。简单列几条：

　　**1、嵌套加密**

　　PC 上可以组合多种不同的加密工具，实现【多层】嵌套——先使用“全盘加密”，然后在此基础上再建立加密盘（物理加密分区 or 虚拟加密盘）。 　　即使在警方的逼迫下解锁了最外层的“全盘加密”，你的敏感数据依然被【内层】的某个加密盘所保护。 　　只要你把内部的加密盘伪装得足够好，取证软件【不一定】能发现。

　　**2、伪装“物理加密分区”**

　　可以把某个“加密分区”伪装成“未使用分区”。 　　（注：做得好的磁盘加密工具，其“加密分区”的数据看起来是【全随机】滴，而且【没有】显式的头部格式或标识。也就是说，其数据看起来与“未用分区”的效果完全一样，取证软件【无法】区分这两者）

　　**3、Plausible Deniability**

  
　　这个特性的原理可以参考“[这篇教程](https://program-think.blogspot.com/2011/05/recommend-truecrypt.html)”。 　　使用这种技巧的加密盘有【两套】密码。用这2个密码解锁之后看到的内容是【不同】滴。其中一个密码专门用来——当你受到胁迫时，故意勉为其难地告诉对方，该密码解锁加密盘之后，看到的都是一些无关痛痒的内容（不那么重要的内容）；而另一个密码才是真正的密码。 　　由于“Plausible Deniability”的设计在“密码学层面”是【严密】滴。因此，取证软件【无法判断】某个加密盘是否采用了这种“双重密码”的机制。也就是说：警方就算找到了你的某个加密盘，并逼迫你交出该加密盘的密码，警方依然【无法判断】这个加密盘是否还存在“另一套密码”。

　　**4、“加密盘”结合“虚拟机”**

　　你可以把【所有的】危险操作都放到虚拟机中进行。而虚拟机则保存在某个加密盘中（可以是“物理加密分区”，也可以是“虚拟加密盘”）。如此一来，你的物理系统（Host OS）上所有的操作痕迹都是很普通滴，即使被取证软件收集到也无所谓。 　　就算取证软件发现了你用来保存虚拟机的加密盘，你还可以继续使用“Plausible Deniability”这个技巧（参见第3条）。 　　刚才列出的这几个招数，都可以帮你更好地隐藏敏感数据。更详细的教程，请参考下面几篇博文：

《[如何用“磁盘加密”对抗警方的【取证软件】和【刑讯逼供】，兼谈数据删除技巧](https://program-think.blogspot.com/2019/02/Use-Disk-Encryption-Anti-Computer-Forensics.html)》

  
《[TrueCrypt 使用经验](https://program-think.blogspot.com/2011/05/recommend-truecrypt.html#index)》（系列）  
《[扫盲 VeraCrypt——跨平台的 TrueCrypt 替代品](https://program-think.blogspot.com/2015/10/VeraCrypt.html)》  
《[扫盲 dm-crypt——多功能 Linux 磁盘加密工具（兼容 TrueCrypt & VeraCrypt）](https://program-think.blogspot.com/2015/10/dm-crypt-cryptsetup.html)》  
《[文件加密的扫盲介绍](https://program-think.blogspot.com/2011/05/file-encryption-overview.html)》  
《[“刷脸”的风险，你知道多少？ @ 检查日报](http://newspaper.jcrb.com/2019/20190417/20190417_005/20190417_005_1.htm)》  

> “人脸识别的便捷性与安全性不可兼得。”在电子科技大学信息与通信工程学院副教授曾辽原看来，不管什么技术总有其特有的使用场景，人脸识别技术应该作为核实身份的辅助手段，而不是唯一的、关键的手段，特別是在安全性要求高的领域，更不能作为单一的识别手段。 “个人生物信息直接采集于人体、且是个人生理特性的直接体现并唯一对应……”今年两会期间，全国人大代表、北京科学学研究中心副主任伊彤提交了一份《关于开展公民个人生物信息保护立法的建议》，伊彤认为，个人生物信息与我们平时设定的密码不同，如果密码泄露，我们可以随即换一个密码；而个人生物信息一旦泄露，就是终身泄露，会将用户个人信息安全置于更大的不确定性中，进而引发一系列风险。 曾辽原同时指出，“一旦带有唯一性的生物特征数据被他人盗取利用，会造成个人信息安全、生命财产安全等相关问题，而且会导致大量深层信息被挖掘、曝光，给公民造成物质和精神上的极大损害。” ...... 在今年2月份，中国就发生了一起广受争议的隐私安全事件——一家专注安防领域的人工智能企业被曝发生大规模数据泄露事件，超过250万人的数据可被获取，有680万条数据疑似泄露，包括身份证信息、人脸识别图像及图像拍摄地点等。据悉，该企业主要研发“人脸识别技术”，与不少部门机构都有人工智能的安防合作。
> 
> “目前，个人生物信息的安全问题是不可控的。”曾辽原表示，人脸和其他生物特征数据间的一个巨大区别是，它们可以远距离起作用，这意味着我们在网上自拍或在街上走路时，都有可能不自觉交出了自己的个人生物信息。可以说，随着摄像头越来越普及，我们将真正进入“弱隐私”时代。如今，人脸、声纹、虹膜、指纹，甚至是步态都已经成为重要的个人身份信息，随着生物特征识别技术在生活中的广泛使用，极有可能成为个人隐私的泄露方式。

  
《[程序员人脸识别成人视频中的女性，引发争议 @ Solidot](https://www.solidot.org/story?sid=60808)》  

> 一位身在德国的中国程序员在新浪微博上发帖称，程序员被说成是从事色情行业的女性的接盘侠，他与其朋友因此决定把成人视频中的女性和社交网络中的女性照片进行匹配，识别其身份，帮助程序员们过滤一下避免成为接盘侠。他们花了半年时间利用 1024、91、sex8、PronHub、xvideos 等网站采集的数据对比 Facebook、instagram、TikTok、抖音、微博等社交媒体，在全球范围内成功识别了10多万名从事色情行业的女性（为了避免微博审查而将色情行业改为不可描述行业）。  
> 此举引发了热议和争议，他随后辩解称他的意图是允许女性检查她们的照片或视频是否在成人网站上，她们可以向网站发送 DMCA 删除通知要求删除照片或视频。这位叫“将记忆深埋”（或 mitboy）的用户表示将在5月31日在 GitLab 公开数据库结构。

  
《[旧金山成美国首个禁止面部识别技术城市 @ 搜狐](http://www.sohu.com/a/314145694_260616)》  
《[Firefox 发布 Track THIS，故意向广告商提供虚假浏览历史 @ cnBeta](https://www.cnbeta.com/articles/tech/861759.htm)》  

> 广告商在互联网上跟踪你的一举一动，然后它会根据你的浏览习惯向你展示针对性的广告。如何应对这种无处不在的监视资本主义？Mozilla 和 mschf 工作室提供了一种方法：把你的浏览历史打乱，创造出虚假版本提供给广告商。
> 
> 他们合作发布了 [Track THIS](https://trackthis.link/)，根据你选定的角色——潮人、有钱人、世界末日预备者以及意见领袖。
> 
>   
> 打开100个特定标签，你的浏览历史将会被去个性化，将让广告商不知道如何定位你。注意，加载一百个标签可能需要几分钟的时间。

  
  
　　**编程随想注：**  
　　这个功能刚引入，目前还没有提供配置界面。为了启用该功能，需要开启 Firefox 中名为 `privacy.resistFingerprinting.letterboxing` 的配置选项。  
　　如果你不懂得定制 Firefox 配置选项，请参见博文：《[扫盲 Firefox 定制——从“user.js”到“omni.ja”](https://program-think.blogspot.com/2019/07/Customize-Firefox.html)》  
《[Major Browsers to Prevent Disabling of Click Tracking Privacy Risk @ Bleeping Computer](https://www.bleepingcomputer.com/news/software/major-browsers-to-prevent-disabling-of-click-tracking-privacy-risk/)》  
　　**编程随想注：**  
　　在上一季度（2019年1季度）的《[近期安全动态和点评](https://program-think.blogspot.com/2019/04/Security-News.html)》中已经提到了——Chrome 移除了“点击追踪”的配置选项，使得用户【无法禁用】该特性。而这个特性是有隐私风险滴！ 　　如今，Safari 和 Opera 跟随 Chrome 的步伐，也在这个问题上耍流氓（不让用户禁止该特性） 　　考虑到某些读者没有看过上一期的《近期安全动态和点评》，再次扫盲一下“点击追踪”的概念—— 　　所谓的“点击追踪”是 HTML5 引入的特性，术语叫做“ping 属性”。如果网站在“超链接”中加入该属性，当用户点击这个超链接的时候，链接所在网站会得到点击的通知。很多网站用“点击追踪”来统计【外链】的点击情况。 　　Google 作为搜索引擎，用户点击搜索结果，当然属于【外链点击】。所以，“点击追踪”这个功能对 Google 而言很有用（可以统计用户曾经点击过搜索结果中的哪些网站）。 　　引申阅读：

《[弃用 Chrome 改用 Firefox 的几点理由——关于 Chrome 69 隐私丑闻的随想](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)》

  
《[今日头条称通讯录不属个人隐私遭“打脸”，98% 网民表示反对 @ IT 时代网](https://www.ittime.com.cn/news/news_28223.shtml)》  
　　**编程随想注：** 　　国内的流氓公司，总是一次又一次地刷新“道德下限”。 　　该说法出自“今日头条”背后的“北京字节跳动科技有限公司”所聘请的律师。由于“今日头条 APP”擅自收集用户通讯录，遭到用户起诉。该公司聘请的律师为了打赢官司，企图证明——通讯录不属于个人隐私，并在法庭上说了一通歪理。 　　此说法引发舆论震惊。事后，“今日头条”赶紧在官网上进行澄清，以平息众怒。  
《[通过 reCaptcha v3，Google 收集大量用户隐私 @ Solidot](https://www.solidot.org/story?sid=61159)》  

> Google 去年更新了它的 reCAPTCHA 机器人程序检测技术。reCAPTCHA 是使用最广泛的反机器人技术，reCAPTCHA v1 让用户看模糊扭曲的字符，reCAPTCHA v2 让用户从模糊的图像中间挑选出街道或商店。而最新的 reCAPTCHA v3 则使用 Google 的私有技术去学习网站的正常流量和用户行为，访问者将会根据访问来源或行为分配一个风险分数。但基于风险分数的系统是需要付出一个巨大代价的：用户的隐私。  
> 两位研究 reCaptcha 的安全研究人员称，Google 判断你是否是恶意用户的一种方法是你的浏览器是否已经安装了 Google cookie。同样的 cookie 允许你无需重新登录就能进入 Google 的服务。多伦多大学计算机科学博士生 Mohamed Akrout 的测试显示，相对于没有 Google 帐户的浏览器，reCaptcha v3 给了已连接 Google 帐户的浏览器更低的风险分数。如果通过 Tor 或 VPN 访问包含 reCaptcha v3 的网站，风险分数总是更高。为了让风险分数正确的工作，网站需要在每一个网页嵌入 reCaptcha v3 代码，而不仅仅是登录页面。这意味着 Google 会从你访问的每一个网页收集数据，而且没有任何视觉指示显示你正在被监视着。Google 声称它的 reCaptcha API 会向它发送软件和硬件信息，表示这些信息只是用于对抗垃圾流量和滥用。根据统计网站 Built With 的数据，目前有超过65万个网站已经使用了 reCaptcha v3。

　　**编程随想注：** 　　经常有读者（尤其那些用 TorBrowser 的读者）抱怨说：在俺博客发表【匿名留言】很麻烦，老是一遍遍地进行“人机验证”。 　　如果你理解了上面这篇报道，自然也就理解了——为啥 Google 的“人机验证”对 TorBrowser 用户【很不友好】。因为 TorBrowser 能有效地【消除】用户的身份信息。碰到这类 Web 客户端，reCaptcha v3 会给出更高的“风险评分”，从而让 Google 的服务器更加怀疑你是恶意用户。 　　（注：具有【恶意行为】的用户，也会采用类似的技术手段，以消除身份信息。所以当 reCaptcha 无法从你的浏览器收集到足够的身份信息，就容易怀疑你是“恶意用户”） 　　你可以【换一个角度】来看待这个问题——当 Google 的 reCAPTCHA 要求你一遍遍地进行人机验证，别太沮丧。这说明你的“隐私保护”还算凑合 :)  
《[香港社媒群主被拘捕，仅因发送“反送中”资讯 @ RFA/自由亚洲电台](https://www.rfa.org/mandarin/Xinwen/d-06122019114307.html)》  

> 香港《立场新闻》6月11号报道，香港警方在当晚以“串谋公众防扰罪”为由拘捕一名 “反送中”游行 Telegram 消息群的管理员。 管理员 Ivan Ip 称，自己只是参与 Telegram 消息群“公海总谷”的管理，仅仅只是发布网上整合的中学罢课名单和参与者被捕的消息，并未到现场参加“反送中”游行，却在6月11号当天晚上遭到警方上门搜查。警察要求他交出手机，然后将他手机上的 Telegram 资料导出，拿到了群组成员的名单和消息内容，并追问他关于群组创办人和管理员的身份信息，以及“其他激进分子的行动计划”。随后警方将其拘捕，带到警署进一步审问直到第二天凌晨4时，他才获保释离开。
> 
> 事发前，Telegram 消息群“公海总谷”已有2、3万名群成员，在这名管理员被捕后，其他管理员已将群组解散。

　　**编程随想注：** 　　俺以【匿名身份】开博已经十多年。期间有很多热心读者建议俺开通 Telegram 或 WhatsApp，以便更好地与读者交流。每次都被俺婉言谢绝了。 　　如今香港的这个案例，再次凸显出 Telegram 在【隐匿性】方面的风险——因为 Telegram 需要【绑定手机】。说得更直白一些：任何需要绑定到手机的网络工具（不管是 IM 还是邮箱），都会大大降低你的【隐匿性】。 　　正是由于这方面的风险，当俺以“编程随想”这个身份进行网络活动时，【绝不】使用任何需要绑定手机的网络服务。 　　引申阅读：

《[为啥朝廷总抓不到俺——十年反党活动的安全经验汇总](https://program-think.blogspot.com/2019/01/Security-Guide-for-Political-Activists.html)》

  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》（系列）  
  
《[NSA Cybersecurity Advisory: Patch Remote Desktop Services on Legacy Versions of Windows @ NSA/美国国安局](https://www.nsa.gov/News-Features/News-Stories/Article-View/Article/1865726/nsa-cybersecurity-advisory-patch-remote-desktop-services-on-legacy-versions-of/)》  
《[微软警告：近百万 Windows PC 存在 Bluekeep 高危漏洞，需紧急修复 @ IT 之家](https://www.ithome.com/0/426/255.htm)》  

> 近期报告称，安全研究人员估计，有近百万台 PC 容易受到 Bluekeep 高危漏洞影响，这是一种存在于 Windows XP、Windows 7 以及 Windows Server 2003 和 Windows Server 2008 的远程桌面攻击。 现在微软加入了呼吁行动的行列，要求 IT 管理员紧急修补他们的设备。 微软警告说，“如果我们回顾 WannaCry 攻击开始前的事件，它们可以告知：未及时修复此漏洞将会面临怎样的风险。”
> 
> ......

　　**编程随想注：**  
　　该漏洞编号 `CVE-2019-0708`，由于此漏洞太过危险，微软【破例】向早已停止支持的 WinXP 和 Win2003 推送安全补丁。  
《[Internet Explorer zero-day lets hackers steal files from Windows PCs @ ZDNet](https://www.zdnet.com/article/internet-explorer-zero-day-lets-hackers-steal-files-from-windows-pcs/)》

　　**编程随想注：**

  
　　俺曾经写过一篇博文：《[吐槽一下 Windows 的安全漏洞——严重性超乎想象](https://program-think.blogspot.com/2017/04/Security-Vulnerabilities-in-Windows.html)》，文中专门针对 IE 写了三个章节（如下）。看完这三个章节，你或许能明白——为啥俺一直在警告“IE 的高危漏洞”。  

> ★为啥 IE 浏览器的漏洞特别危险？ ★（在 Windows 上）改用其它浏览器上网，并【不能】消除 IE 的危险性
> 
> ★更要命的是——IE 浏览器的安全漏洞还特别多

　　这次曝光的 IE 高危漏洞与 **mht** 这种格式的处理有关。在绝大部分 Windows 中，IE 都是打开 mht 格式的默认软件（通常也是唯一的软件）。因此，就算你平常【不用】IE 上网，但只要你不小心打开了某个【恶意的】mht 文件，你的 Windows 就会中招。 　　对于攻击者而言，他们可以有很多种方式来诱骗你打开某个恶意的 mht 文件。  
《[Security vulnerabilities fixed in Firefox 67.0.3 and Firefox ESR 60.7.1 @ Mozilla](https://www.mozilla.org/en-US/security/advisories/mfsa2019-18/)》

　　**编程随想注：**

  
　　这是 Firefox 在两年半之后再次出现高危的 0day 漏洞，编号：`CVE-2019-11707`。攻击者可以利用它实现【远程代码执行】。 　　Mozilla 紧急发布了 Firefox 67.0.3 和 Firefox ESR 60.7.1 版本，进行修复。 　　这个漏洞在被公布之前，或许已经在地下黑市流传了。攻击者利用该漏洞攻击【高价值目标】（比如“比特币交易所的员工”）。 　　以【数字货币】为目标的攻击，正在成为入侵的新趋势——攻击这类目标可以获得高额经济利益。

　　比如：近期微软的邮件服务遭遇入侵（[相关报道](https://www.solidot.org/story?sid=60449)），攻击者的目标也是为了盗取【数字货币】。

  
《[WhatsApp voice calls used to inject Israeli spyware on phones @ FT/金融时报](https://www.ft.com/content/4da1117e-756c-11e9-be7d-6d846537acab)》

　　**编程随想注：**

  
　　这是个“缓冲区溢出漏洞”，编号为 `CVE-2019-3568`。该漏洞位于 WhatsApp 的程序中，适用于 Android 和 iOS。 　　攻击者向目标手机（受害者手机）发起某个特定的 WhatsApp 呼叫，即使对方没有接听也会中招。中招之后，“呼叫记录”【不会】显示在历史记录中。 　　俺已经唠叨了无数次——如果你很在意安全性，就【不要】在手机上进行“重要的操作”或者“敏感的操作”。  
《[Vim 和 NeoVim 曝出高危漏洞 @ Solidot](https://www.solidot.org/story?sid=60976)》  

> Vim 和 NeoVim 曝出了一个允许任意代码执行的高危漏洞。漏洞编号 CVE-2019-12735，Vim 8.1.1365 和 Neovim 0.3.6 之前的版本都受到影响。  
> 漏洞位于编辑器的 modelines 功能中，该功能允许用户指定窗口大小和其它定制选项，modelines 限制了沙盒内可用的指令，但安全研究员 Armin Razmjou [发现](https://github.com/numirias/security/blob/master/doc/2019-06-04_ace-vim-neovim.md) source! 指令会绕过这一保护。因此如果用户打开一个恶意文本文件，攻击者可以控制计算机。  
> 漏洞利用需要编辑器启用 modelines，部分 Linux 发行版默认启用了该功能，而苹果的 macOS 没有默认启用。

　　**编程随想注：**  
　　漏洞发现者制作了一个 GIF 动画（链接在“[这里](https://camo.githubusercontent.com/12bccf0112d4c05f2a26ac528f92ae4fe50575fd/68747470733a2f2f692e696d6775722e636f6d2f387734747465582e676966)”），示范了攻击者利用该漏洞的效果。 　　对于该漏洞，攻击者可以制作某个特殊的 txt 文本文件。这个文件用 cat 命令查看，内容挺正常；但用（有漏洞的）vim 打开这个文本文件，就会中招。 　　顺便吐槽一下： 　　Vim 的【modeline】特性真的是一个非常 ugly 的玩意儿！ 　　为了实现所谓的“文件级的个性化定制”，把【Vim 专有的】控制指令写到文本文件中。这种做法本身就很怪异（让文本文件的内容去依赖某种特定编辑器），而且还增加了【攻击面】。  
  
《[NoScript extension officially released for Google Chrome @ ZDNet](https://www.zdnet.com/article/noscript-extension-officially-released-for-google-chrome/)》

　　**编程随想注：**

  
　　这个扩展的名气很大，维基百科的介绍在“[这里](https://en.wikipedia.org/wiki/NoScript)”。同样大名鼎鼎的 Tor Browser 就内置了它。 　　考虑到“Web 攻击”有很大比例与 JS 相关。俺强烈建议使用 NoScript（或类似的扩展）。这类扩展会提供【白名单模式】——除了少数允许的网站（白名单网站），所有其它网站默认都禁止 JS。 　　NoScript 的“Chrome 版”在功能方面大致类似于“Firefox 版”。但【少了】“XSS filter”的功能——因为这个功能用到了某个 Firefox 的 API，而这个 API 在 Chrome 上没有 :( 以下是 NoScript 作者的原话：

> Talking about differences across supported browsers, the code base is now is exactly the same. But on Chromium, I had to disable, at least for the time being, NoScript's XSS filter. Chromium users will have to rely on the browser's built-in 'XSS Auditor,' which over time proved not to be as effective as NoScript's 'Injection Checker'.
> 
> But the latter could not be ported in a sane way yet, because it requires asynchronous processing of web requests: a feature provided by Firefox only.

　　另外， 　　NoScript 的 10.6.x 版本已经可以兼容 Chrome/Chromium，但还只能达到 beta 品质。作者认为：等到11.0版本时，在兼容 Chrome/Chromium 方面就 OK 了。（注：截止俺写本文时，NoScript 最新版本已经升到11.0）  
《[Dragonblood Vulnerabilities Disclosed in Wi-Fi WPA3 Standard @ Slashdot](https://mobile.slashdot.org/story/19/04/11/1431219/)》  
《[受新 Dragonblood 漏洞影响的 WPA3 Wi-Fi标准 @ 知乎专栏](https://zhuanlan.zhihu.com/p/62188862)》

　　**编程随想注：**

　　WPA 是洋文“Wi-Fi Protected Access”的缩写。WPA3 发布于去年（2018），以替代有设计缺陷的 WPA2。但是 WPA3 才发布一年，其协议设计就被找到严重的漏洞。为啥捏？因为无线网络的协议，设计很复杂（相比【有线】网络的协议而言）。 　　俺又要重新唠叨一下【无线网络】的风险（更大的攻击面）。 　　无线网络的“攻击面”来自很多维度，协议的“复杂性”只是其中之一；另一个维度是【物理空间】。无线网络的本质决定了——在无线信号覆盖范围内的任何人都可以对收集到的无线信号进行分析。如果网络协议本身不严密（有漏洞），那么攻击者就能【更容易地】加以利用。

　　在下面这篇博文中，俺还提到了：那些安全防范等级较高的公司或机构，其【核心网络】肯定是物理布线，而不会走 wifi 之类的无线网络。

  
《[为啥朝廷总抓不到俺——十年反党活动的安全经验汇总](https://program-think.blogspot.com/2019/01/Security-Guide-for-Political-Activists.html)》  
《[Linux PCs, Servers, Gadgets Can Be Crashed by 'Ping of Death' Network Packets @ Slashdot](https://linux.slashdot.org/story/19/06/17/2018227/)》

　　**编程随想注：**

  
　　漏洞编号 `CVE-2019-11477`，影响 Linux Kernel 2.6.29 之后的所有版本。 　　这个漏洞最多只引发“DoS”（拒绝服务攻击），风险还不算高（相比那些能【执行代码】的漏洞而言）。服务器的管理员会比较关注这个漏洞。 　　俺提到这个漏洞是为了——顺便介绍一下 Linux 的【sysctl】。 　　在这个漏洞刚刚曝光时，补丁尚未发布，系统管理员可以利用 sysctl 禁用 TCP SACK。 　　sysctl 是 Linux 内核提供的一种机制，可以动态修改内核的参数。 　　与“重编译内核”相比，sysctl 的灵活性比较差（可定制的选项不太多），但 sysctl 用起来比较简单（傻瓜化）。 　　“加固 Linux 系统”有很多种手法，其中一种是：用 sysctl 把一些没用要到的功能模块禁掉，以【降低攻击面】。举个栗子：如果你的 Linux 完全没用到 IPv6，可以通过 sysctl 把 IPv6 禁掉。 　　sysctl 除了可以用来“禁用功能模块”，还可以用于“参数调优”，以提升安全性和性能。

　　更多的相关介绍请参考：《[Linux hardening with sysctl settings @ Linux Audit](https://linux-audit.com/linux-hardening-with-sysctl/)》

  
  
《[Tor Browser for Android 发布首个稳定版本 @ Solidot](https://www.solidot.org/story?sid=60704)》  

> Tor 项目在 Google Play 应用商店[发布了](https://blog.torproject.org/new-release-tor-browser-85) Tor Browser for Android 的首个稳定版本。 去年9月发布的 alpha 版本需要先安装代理应用 Orbot 将 Tor Browser for Android 与 Tor 网络连接起来，稳定版本不再需要 Orbot。
> 
> Tor Browser for Android 是基于 Firefox 60.7.0esr，开发者表示由于苹果的限制它无法发布 Tor Browser to iOS。

　　**编程随想注：** 　　引申阅读：

《[“如何翻墙”系列：扫盲 Tor Browser 7.5——关于 meek 插件的配置、优化、原理](https://program-think.blogspot.com/2018/04/gfw-tor-browser-7.5-meek.html)》

  
《[Cellebrite Now Says It Can Unlock Any iPhone for Cops @ Wired](https://www.wired.com/story/cellebrite-ufed-ios-12-iphone-hack-android/)》

　　**编程随想注：**

　　一家专门开发【取证软件】的以色列公司（Cellebrite）宣称：它刚发布的取证软件 UFED（Universal Forensic Extraction Device）可以破解任意型号的苹果手机（包括刚刚发布的 iOS 12.3）。 　　可能某些读者会怀疑：这个 Cellebrite 公司有没有吹牛？ 　　在上述报道中还提到了“Cellebrite 的竞争对手”——来自美国的 GreyKey 公司。GreyKey 开发的取证软件已经能破解 iOS 12 的某些版本。 　　贴这个新闻就是为了说明—— 　　【移动设备】的风险，以及警方【取证软件】对移动设备的威胁。 　　（具体的讨论，本文前面的章节刚刚聊过，就不重复了）  
《[Phones Can Now Tell Who Is Carrying Them From Their Users' Gaits @ Slashdot](https://mobile.slashdot.org/story/19/05/22/2125252/)》

　　**编程随想注：**

　　由于这篇是洋文，通俗解释一下。 　　每个人的【步态】都具有其独特性（唯一性），就好像每个人都有独特的指纹。 　　由于手机经常会被随身携带，而且智能手机通常都内置了陀螺仪。那么，如果某个 App 具备了相关的权限，就可以观测手机主人的【步态】。并以此来作为某种【唯一标识】。这其中当然就包含了“隐私风险”。 　　更危险的是——以【步态】作为“身份标识”具有【跨设备】的效果。 　　设想一下：如果你有两个手机，都装了某个 App，并且这个 App 具备上述风险。哪怕你【从不】在这两个手机的 App 上进行【用户登录】，哪怕你【从不】同时携带这两个手机（每次只携带其中一个）。但这两个手机上的 App 如果收集了足够多的【步态信息】并汇总到 App 的服务器，服务器上的软件根据这些数据就可以判断出——这两个物理设备属于【同一个自然人】。

　　手机的问题在于——它包含了很丰富的【探测手段】（比如：摄像头、麦克风、陀螺仪、GPS......）。这玩意儿简直就是现代版的“电幕”（看过《[1984](https://docs.google.com/document/d/144NKDAcg-ip8rwhRtE9fdPan8ZSxqNaEh1A-sYYa7nk/)》这部小说的同学应该知道俺在说啥）

  
《[Android 供应链攻击 @ Solidot](https://www.solidot.org/story?sid=61139)》  

> Google 本月初[披露](https://security.googleblog.com/2019/06/pha-family-highlights-triada.html)了一起 Android 供应链攻击，称一家供应商在数百万台设备上预装了 Triada 恶意程序去展示广告。那么 Triada 是谁开发的呢？Google 称供应商使用了野火（Yehuo 或 Blazefire）这个名字。KrebsonSecurity 对这个名字以及相关域名，域名注册邮箱进行了一番跟踪，[认为](https://krebsonsecurity.com/2019/06/tracing-the-supply-chain-attack-on-android-2/) Triada 与上海野火网络科技有限公司有关，该公司的 CEO 叫楚达。公司域名 blazefire.com 的注册邮箱是 tosaka1027@gmail.com，同一邮箱被用于注册了至少24个域名，至少7个域名被用于传播 Android 恶意程序，其中两个域名被用于传播 Triada，**另外五个被用于传播 Hummer 木马**。Brian Krebs 称 Google 拒绝置评，而野火网络则没有回应。

　　**编程随想注：** 　　请注意俺标注了粗体的那句。上海的这家公司，不仅利用“供应链攻击”植入广告，还传播【木马】。 　　最近一年，“中美对抗”急剧升温。其中一个焦点就是【信息安全】。如今出了这么一个案例，典型的“授人以柄”。  
  
《[Introducing Matrix 1.0 and the Matrix.org Foundation @ Matrix 官网](https://matrix.org/blog/2019/06/11/introducing-matrix-1-0-and-the-matrix-org-foundation)》

　　**编程随想注：**

　　前面提到：香港“反送中抗议活动”期间，某个 Telegram 群主被警方抓了。那段时间也有读者在博客评论区交流：如何更隐匿地使用 IM 工具？ 　　6月份正好赶上“Matrix 1.0 版本发布”，今天顺便介绍一下： 　　利用“Matrix 协议”可以帮你实现一个更自由的、不受政府和商业公司控制的“IM 生态环境”。Matrix 是【去中心化】的，但它又不同于“P2P 模式”，它实际上属于【联邦式】（federation）。 　　在这种模式中，还是有 Server 与 Client。但不同于传统的【中心式】，任何人都可以创建 Server。“Matrix 协议”负责在“Server 与 Server 之间”、“Client 与 Server 之间”同步数据，从而让不同 Server 的帐号也能相互沟通。

　　擅长看洋文的，可直接看“英文维基百科”（[这里](https://en.wikipedia.org/wiki/Matrix_(protocol))）；不擅长看洋文的，贴一篇中文的扫盲教程（[这里](https://vimacs.wehack.space/matrix-guide/)）。

　　引申阅读：

《[“对抗专制、捍卫自由”的 N 种技术力量](https://program-think.blogspot.com/2015/08/Technology-and-Freedom.html)》

　　另外，在4月份还有这样一个新闻：《[法国政府发布它开发的端对端加密消息应用 @ Solidot](https://www.solidot.org/story?sid=60328)》。

　　法国政府基于【Matrix 协议】开发了一个 IM 工具（Tchap），用来替代“Telegram 和 WhatsApp”。并且这个 Tchap 最终会被用于法国所有政府部门。  
  
《[Security flaw lets attackers recover private keys from Qualcomm chips @ ZDNet](https://www.zdnet.com/article/security-flaw-lets-attackers-recover-private-keys-from-qualcomm-chips/)》

　　**编程随想注：**

  
　　此漏洞编号 `CVE-2018-11976`，去年就已经发现（注意看编号的前4位），据说高通到今年4月才修复此问题。 　　高通芯片内有个硬件级的“安全执行环境”（洋文叫“Qualcomm Secure Execution Environment”，简称“QSEE”），专门用于进行敏感的密码学运算。

　　NCC Group 的安全研究人员通过“旁路攻击”（也称“边信道攻击”）的手法，可以从 QSEE 中逐步地恢复出 ECDSA（Elliptic Curve Digital Signature Algorithm）的密钥。漏洞发现者（NCC Group）在今年4月发了一篇 whitepaper（链接在“[这里](https://www.nccgroup.trust/globalassets/our-research/us/whitepapers/2019/hardwarebackedhesit.pdf)”）

　　考虑到高通芯片在移动设备中【极高的使用率】。这个漏洞的打击面非常大。  
《[RAMBleed Rowhammer 攻击能窃取数据 @ Solidot](https://www.solidot.org/story?sid=60955)》  

> 一个国际研究团队发表[论文](https://rambleed.com/docs/20190603-rambleed-web.pdf)，描述了 Rowhammer 比特翻转攻击的新变种，称能用于窃取内存中的数据。 Rowhammer 攻击利用了 DRAM 临近内存单元之间电子的互相影响，当重复访问特定内存位置数百万次后，攻击者可以让该位置的值从0变成1，或从1变成0。新的攻击被称为 RAMBleed，通过观察 Rowhammer 诱导的比特翻转，攻击者能推断出附近 DRAM 行中的值。
> 
> 在论文中，研究人员演示了对 OpenSSH 7.9 的攻击，他们利用 RAMBleed 攻击获取了2048比特的 RSA 密钥。研究人员称 RAMBleed 潜在能读取储存在内存中的任何数据，表示 ECC（Error Correcting Code）内存并不能防止 RAMBleed 攻击。

　　**编程随想注：**  
　　在上一季度（2019年1季度）的《[近期安全动态和点评](https://program-think.blogspot.com/2019/04/Security-News.html)》中已经简单扫盲了【Row Hammer 攻击】。当时提到了“针对 Intel 处理器的新型 Spoiler 攻击”，并提到：这种“新型 Spoiler 攻击”能大大加快“Row Hammer 攻击”的效率。 　　俺估计：未来应该会有更多“Row Hammer 攻击手法”被研究出来。  
《[绕过验证安装底层后门——英特尔固件启动验证绕过新方法 @ 安全内参](https://www.secrss.com/articles/10631)》  

> 本周在荷兰阿姆斯特丹举行的 Hack in the Box 大会上，研究员 Peter Bosch 和 Trammell Hudson 演示了针对英特尔统一可扩展固件接口（UEFI）Boot Guard 功能的“检查时间与使用时间”（TOCTOU）漏洞攻击。 注： TOCTOU：“time of check and the time of use”，代码先检查某个前置条件（例如认证），然后基于这个前置条件进行某项操作，但是在检查和操作的时间间隔内条件却可能被改变，如果代码的操作与安全相关，就很可能产生漏洞。 Boot Guard 是英特尔第4代 Core 微架构（Haswell）中引入的一种技术，旨在提供底层固件（UEFI）防护保障，使其免于被恶意篡改。 ...... 虽然该攻击要求打开笔记本电脑以往芯片上夹上连接器，但有多种方法可以让攻击成为永久性的，比如直接将 SPI 芯片换成模拟 UEFI 的同时注入恶意代码的流氓 SPI。该攻击的芯片替换版就类似于驻留硬件版的 bootkit，可用于从系统中盗取磁盘加密口令和其他敏感信息，且若不开箱仔细检查主板是非常难以检测出来的。 尽管此类物理攻击针对性很强，永远不会成为广泛传播的威胁，但仍对能接触到有价值信息的公司企业和用户形成严重的风险。 此类物理侵害发生形式多样，比如邪恶女佣类场景——公司 CEO 之类高价值目标海外旅游去了，笔记本电脑就这么毫不设防地留在了酒店房间里，攻击者买通或自己假扮成服务生就能进去换掉 SPI 芯片。
> 
> ......

　　**编程随想注：**  
　　“邪恶女佣攻击”，洋文叫做“evil maid attack”，相关介绍参见维基百科的[这个页面](https://en.wikipedia.org/wiki/Evil_maid_attack)。 　　借这个案例再次提醒大伙儿（尤其是“高价值目标”），【物理安全】也很重要哦！ 　　依靠硬件漏洞实现的【bootkit】比 rootkit 更牛逼——因为其层次比操作系统【更低】。比如说，当你输入“全盘加密的解锁密码”之时，操作系统【并未】真正启动。所以操作系统内部的恶意软件【无法】截获你的“全盘加密密码”，但 bootkit 可以。 　　另外， 　　在上述文章中也提到了【供应链攻击】。如果笔记本电脑的在另一个国家组装，可以在组装过程中【偷掉 SPI 芯片】。“中美对抗”在近期逐渐升温，美方的安全人员一直在警告【供应链攻击】。  
  
《[SHA-1 碰撞攻击正变得切实可行 @ Solidot](https://www.solidot.org/story?sid=60610)》  

> Google 在2017年宣布了对 SHA-1 哈希算法的首个成功碰撞攻击。所谓碰撞攻击是指两个不同的信息产生了相同的哈希值。在 Google 的研究中，攻击所需的计算量十分惊人，用 Google 说法，它用了6,500年的 CPU 计算时间去完成了碰撞的第一阶段，然后用了110年的 GPU 计算时间完成第二阶段。  
> 现在，SHA-1 碰撞攻击[正变得切实可行](https://www.zdnet.com/article/sha-1-collision-attacks-are-now-actually-practical-and-a-looming-danger/)。上周一组来自新加坡和法国的研究人员演示了首个构造前缀碰撞攻击（[PDF](https://eprint.iacr.org/2019/459.pdf)），即攻击者可以自由选择两个碰撞信息的前缀。构造前缀碰撞攻击所需的计算费用不到10万美元，意味着伪造 SHA-1 签名文件将变得可能，这些文档可能是商业文件也可能是 TLS 证书。现在是时候完全停止使用 SHA-1 了。

　　**编程随想注：** 　　不懂“散列算法”的同学可以看下面这篇扫盲教程。

《[扫盲文件完整性校验——关于散列值和数字签名](https://program-think.blogspot.com/2013/02/file-integrity-check.html)》

　　在 SHA1 报废之后，可用来替代它的是 SHA256。俺估计 SHA256 在5~10年的跨度内应该没问题。至于更久远的未来，SHA256 也会被攻破（找到快速碰撞的算法）。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[为啥朝廷总抓不到俺——十年反党活动的安全经验汇总](https://program-think.blogspot.com/2019/01/Security-Guide-for-Political-Activists.html)》  
《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》（系列）  
《[如何防止黑客入侵](https://program-think.blogspot.com/2010/06/howto-prevent-hacker-attack-0.html)》（系列）  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》（系列）  
《[“对抗专制、捍卫自由”的 N 种技术力量](https://program-think.blogspot.com/2015/08/Technology-and-Freedom.html)》  
《[吐槽一下 Windows 的安全漏洞——严重性超乎想象](https://program-think.blogspot.com/2017/04/Security-Vulnerabilities-in-Windows.html)》  
《[为什么桌面系统装 Linux 可以做到更好的安全性（相比 Windows & macOS 而言）](https://program-think.blogspot.com/2017/03/Why-Linux-Is-More-Secure-Than-Windows-and-macOS.html)》  
《[如何用“磁盘加密”对抗警方的【取证软件】和【刑讯逼供】，兼谈数据删除技巧](https://program-think.blogspot.com/2019/02/Use-Disk-Encryption-Anti-Computer-Forensics.html)》  
《[TrueCrypt 使用经验](https://program-think.blogspot.com/2011/05/recommend-truecrypt.html#index)》（系列）  
《[扫盲 VeraCrypt——跨平台的 TrueCrypt 替代品](https://program-think.blogspot.com/2015/10/VeraCrypt.html)》  
《[扫盲 dm-crypt——多功能 Linux 磁盘加密工具（兼容 TrueCrypt 和 VeraCrypt）](https://program-think.blogspot.com/2015/10/dm-crypt-cryptsetup.html)》  
《[文件加密的扫盲介绍](https://program-think.blogspot.com/2011/05/file-encryption-overview.html)》  
《[扫盲文件完整性校验——关于散列值和数字签名](https://program-think.blogspot.com/2013/02/file-integrity-check.html)》  
《[弃用 Chrome 改用 Firefox 的几点理由——关于 Chrome 69 隐私丑闻的随想](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)》  
《[“如何翻墙”系列：扫盲 Tor Browser 7.5——关于 meek 插件的配置、优化、原理](https://program-think.blogspot.com/2018/04/gfw-tor-browser-7.5-meek.html)》  
《[扫盲 Firefox 定制——从“user.js”到“omni.ja”](https://program-think.blogspot.com/2019/07/Customize-Firefox.html)》

