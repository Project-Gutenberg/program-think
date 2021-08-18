---
layout: default
title: '近期安全动态和点评&#65288;2020年1季度&#65289;'
date: None
author:
    display_name: 
---

　　最近两周，没在评论区出没，某些读者以为俺静默了。其实俺这段时间还是很活跃滴——陆续更新了一批电子书到网盘。那些细心的读者，观察[俺 Github 页面](https://github.com/programthink)的更新历史，会意识到这点。  
  
  
《[疫情下各国强化监控，健康与隐私不可兼得？ @ 纽约时报](https://cn.nytimes.com/technology/20200326/coronavirus-surveillance-tracking-privacy/)》  

> 为了对抗现在的大流行病加强监视，可能会为今后进行更具侵入性的窃听打开永久性的大门。公民自由专家说，这是美国人在2001年9月11日恐怖袭击之后学到的教训。 9·11事件发生将近二十年后，执法机构如今掌握着更强大的监视系统，例如细致精确的位置跟踪和面部识别——这些技术可能会被重新用于反移民政策等进一步的政治议程。公民自由专家警告说，公众几乎没有办法挑战这些由国家实施的数字行动。 曼哈顿的非营利组织监控技术监督项目（Surveillance Technology Oversight Project）总干事阿尔伯特·福克斯·卡恩（Albert Fox Cahn）说：“我们很容易陷入这样的情况，即我们授权地方、州或联邦政府采取措施应对流行病，而这一举措从根本上改变了美国公民权利的范围。” ...... 大流行病的迅速传播促使各国政府以自身利益为名，制定了一系列数字监视措施，而对其合理性或有效性缺乏各国协同的评估。
> 
> 在中国的数百个城市，政府要求市民在手机上使用一种软件，可以自动用颜色代码——红、黄、绿——给每个人分类，以显示感染风险。这个软件决定哪些人应该被隔离，或是可以进入地铁等公共场所。但官员们并没有解释系统如何做出这样的决定，市民们也觉得无力挑战它。

  
《[新冠疫情在全球催生独裁和滥权？ @ 纽约时报](https://cn.nytimes.com/world/20200331/coronavirus-governments-power/)》  

> 在美国，司法部要求国会赋予其更多权力，包括取消对寻求庇护者的法律保护，以及在未经审判的情况下无限期拘禁人民。在共和党和民主党的阻挠下，司法部做出了让步，提交了一份较缓和的提案。 人权组织称，在公民被分心的情况下，政府可能会继续吸收更多权力。他们担忧人们可能意识不到他们让出的权利，等到想收回时已经来不及。 一些紧急法案通过得如此之快，以至于议员和人权组织都没时间阅读，更不用说讨论它们的必要性了。人权活动者也质疑了各国起草冗长立法的速度。 联合国特别报告员奥蕾茵表示，某些政府已为紧急或危机情况“准备好了”一整套所需的权力。他们提前起草了法律，就等“危机出现的机会”，她说。 目前还不清楚危机过后，这些紧急状态法案将何去何从。以往仓促颁布的法律，如9·11袭击后的《爱国者法案》（Patriot Act），在它本来要应对的危机结束后仍然存在着。 随着时间推移，紧急法令会渗透到法律结构中，并成为常态，位于华盛顿的非营利法律国际中心（International Center for Not-for-Profit Law）总裁道格拉斯·鲁岑（Douglas Rutzen）表示，该机构正在追踪大流行期间的新立法和政令。
> 
> “塑造紧急权力真的很容易，”鲁岑说。“拆解它们就很难了。”

　　**编程随想注：** 　　再次提醒大伙儿： 　　不论是在成熟的民主国家，还是在高度专制的国家，都要防范政府滥用公权力。 　　对任何国家的官僚系统（从高层的政客到基层的公务员），都要保持警惕——因为他们手中握有【公权力】。

　　借用启蒙思想家【孟德斯鸠】的名言：**一切拥有权力的人，都有滥用权力为自己谋求私利的倾向。**

　　除了“滥用权力的倾向”，很多政客在滥用权力时，还会为自己找一个非常冠冕堂皇的理由。 　　当年中共夺权后，毛腊肉说：“为人民服务” 　　911事件之后，小布什说：“为了反恐” 　　如今，各国领导人说：“为了防控疫情” 　　......  
《[Google To Phase Out User-Agent Strings in Chrome @ Slashdot](https://tech.slashdot.org/story/20/01/14/1642256/)》

　　**编程随想注：**

　　简而言之，Chrome 从 v81 版本开始减低对“User Agent”的支持；到 v85 版本完全不支持 UA 字符串。

　　（注：关于“User Agent”的讨论，可以参见《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》系列教程的其中一篇）

　　从表面上看，取消“User Agent”有助于降低“浏览器指纹”的信息量。因此，Chrome 的这个举动是值得表扬滴。 　　有些同学会感到奇怪：Google 作为一个【在线广告巨头】，为啥会这么好心捏？因为 Google 有了【更好的】追踪手段。请看——

《[Google 能通过 Chrome 安装 ID 跟踪用户 @ Solidot](https://www.solidot.org/story?sid=63440)》

  

> Google 想要封杀第三方 cookie，想要替换 User-Agent 字符串...Google 会提供很多理由。但最主要的理由它未必会说出来：它有更多的方法跟踪用户。当竞争对手的可用跟踪方法少了之后，它的竞争优势会更大，而 Google 的 Android 和 Chrome 都有无数用户在使用。  
> 在 W3C Technical Architecture Group 上，Google 工程师提出了 User-Agent 的替代。在讨论中，有用户指出 Google 能通过 Chrome 安装 ID 跟踪用户。Chrome 在首次安装运行时会生成 Chrome-Variations 消息头，使用随机选择的种子数生成，如果浏览器禁用了使用统计和崩溃统计，种子数会在0~7999之间选择。Google 称这个消息头不包含任何身份信息，但它可以组合收集的其它信息创造一个[独特 Chrome ID](https://news.ycombinator.com/item?id=22236106)，即使用户使用隐身模式，这个 ID 也不会发生变化。

　　**编程随想注：**  
　　关于 Chrome 的问题，俺已经聊过很多次了。比如这篇《[弃用 Chrome 改用 Firefox 的几点理由](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)》 　　对于重度的 Google 用户，再次唠叨一下： 　　你越是 Google 的重度用户，你就越【不应该】使用 Chrome 作为你的日常浏览器。对于 Google 的重度用户，Google 已经能通过网站服务，收集到你的很多个人信息。而 Chrome 作为【本机软件】，又可以从【操作系统】层面进一步收集信息。 　　这两者结合起来，Google 对你的了解就太多了。  
《[確保用戶隱私，Brave 提供隨機瀏覽器指紋技術 @ iThome](https://www.ithome.com.tw/news/136256)》

　　**编程随想注：**

　　由于隐私意识的提升，对 cookie（尤其是“第三方 cookie”）的限制越来越严格。因此，商业网站和广告商越来越多地依赖【浏览器指纹】来追踪用户。 　　为了对抗“浏览器指纹”，Firefox（以及 Tor Browser）已经做了很多努力——尽量降低浏览器指纹的【信息量】。

（注：关于“浏览器指纹的信息量”，在《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》系列教程的其中一篇有专门介绍）

　　而另一款专注于隐私保护的“Brave 浏览器”计划在未来版本提供【浏览器指纹随机化】。这是一个完全不同的思路——它不是为了降低“指纹的信息量”，而是每次都产生【随机的指纹】。该功能会在每一个浏览器会话（session）产生不同的“浏览器指纹”。因此，当你多次访问同一个网站，网站服务端收集到的“浏览器指纹”会完全不同。如此一来，网站端就搞不清楚：是不是同一个人 :) 　　俺估计，不久的将来，Tor Browser 也会有这方面的举措。 　　关于“浏览器指纹”的小知识： 　　网站之所以能通过“浏览器指纹”来追踪用户，关键在于“浏览器指纹”具有如下两个特点： 其一，独特性 其二，稳定性 　　降低“浏览器指纹”的【信息量】是为了破坏其“独特性”；而随机化“浏览器指纹”是为了破坏其【稳定性】。

　　关于“随机化”这招，当年俺写《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》系列的时候，提到过类似的思路——随机化伪装 User-Agent 字符串。

  
《[Hacker Selling Data of 538 Million Weibo Users @ Slashdot](https://yro.slashdot.org/story/20/03/23/1642248/)》

《[5.38亿微博用户信息泄露，暗网只售不到1万元 @ InfoQ](https://www.infoq.cn/article/G1cH6ygMQWJsuYcQTeAA)》

《[工信部就新浪微博 App 数据泄露问题开展问询约谈 @ 人民网](http://it.people.com.cn/n1/2020/0325/c1009-31646824.html)》

  
  
《[微软提前释出补丁修复加密组件高危漏洞 @ Solidot](https://www.solidot.org/story?sid=63259)》  

> 微软本周二将释出例行安全更新，而 KrebsOnSecurity 援引知情人士的消息[报道](https://krebsonsecurity.com/2020/01/cryptic-rumblings-ahead-of-first-2020-patch-tuesday/)，微软将释出补丁修复一个影响所有版本 Windows 的加密组件高危漏洞。而在例行更新释出前，微软就悄悄向美国军方机构和管理互联网基础设施的高价值客户释出了补丁，为防止漏洞信息泄露，微软还要求这些机构签署了保密协议。消息源称，漏洞存在于加密组件 crypt32.dll 中，该模块用于处理 CryptoAPI 中的证书和加密消息函数。它存在高危漏洞将会影响到许多 Windows 重要功能，包括 Windows 桌面和服务器之间的验证，敏感数据保护，以及第三方应用和工具。

　　**编程随想注：**  
　　该漏洞（`CVE-2020-0601`）位于“验证椭圆曲线加密（ECC）”的函数中。ECC 算法本身【没】缺陷，是 crypt32.dll 这个模块对 ECC 算法的实现没做好。漏洞由 NSA（美国国安局）发现，然后上报给微软。 　　攻击者可以利用这个漏洞，伪造一个貌似合法的数字签名。比如说：把某个木马伪装成带有合法数字签名的安装包，或者利用这个漏洞对加密通讯进行“中间人攻击”，或者搞一个钓鱼网站 ......  
《[微软警告黑客正在利用一个 Windows 0day 漏洞（Adobe Type Manager） @ Solidot](https://www.solidot.org/story?sid=63910)》  

> 微软警告黑客[正在利用](https://arstechnica.com/information-technology/2020/03/attackers-exploit-windows-zeroday-that-can-execute-malicious-code/)一个 Windows 0day 漏洞去执行恶意代码。[漏洞](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/adv200006#ID0EMGAC)存在于 Adobe Type Manager Library 中，这个 DLL 文件被应用广泛用于管理和渲染 Adobe Systems 的字体。它由两个代码执行漏洞构成，可以通过不正确处理 Adobe Type 1 Postscript 格式的恶意主字型触发。攻击者诱骗目标打开恶意文档或在 Windows 预览面板浏览文件来利用该漏洞。在补丁释出前，微软建议用户禁用 Windows Explorer 的 Preview Pane 和 Details Pane，或禁用 WebClient 服务，重命名 ATMFD.DLL。采用这些权益方法可能会导致其它问题。

　　**编程随想注：** 　　这个漏洞的危险之处在于——它可以通过“Windows 资源管理器”的【预览】功能触发。 　　假设攻击者通过某种方式（邮件、IM、网站下载 ......），给了你一个恶意的【数据文档】。当你在“资源管理器”中选中该文件，“资源管理器”就会在右侧的“预览窗格”显示该文件的内容。这时候，漏洞就已经触发了。 　　换句话说，你仅仅只是【选中】该文件，还没有用任何软件打开它，攻击代码就已经激活了。 　　提醒一下： 　　很多网民有个【误解】——误以为只有“可执行文件”才可以发动攻击/入侵。实际上【数据文件】也可以。前提是，处理数据文件的软件本身有漏洞（尤其是“可执行漏洞”），然后攻击者就可以针对该漏洞，精心构造一个特殊的数据文件，从而人为触发这个漏洞。

　　类似的案例，俺在《[如何防止黑客入侵](https://program-think.blogspot.com/2010/06/howto-prevent-hacker-attack-0.html)》系列教程的其中一篇介绍过（当时俺举了“浏览器渲染图片”的例子）

  
《[Microsoft Patches SMBv3 Wormable Bug That Leaked Earlier this Week @ ZDNet](https://tech.slashdot.org/story/20/03/12/1757223/)》

《[微软释出紧急补丁修复 SMB 漏洞 @ Solidot](https://www.solidot.org/story?sid=63808)》

  

> 本周早些时候，微软[披露](https://www.solidot.org/story?sid=63794)了 Server Message Block（SMB）v3.1.1 协议中的一个漏洞 CVE-2020-0796，允许攻击者在目标服务器和终端用户计算机上远程执行代码。SMB 服务被用于在本地和互联网上共享文件、打印机和其它资源，漏洞影响 Windows 10 v1903 和 v1909，以及 Windows Server v1903 和 v1909。漏洞[涉及到](https://news.sophos.com/en-us/2020/03/12/patch-tuesday-for-march-2020-fixes-a-very-serious-smb-bug/)一个内核驱动的整数溢出和下溢，攻击者可利用特质恶意包去触发整数溢出或下溢。微软现在释出了紧急补丁 KB4551762 修复该漏洞。

　　**编程随想注：** 　　很多 Windows 用户喜欢通过【共享目录】的方式跨主机传输文件，这个习惯不好。 　　“共享目录”这个功能是由 Windows 的某个服务（service）提供滴。这个服务本身就以【管理员权限】运行，而且它在历史上已经曝光了很多高危漏洞。这次曝光的 SMB 漏洞只不过是其中之一。也就是说，未来很可能还会再爆别的漏洞。 　　如果这个服务出现了【代码执行】的漏洞，攻击者攻击之后就能获得【管理员权限】（然后就可以干很多事情）。  
《[Mozilla Foundation Security Advisory 2020-11 @ Mozilla](https://www.mozilla.org/en-US/security/advisories/mfsa2020-11/)》

　　**编程随想注：**

  
　　Mozilla 在本月初（注：4月初）发布 Firefox 74.0.1 ＆ Firefox ESR 68.6.1 版本，修复两个高危 0day 漏洞（编号：`CVE-2020-6819` ＆ `CVE-2020-6820`）。 　　Mozilla 没有公布太多漏洞细节，但两个漏洞已经被用来发动针对性攻击。因此，那些使用 Firefox 的同学要尽快升级。

《[OpenBSD 建议 Firefox 用户切换到 ESR 版本 @ Solidot](https://www.solidot.org/story?sid=63243)》

  

> Firefox 本周早些时候（注：1月初）紧急释出更新 Firefox 72.0.1 和 Firefox ESR 68.4.1，修复了一个正被利用 0day 漏洞。OpenBSD 开发者表示他们不会更新稳定版分支，建议其用户切换到 ESR 版本（扩展支持版）。  
> OpenBSD 开发者给出的理由，由于依赖问题（如 cbindgen 和 rust），给 Firefox 打补丁太复杂了，所以稳定版本不会得到更新，因此正被利用的漏洞仍然存在，但 ESR 版会得到更新，开发者建议用户切换到 ESR 版本。

　　**编程随想注：** 　　俺在如下博文中建议：注重安全性的 Firefox 用户，应该使用【ESR】版本。并分析了 ESR 的安全优势。

《[基于安全考虑，如何选择及切换 Firefox 版本？](https://program-think.blogspot.com/2018/10/How-to-Choose-Firefox-Version.html)》

  
《[Sudo 漏洞让非特权用户获得 root 权限 @ Solidot](https://www.solidot.org/story?sid=63429)》  

> UNIX 和 Linux 操作系统广泛使用的工具 Sudo 又发现了一个高危漏洞，这个漏洞在启用了 pwfeedback 的系统中很容易利用。漏洞编号 CVE-2019-18634，是一个堆栈缓冲溢出 bug，影响 v1.7.1 到 v1.8.25p1，能通过管理员权限触发，而在启用了 pwfeedback 的操作系统中，该漏洞让非特权用户很容易通过缓冲溢出获得 root 权限，不需要攻击者有 Sudo 使用权限。在 Sudo 上游版本中，pwfeedback 没有默认启用，但在下游发行版如 Linux Mint 和 Elementary OS 中，pwfeedback 被默认启用了。Ubuntu 不受影响。该漏洞是在2009年被引入到 Sudo 中的，直到2018年释出的 v1.8.26b1，受影响的系统应尽可能快的更新到 v1.8.31。

　　**编程随想注：** 　　3个月前（2020年1月）的那篇《近期安全动态和点评》，俺已经聊过 sudo 的另一个高危漏洞。 　　在不到半年时间内，sudo 连续爆了两个非常致命的漏洞——对攻击者而言，这2个漏洞很容易利用，而且都能实现【提权】。 　　这样的苗头挺危险，很可能预示着——sudo 这个软件包内部还有其它一些高危漏洞没被发现。

　　有鉴于此，你或许要考虑：【不装或卸载】这个软件包。在需要切换用户权限时，改用 `su` 命令。当然啦，`sudo` 命令在很多场合比 `su` 命令更方便。因此，你需要作出一些取舍。

  
《[OpenWRT 使用 HTTP 连接传输更新 @ Solidot](https://www.solidot.org/story?sid=64000)》  

> 安全研究员报告，流行的路由器发行版 OpenWRT [容易受到远程代码执行攻击](https://arstechnica.com/information-technology/2020/03/openwrt-is-vulnerable-to-attacks-that-execute-malicious-code/)，原因是它的更新是通过未加密渠道传输的，其数字签名验证很容易绕过。OpenWRT 被广泛用于路由器和其它嵌入式系统，安全研究员 Guido Vranken 发现它的更新和安装文件是通过 HTTP 连接传输的，容易受到中间人攻击，攻击者可以用恶意更新文件去替换合法更新文件。除此之外，它的数字签名检查和验证也很容易绕过，验证函数 checksum\_hex2bin 存在 bug，在输入字符串前加空格可绕过检查，该 bug 是在2017年2月引入的。组合这两个弱点攻击者可以向设备发送恶意更新并自动安装。OpenWRT 维护者已经释出了更新部分修复了问题。

　　**编程随想注：** 　　上述安全漏洞会影响到那些玩“路由器翻墙”的同学。 　　OpenWRT 以【明文】的 HTTP 协议进行升级，这已经很冒险了；然后“验证机制”还存在缺陷 :( 　　如果攻击者能监控你的网络传输，以上两点堪称完美组合。  
《[Ghostcat 漏洞影响过去13年发布的所有 Apache Tomcat 版本 @ Solidot](https://www.solidot.org/story?sid=63676)》  

> Ghostcat 漏洞[影响](https://www.zdnet.com/article/ghostcat-bug-impacts-all-apache-tomcat-versions-released-in-the-last-13-years/)过去13年发布的所有 Apache Tomcat 版本，该漏洞允许攻击者控制系统。Ghostcat 是中国安全公司长亭科技发现的，存在于 Tomcat AJP 协议中，攻击者通过 Tomcat AJP Connector 可以读取或包含 Tomcat 上所有 webapp 目录下的任意文件，例如可以读取 webapp 配置文件或源代码。此外在目标应用有文件上传功能的情况下，配合文件包含的利用还可以达到远程代码执行的危害。

　　**编程随想注：** 　　这个主要影响 Web 服务端。与普通用户没啥关系。  
  
　　**编程随想注：**  
　　不晓得“WebAssembly”的同学可以先看维基百科的“[这个页面](https://zh.wikipedia.org/wiki/WebAssembly)”。 　　这玩意儿已经在去年（2019）成为 W3C 的标准。也就是说，它成为继“HTML、CSS、JS”之后的第4种“标准化的 Web 语言”；也是继 JS 之后的第2种“标准化的 Web 编程语言”。 　　有了它，程序员可以使用其它编程语言编写 Web【前端】应用，然后使用编译器把代码编译成 WebAssembly 并部署到网站上。 　　它的【好处】至少包括： 1. 要想编写（标准化的）Web 客户端应用，可以使用各种语言（以前只能用 JS） 2. WebAssembly 类似于某种“字节码”，浏览器执行它的速度比执行 JS 要快很多 　　有好处当然也有坏处：因为 WebAssembly 是面向机器，而不是面向人。要理解某个页面上的一坨 WebAssembly 代码是用来干啥，就很困难——“理解 WebAssembly 代码”比“理解混淆后的 JS 代码”还要难。 　　因此，某些动机不良的人，就会使用 WebAssembly 来干一些动机不良的事情。具体参见如下这篇报道：

《[Half of the websites using WebAssembly use it for malicious purposes @ ZDNet](https://www.zdnet.com/article/half-of-the-websites-using-webassembly-use-it-for-malicious-purposes/)》

  

> two categories of Wasm code stood out as inherently malicious. The first category was WebAssembly code used for cryptocurrency-mining. These types of Wasm modules were often found on hacked sites, part of so-called cryptojacking (drive-by mining) attacks.
> 
> The second category referred to WebAssembly code packed inside obfuscated Wasm modules that intentionally hid their content. These modules, the research team said, were found part of malvertising campaigns.

  
  
　　**编程随想注：**  
　　Bruce Schneier 是信息安全领域的大牛（搞密码学的应该都知道他）。他发了一篇博文《[5G Security @ Schneier](https://www.schneier.com/blog/archives/2020/01/china_isnt_the_.html)》，谈“5G 网络的安全问题”。开篇就点到了咱们天朝（中国公司会迫于政府压力，在网络设备中内置后门）。然后他又说：即使完全禁止中国公司参与 5G 网络，依然是【不够】滴。 　　在文章的后续部分，他指出了 5G 网络可能会有如下三大问题：

**问题1——5G 标准太复杂**

首先，这会导致软件的实现也太复杂，软件代码一旦复杂，潜在的漏洞就更多，也更难发现/修复。 其次，这会导致软件对标准协议的实现不够完全（只是【部分实现】了协议），同样会导致安全问题。

**问题2——向后兼容性**

熟悉网络攻击的同学，应该听说过【降级攻击】。这类攻击经常出现在“TLS/SSL、Wi-Fi、移动通讯网络”之类的场景中。 由于 5G 网络必须大量兼容 4G 协议，攻击者可以采用某种技巧，诱导设备降级到 4G 协议，然后再利用 4G 协议的弱点。

**问题3——5G 标准中，很多“安全选项”不是强制滴**

这个要由“标准委员会”来背锅。由于标准中的一些安全选项属于【可选】选项（非强制性），设备制造商通常不去实现它们。 （对设备制造商而言）实现的选项越少，开发就越简单，开发成本也越低。另外，很多设备制造商还面临竞争压力，为了让产品尽快上市，他们倾向于不完成那些【可选】的协议选项。  
《[Attackers Can Bypass Fingerprint Authentication With an 80 Percent Success Rate @ Slashdot](https://it.slashdot.org/story/20/04/08/2020202/)》

《[Fingerprint cloning: Myth or reality?](https://blog.talosintelligence.com/2020/04/fingerprint-research.html)》

  

> **What's new?** 3-D printing technologies made it possible for anyone to create fake fingerprints. But not only that it also made it possible, with the right resources, to be done at scale. Moreover, with the democratization of the usage of fingerprint authentication, the impact of biometric data copies is even bigger than in the past. We applied our threat models to mobile phones, laptops, padlocks and USB pen drives.
> 
> **How did it work?** We created copies using three different methods, which were defined according to the defined threat profiles. A mold was created using a 3-D printer, which was then used to recreate the fingerprint with textile glue.
> 
> **So what?** Fingerprint authentication is now in common usage, on all kinds of devices. However, its reliability is not the same on all devices. Organizations need to be aware that the security of fingerprint authentication is not secure, despite common assumptions. This means that depending on the threat profile of each user, it may not be advisable to use it. In reality, some companies have the same reliability as they had six years ago. This means that with the advances of technologies like 3-D printing, it's now even easier to defeat them.

　　**编程随想注：** 　　不光是“指纹解锁”不靠谱，“刷脸解锁”也不靠谱。更进一步，汽车的“无线钥匙”也不靠谱（已经有很多破解的案例）。 　　这几样技术的共同点在于——它们都提供了“便捷性”，而代价是牺牲了“安全性”。 　　很多时候，你需要进行某种【取/舍】。  
《[Google 将限制 Android 应用在后台访问地理位置数据 @ Solidot](https://www.solidot.org/story?sid=63607)》  

> Google [宣布](https://www.zdnet.com/article/google-to-put-a-muzzle-on-android-apps-accessing-location-data-in-the-background/)打击滥用系统权限访问不必要地理位置数据的 Android 应用。从今年五月开始，Google 将要求所有 Android 应用开发者更新应用，Android 应用只有在需要地理位置信息的情况下才能请求访问此类信息。Google 将逐个审查每一个应用，如果应用请求访问地理位置数据但不在应用中立即使用 Google 会将其从应用商店 Play Store 下架。Google 表示会审查自己的应用。此举旨在打击悄悄收集地理位置数据的应用，此类的后台地理位置数据在收集后会出售给分析公司和广告商。从8月3日起，Google 计划评估每一个新递交的应用，检查是否请求访问后台地理位置数据，是否确实需要这一数据才能工作。

  
  
《[政府如何限制互联网网速 @ Solidot](https://www.solidot.org/story?sid=63785)》  

> 相比切断互联网，限制互联网网速更隐秘更难以察觉和确认。印度去年切断了克什米尔邦的互联网接入，至今没有完全解除。此事广为人知。 但没有多少人知道的是约旦政府限制了 Facebook live 直播服务，如果它屏蔽 Facebook 那么确认起来很简单，如果它让网民难以直播视频，那么网民可能只会以为某个线路发生了故障。
> 
> [政府有很多方法去限制网速](https://netzpolitik.org/2020/jordan-throttles-not-blocks-internet-access-shutdowns-keepiton/)：带宽管理/流量控制和策略；QoS(Quality of Service) 可以有效的降低特定通信协议的流量；Inline DPI(Deep Packet Inspection) 可用于引入延迟；NIC (Network Interface Card) /端口分区 可用于影响所有流量；路由寻径可路由流量通过更长或容量更低的网络端点去限制网速。

　　**编程随想注：** 　　如今朝廷对付 Github 的手法也类似。前几年俺在博文及评论区聊过：GFW 会故意产生“传输质量劣化”的效果。 　　另外，当年还没有彻底封杀 Gmail 之前，GFW 也用这招来对付 Gmail。  
《[俄罗斯和 Telegram 之间的封锁和反封锁 @ Solidot](https://www.solidot.org/story?sid=63255)》  

> 在混沌俱乐部年会上，软件开发者 Leonid Evdokimov [回顾了](https://media.ccc.de/v/35c3-9653-russia_vs_telegram_technical_notes_on_the_battle)俄罗斯政府和流行消息应用 Telegram 之间史诗性的封锁和反封锁。 2018年4月，因为 Telegram 拒绝遵守法庭命令交出加密密钥，俄罗斯政府下令对其进行屏蔽，第一天有400万 IP 被封，第二天有1600万 IP 被封，最多有1900万 IP 被封。俄罗斯封掉了云服务商如 Amazon、Google、Microsoft、DigitalOcean 和 Hetzner，涉及了 0.5% 的 IP 地址空间，试图向施压云服务商，让 Telegram 成为这些企业不受欢迎的人。俄罗斯还不小心封掉了本国互联网服务如 VKontakte 和 Yandex 的 IP 地址。
> 
> 尽管政府否认，但附带损伤是巨大的。到4月底封杀力度开始减弱，到6月8日封杀的 IP 地址减少到400万，而在期间 Telegram 一直能在俄罗斯境内工作。俄罗斯被观察到使用主动探测去识别代理服务器，主动探测已经日益成为一种常用的监测和识别代理服务器的方法。

  
  
《[TikTok 告诉内容审查团队过滤“丑人/穷人/残疾人”上传的视频 @ Solidot](https://www.solidot.org/story?sid=63851) 》  

> The Intercept 援引内部文件[报道](https://theintercept.com/2020/03/16/tiktok-app-moderators-users-discrimination/)，流行短视频应用 TikTok 明确指示内容审核团队过滤“丑人、穷人和残疾人”上传的帖子。文件还要求内容审核团队审查直播中的政治言论，惩罚损坏国家荣誉或被禁止直播的国家机构如警察的用户。 今天的社交平台都会向新用户推荐内容，但内容推荐算法通常是一个秘密。TikTok 文件的原始版本是中文，之后翻译到英文，这些指示与内容推荐有关。它建议审核团队移除体型异常、过胖或过瘦、面部表情丑陋或面部畸形的用户内容，因为人长得难看视频也没有多少吸引力，不值得推荐给新用户。文件还建议：移除拍摄环境简陋不吸引人的视频。
> 
> TikTok 发言人承认文件的真实性，但表示大部分指示要么不再使用要么从未真正使用过。直播政策文件是在2019年创建的，至少在2019年使用过。

  
  
《[国内下载站提供的开源编辑器被发现捆绑了恶意代码 @ Solidot](https://www.solidot.org/story?sid=64075)》  

> 安全公司报告，国内下载站西西软件园提供的开源编辑器 Notepad++ 被发现捆绑了恶意代码，而这个恶意脚本代码与勒索软件 WannaRen 有关联，该勒索软件可能通过国内下载站进行传播。在中文搜索引擎百度搜索 Notepad++，排在前几位的都是下载站，而不是官网 notepad-plus-plus.org，如果下载站的版本存在恶意代码，那么可能会有很多中国用户受到影响。

  
《[2345旗下的下载站被发现传播木马 @ Solidot](https://www.solidot.org/story?sid=63757)》  

> 安全公司火绒报告： 2345旗下“多特下载站”的下载器（所谓的“高速下载”）正在实施传播木马程序的恶意行为。用户下载运行该下载器后，会立即被静默植入一款名为“commander”的木马程序，该木马程序会在后台运行，并根据云控配置推送弹窗广告和流氓软件。即使用户关闭下载器，“commander”仍然会一直驻留用户系统。同时，该下载器还会释放病毒劫持用户浏览器首页，用以推广广告程序。
> 
> 截至目前，被“commander”木马程序静默推广的软件共有9款，包括趣压、拷贝兔、小白看图等，且这些被静默安装的软件与“commander”木马程序系同源流氓软件。它的一个模块被发现还检测当前 IP 所在城市，被检测的城市包括：北京、上海、广州、珠海、杭州、西安、马鞍山、苏州、武汉、天津、合肥。

　　**编程随想注：** 　　那些使用 Windows 的同学，如果你想用某款第三方软件，要注意如下几点： 　　1、只用那些成熟度足够高，而且口碑足够好的； 　　2、总是从【官网】下载； 　　3、（即使从官网下载）下载完成之后，再校验一下 exe 的数字签名。 　　有些软件虽然 exe 没有自带数字签名，但会在官网公布该 exe 的散列值（哈希值）或者 exe 文件对应的数字签名文件，以让你进行校验。 　　如果某个软件既没有自带数字签名，官网页面也没提供任何校验信息，你就得怀疑它是否符合“第1条”（成熟度是否足够高） 　　引申阅读：

　　《[扫盲文件完整性校验——关于散列值和数字签名](https://program-think.blogspot.com/2013/02/file-integrity-check.html)》

  
《[奇虎360研究员披露：Shadowsocks 流密码重定向攻击 @ Solidot](https://www.solidot.org/story?sid=63529)》  

> 奇虎360的一位安全研究员[披露了](https://github.com/edwardz246003/shadowsocks)流行 SOCKS5 代理 Shadowsocks 的流密码重定向攻击漏洞。流密码是一种对称加密算法，加密和解密双方使用相同伪随机加密数据流作为密钥，明文数据每次与密钥数据流顺次对应加密，得到密文数据流。流行的流密码算法包括 ChaCha、RC4、A5/1、A5/2、Chameleon、FISH、Helix 等。  
> 研究人员发现 Shadowsocks 协议存在漏洞，会破坏流密码的保密性。利用重定向攻击，被动攻击者可以轻松解密所有 Shadowsocks 的加密数据包。中间人攻击者还能实时修改流量，就好像加密根本不存在。受影响的版本包括 shadowsocks-py、shadowsocoks-go 和 shadowsocoks-nodejs；shadowsocks-libev 和 go-shadowsocks2 不受影响，研究人员还建议使用 AEAD 加密算法。漏洞是在2018年12月发现的，2019年3月发布了概念验证攻击。

　　**编程随想注：** 　　看到这个新闻，俺又要再次唠叨【基于 Tor 的双重代理】（关于这招，俺已经唠叨了不止5年）。 　　以 Shadowsocks 为例，如果你使用 Tor over Shadowsocks 的方式，即使 Shadowsocks 的协议本身出现某种漏洞（比如上述这种），导致攻击者破解了 Shadowsocks 的流量；攻击者看到的也只是【强加密】的 Tor 流量。换句话说，攻击者依然【看不到】你真实的上网流量。 　　另， 　　某些网友猜测：去年（2019）六四前后，很多人抱怨 Shadowsocks 失效。可能与上述漏洞有关。 　　引申阅读：

　　在《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》系列教程的其中一篇，介绍了【多重代理】的玩法。

  
《[SIM Swappers Are Using RDP To Directly Access Internal T-Mobile, AT&T, and Sprint Tools @ Slashdot](https://it.slashdot.org/story/20/01/10/2218239/)》

《[Academic Research Finds Five US Telcos Vulnerable To SIM Swapping Attacks @ Slashdot](https://yro.slashdot.org/story/20/01/13/1554235/)》

《[PayPal and Venmo Are Letting SIM Swappers Hijack Accounts @ Slashdot](https://news.slashdot.org/story/20/04/06/1852214/)》

《[一文看懂巨鲸被盗2亿元数字货币始末，找回几无可能 @ 36氪](https://36kr.com/p/5294183)》

　　**编程随想注：**

　　在半年前（2019年3季度）的博文，俺已经提到过这种攻击手法。当时 Twitter CEO 的推特帐号被劫持，攻击者用的就是这招。从上述几篇报道来看，如今这种攻击越来越普及（越来越危险）。 　　这类攻击的危险性在于——如今很多帐号都绑定手机，并且可以通过手机来【重置密码】。因此，攻击者一旦实现了【SIM 卡劫持】，就可以控制你的【手机号】，进而控制所有绑定到该手机的网络帐号。

　　关于这种攻击手法的【原理】，请参见博文《[近期安全动态和点评（2019年3季度）](https://program-think.blogspot.com/2019/09/Security-News.html)》

  
《[微软 Github 疑被中间人攻击 @ 月光博客](https://www.williamlong.info/archives/6021.html)》  

> 今天（注：3月26日），有很多中国网民反馈，从中国的 IP 访问知名代码托管平台微软 Github.com、Github.io、Github Pages 等网站会加载一个无效的证书，使用国外的 IP 访问则加载正常的证书，疑似该域名遭到了中间人攻击。 ...... 目前经测试 DNS 系统解析是完全正常的，例如，pages.github.com 的 IP 地址解析并未出现问题，从中国地区解析的 IP 为185.199.111.153，是属于 Github 的 IP 地址。受影响的主要是部分地区用户但涉及所有运营商。
> 
> 由于攻击者使用的自签名证书不被所有操作系统以及浏览器信任，因此用户访问这些网站时可能会出现安全警告。

　　**编程随想注：**  
　　“中间人攻击”洋文称作“MITM”，维基百科的介绍在“[这里](https://zh.wikipedia.org/wiki/%E4%B8%AD%E9%97%B4%E4%BA%BA%E6%94%BB%E5%87%BB)”。 　　根据某些网友当天的网络分析，这次事故很大可能是 GFW 搞的。类似的情况已经不是第一次出现了（前几年也有，也是短暂出现了一下） 　　不排除 GFW 在进行某种 MITM 的技术尝试，或者在尝试的过程中出现了某种失误，导致上述现象。 　　这次事件给大伙儿敲了警钟—— 很多使用 Github 的网民发现异常是因为——浏览器显示“证书警告”。 浏览器显示“证书警告”是因为——这次攻击使用的是一个随便生成的 CA 证书（浏览器当然不认可这种证书） 　　试想一下： 如果 GFW 真心要搞 MITM 攻击，它会使用一个很逼真的（看起来合法的）CA 证书；如此一来，浏览器就【不】显示警告信息。基本上很难察觉。

对于普通网民而言，应该尽量把操作系统中（以及浏览器中）那些【不靠谱的 CA】颁发的证书清理干净。所谓“不靠谱的 CA”，除了俺之前专门写博文点名批评的两个老流氓（[CNNIC](https://program-think.blogspot.com/2010/02/about-cnnic.html) ＆ [沃通/WoSign](https://program-think.blogspot.com/2016/09/About-WoSign.html)），至少还包括：【所有】位于朝廷具有司法管辖权的地区的 CA 机构。也就是说：处于“大陆、香港、澳门”的 CA 机构都【不能】信任。

  
　　“清理流氓 CA”的招数有个缺点——容易漏网。因为每隔几年，可能又会有某个天朝的 CA 机构的根证书被加入到“Windows 或 Android 或 iOS 或 Mozilla”的信任列表中。如果你对安全性的要求【非常高】，应该采用俺在《[近期安全动态和点评（2019年1季度）](https://program-think.blogspot.com/2019/04/Security-News.html)》中介绍的【证书白名单策略】。考虑到某些读者比较健忘，俺把当时的招数再重新贴出来：  

> 　　你在某个【专用】的浏览器实例中操作特别重要的帐号（也就是说，这个实例只操作这个帐号，不访问其它网站）然后在该实例中采用【证书白名单策略】——只留下这个帐号对应网站所需的 CA 证书，其它证书全部禁掉。当然啦，你还需要保留一个【通用】的实例，用来进行日常的上网浏览。如此一来，假设你有 N 个重要帐号，需配置 N + 1 个实例。 　　浏览器的选择： 　　Chrome 和 Firefox 都可以创建“多实例”，但 Chrome 有个【缺点】——它用的是操作系统的证书。因此，Chrome【无法】使用刚才介绍的招数。
> 
> 　　相比之下，Firefox 使用的是【自带证书】。因此，你可以创建多个 Firefox 实例，并通过配置让每个实例的证书都采用各自的【白名单策略】。

  
  
《[俄罗斯电信劫持了 Google 和 AWS 的流量 @ Solidot](https://www.solidot.org/story?sid=64048)》  

> 上周，两百多家 CDN 和托管商的流量遭到了国有的俄罗斯电信公司的劫持。受影响的公司包括了 Google、Amazon、Facebook、Akamai、Cloudflare、GoDaddy、Digital Ocean、Joyent、LeaseWeb、Hetzner 和 Linode。俄罗斯电信公司是通过 BGP 路由通告劫持了不属于它的网络流量。BGP 劫持未必都是恶意的，很多时候都是因为人为失误导致的。同一机构频繁发生路由劫持则视为可能有恶意。最大的电信公司中国电信频繁发生过 BGP 路由劫持事故。俄罗斯电信也发生过多次。

　　**编程随想注：**  
　　在《[近期安全动态和点评（2019年3季度）](https://program-think.blogspot.com/2019/09/Security-News.html)》中，俺正好介绍“中国电信劫持美国国内的互联网流量”。如今“俄罗斯电信”的手法与“中国电信”如出一辙。 　　关于“流量劫持”的【原理】，当时俺分享了一篇文章。把那篇文章以及中文翻译，再次贴出（如下）

《[China Telecom's Internet Traffic Misdirection @ Oracle dyn](https://dyn.com/blog/china-telecoms-internet-traffic-misdirection/)》

  
《[甲骨文：中国电信误导国际互联网流量（译文） @ Submarine Networks](https://www.submarinenetworks.com/zh/internet/2018111001)》  
《[美已视中港为“一体”，禁止美台高速网缆与香港连通 @ RFI/法广](http://www.rfi.fr/cn/%E4%B8%AD%E5%9B%BD/20200410-%E7%BE%8E%E5%B7%B2%E8%A7%86%E4%B8%AD%E6%B8%AF%E4%B8%BA-%E4%B8%80%E4%BD%93-%E7%A6%81%E6%AD%A2%E7%BE%8E%E5%8F%B0%E9%AB%98%E9%80%9F%E7%BD%91%E7%BC%86%E4%B8%8E%E9%A6%99%E6%B8%AF%E8%BF%9E%E9%80%9A)》  

> 根据《华尔街日报》报道，美国官员准许 Alphabet Inc 旗下的谷歌（Google）启动与台湾连接的高速互联网光缆，但不能与香港连通，理由是存在国家安全隐患。报道指这项决定凸显出美中之间越来越紧张的关系。 ...... 报道指出，这项决定可能会终结香港作为美国互联网电缆首选目的地的主导地位，并危及正在进行的几个项目，其中包括一条由面书（Facebook）支持的连接洛杉矶和香港的光缆，以及一个由谷歌支持的连接香港和美国关岛的项目。 《华尔街日报》的报道指，美国司法部周三宣布决定时说：“许可美国和香港直接连通光缆存在重大风险，有可能严重危害美国国家安全和执法利益。”这一决定得到了美国国土安全部和国防部的支持。 中国政府部门禁止包括面书和谷歌在内的一些美国公司在中国大陆运营，但香港却可以不受限制地接入互联网，从而成为想和中国大陆建立联系的跨国公司的中转站。 华尔街日报指出，然而随着北京方面对香港的立场趋于强硬，美国官员对香港的态度也发生了变化。几个月以来，香港人一直在抵制北京方面推动香港与大陆融合的努力。
> 
> 华盛顿正在转向台湾这个自治岛屿，虽然北京方面宣称台湾是中国的一部分，但美国通过军售和非官方政治联系向台湾提供支持。

　　**编程随想注：** 　　这条光缆原计划要从美国加州一直铺设到香港，如今只到台湾。 　　结合刚才提到的“流量劫持”以及最近几年越来越升温的“中美对抗”，你或许能理解——为啥美国佬禁止新的太平洋光缆部署到香港和大陆。  
  
《[苏俄如何监听美国大使馆的打字员 @ Solidot](https://www.solidot.org/story?sid=63225)》  

> 最近出版的一本新书回顾了冷战期间美国和苏联之间的谍报战，讲述了[一段尘封已久的供应链攻击案例](https://spectrum.ieee.org/tech-history/silicon-revolution/the-crazy-story-of-how-soviet-russia-bugged-an-american-embassys-typewriters)：神秘的苏联工程师巧妙的替换 IBM 打字机零部件去监听美国大使馆打字员的打字内容，而 NSA 的电机工程师费了多年时间揭开了这一秘密。  
> 1970年代末有多名美国间谍遭到逮捕，但美国情报界不知道他们的身份是如何曝光的。首次突破来自于在（美国驻）莫斯科大使馆无意中发现的假烟囱腔内的八木天线，但天线的用途和无线发射机的下落仍然不明。NSA 工程师 Charles Gandy 对此展开了多年的寻找，他得到了里根总统的授权，将大使馆内的所有电子设备都安全打包运回美国。每个设备都被拆开，用 X 射线进行扫描。在进行了数万次扫描之后，技术人员在一台 IBM 打字机的 on/off 开关内发现了一个小线圈，Gandy 认为它充当了降压器为打印机内的东西供应低电压电。他最终发现，打印机内的有多个零件被替换了，一个外形相同的固体铝棒里面是空的，被放入了一个电路板和六个磁强计，磁强计能感知按键的移动，按键的信息被储存加密然后发送出去。

　　**编程随想注：** 　　上述这个已经是陈年往事。分享它是为了让大伙儿意识到【物理安全】的重要性——如果攻击者能够接触到你的电脑，并且在上面动手脚；那么，软件层面的任何防范都形同虚设。

　　在之前的《[近期安全动态和点评（2019年2季度）](https://program-think.blogspot.com/2019/07/Security-News.html)》中提到了【邪恶女佣】（[evil maid attack](https://en.wikipedia.org/wiki/Evil_maid_attack)）的攻击场景。这个术语就是用来描述此类攻击手法。

  
《[Intel CSME bug is worse than previously thought @ ZDNet](https://www.zdnet.com/article/intel-csme-bug-is-worse-than-previously-thought/)》

《[英特尔 CSME 漏洞比想象中的要严重 @ NOSEC](https://nosec.org/home/detail/4199.html)》

  

> 这个漏洞被标记为 CVE-2019-0090，影响了英特尔的 Converged Security and Management Engine 安全管理引擎，以前称为 Management Engine BIOS Extension（Intel MEBx）。 CSME 是所有最近的英特尔 CPU 都具有的一个安全特性。它被认为是在基于英特尔的平台上所有其他英特尔技术和固件的“加密基础”。 ...... CSME 是机器中最早开始运行的系统之一，负责对基于英特尔的计算机上装载的所有固件进行密码验证和授权。 例如，CSME 负责加载和验证 UEFI BIOS 固件和 PMC 固件（电源管理控制器）以及管理芯片组电源的组件。 CSME 也是其他 Intel 技术的“加密基础”，如 Intel EPID（增强隐私 ID）、Intel 身份保护、任何 DRM（数字版权管理）技术或基于固件的 TPMs（可信平台模块）。 换句话说，CSME 是运行在英特尔芯片组上的所有其他技术的“可信之本”。 ......
> 
> 在新发表的一项新研究中，Ermolov 表示，攻击者可以利用这个漏洞来恢复芯片组密钥，这是 root 加密密钥，可以让攻击者访问设备上的一切。

　　**编程随想注：** 　　从上述介绍可以看出——CSME 是 Intel 芯片硬件体系的【信任链之锚】。 　　据初步的研究结果，该漏洞可以被【本地利用】。也就是说，如果攻击者获得了在本地执行代码的机会，并且能够“提权”，就有可能利用该漏洞。 　　在英特尔硬件体系中，UEFI 的信任链也是基于 CSME 之上。也就是说，UEFI 的安全性并没有某些同学想象的那么好。  
《[Intel Is Patching Its 'Zombieload' CPU Security Flaw For the Third Time](https://it.slashdot.org/story/20/01/27/2126231/)》

　　**编程随想注：**

　　关于这个 CPU 漏洞，之前的某期《安全动态和点评》已经提到了。 　　为了修复该漏洞，Intel 在去年（2019）5月和11月两次放出补丁，但都【没】彻底修复。今年（2020）1月份，英特尔不得不承认：之前的补丁不够完善，攻击者仍然能利用 Zombieload 漏洞；然后发布了第三次补丁。

　　在《[近期安全动态和点评（2019年4季度）](https://program-think.blogspot.com/2020/01/Security-News.html)》一文中，俺引用了 Linux 内核维护者 Greg Kroah-Hartman 的一次演讲（如下）

  

> 稳定版内核维护者 Greg Kroah-Hartman 在欧洲开源峰会上发表主题演讲时指出，英特尔芯片的安全问题将会存在很长时间。这些被称为 MDS、RDDL、Fallout 和 Zombieland 的芯片漏洞从某种程度上说都是相同的问题或者说是相同问题的不同变种，但解决方法各不相同。举例来说，RIDL 和 Zombieload 漏洞能跨应用程序、虚拟机和安全区域（secure enclaves）窃取数据，讽刺的是：英特尔软件防护扩展（SGX）在芯片内本是保护数据安全的，结果本身却有很多漏洞。  
> Kroah-Hartman 称：为了修复每一个曝出的问题，你必须同时给 Linux 内核、CPU BIOS 和微码打上补丁。这不只是 Linux 的问题，任何操作系统都面临相同的问题。他承认 OpenBSD 给出了解决此类漏洞的最近解决方案：关闭英特尔处理器的超线程，克服带来的性能损失。Kroah-Hartman 称，你必须选择性能还是安全，而这里不存在好的选择。

　　当时 Greg Kroah-Hartman 提到了关闭英特尔处理器的超线程，这是一种玩法。 　　另一种玩法是：改用 AMD 处理器的电脑。当然啦，AMD 处理器也有不少安全问题（下面会提到），但 AMD 的安全问题比 Intel【少】很多。

　　更进一步，善于折腾的同学，甚至可以考虑那些【非】[x86 架构](https://zh.wikipedia.org/wiki/X86)的处理器（比如 ARM 之类的）。

  
《[Intel CPUs vulnerable to new LVI attacks @ ZDNet](https://www.zdnet.com/article/intel-cpus-vulnerable-to-new-lvi-attacks/)》

《[英特尔处理器新漏洞 Load Value Injection @ Solidot](https://security.solidot.org/story?sid=63784)》

  

> 研究人员披露了名叫 [Load Value Injection](https://lviattack.eu/)（LVI） 的英特尔处理器新漏洞，能窃取英特尔 SGX（代表 Software Guard eXtensions）中储存的秘密信息。LVI 与 Meltdown 和 Spectre 等类似，都属于瞬态执行利用，源自于 CPU 的一项优化技术“预测执行”。与其它瞬态执行漏洞类似，LVI 只能缓解无法修复。  
> SGX 能在内存中创建一个隔离的环境，使用强加密和硬件层的隔离确保数据和代码的安全，防止被纂改。研究人员演示了他们可以利用 LVI 漏洞窃取 SGX 保护的密钥。受影响的处理器包括了 Sandy Bridge 家族、Ivy Bridge 家族和 Haswell 家族等等，Ice Lake 不受影响。芯片巨人声称 LVI 在现实中很难利用。

  
  
《[AMD processors from 2011 to 2019 vulnerable to two new attacks @ ZDNet](https://www.zdnet.com/article/amd-processors-from-2011-to-2019-vulnerable-to-two-new-attacks/)》

　　**编程随想注：**

　　奥地利的安全研究人员新发现两种针对 AMD 处理器的攻击方式：Collide+Probe ＆ Load+Reload，两者统称为“Take A Way 攻击”。 　　类似于大名鼎鼎的 Spectre ＆ Meltdown 漏洞，这种“Take A Way”攻击依然属于【边信道攻击】。但其危险性【低于】其它那几个知名的 CPU 漏洞——因为“Take A Way 漏洞”泄漏的信息量很小（这是该漏洞的发现者自己说的）。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》（系列）  
《[如何防止黑客入侵](https://program-think.blogspot.com/2010/06/howto-prevent-hacker-attack-0.html)》（系列）  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》（系列）  
《[弃用 Chrome 改用 Firefox 的几点理由](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)》  
《[基于安全考虑，如何选择及切换 Firefox 版本？](https://program-think.blogspot.com/2018/10/How-to-Choose-Firefox-Version.html)》  
《[扫盲文件完整性校验——关于散列值和数字签名](https://program-think.blogspot.com/2013/02/file-integrity-check.html)》  
《[数字证书及 CA 的扫盲介绍](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)》  
《[近期安全动态和点评（2019年4季度）](https://program-think.blogspot.com/2020/01/Security-News.html)》  
《[近期安全动态和点评（2019年3季度）](https://program-think.blogspot.com/2019/09/Security-News.html)》  
《[近期安全动态和点评（2019年2季度）](https://program-think.blogspot.com/2019/07/Security-News.html)》  
《[近期安全动态和点评（2019年1季度）](https://program-think.blogspot.com/2019/04/Security-News.html)》

