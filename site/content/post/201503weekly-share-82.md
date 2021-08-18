---
layout: default
title: '每周转载&#65306;关于 GitHub 和 GFW 的 PK&#65288;第2季&#65289;'
date: None
author:
    display_name: 
---

　　如果你是个程序员，或者比较关注翻墙的动态，或许你已经听说——最近一周，GFW 又跟 GitHub 干上了。  
　　早在2年前，GitHub 已经跟 GFW PK 过一次了。当时俺还发了一篇《[每周转载：关于 GitHub 和 GFW 的 PK](https://program-think.blogspot.com/2013/02/weekly-share-39.html)》。所以，本次的交锋，称为“第2季”。  
[Large Scale DDoS Attack on github.com @ GitHub Blog](https://github.com/blog/1981-large-scale-ddos-attack-on-github-com) （编程随想注：这是 GitHub 官方博客对此事的说明，俺摘录其中部分文字）

> We are currently experiencing the largest DDoS ([distributed denial of service](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack in github.com's history. The attack began around 2AM UTC on Thursday, March 26, and involves a wide combination of attack vectors. These include every vector we've seen in previous attacks as well as some sophisticated new techniques that use the web browsers of unsuspecting, uninvolved people to flood github.com with high levels of traffic. Based on reports we've received, we believe the intent of this attack is to convince us to remove a specific class of content.  
> We are completely focused on mitigating this attack. Our top priority is making sure github.com is available to all our users while deflecting malicious traffic. Please watch [our status site](https://status.github.com/) or follow [@githubstatus](https://twitter.com/githubstatus) on Twitter for real-time updates.

  
[China's national firewall hijacks JavaScript to DDoS GitHub @ slashdot.org](https://slashdot.org/submission/4299157/chinas-national-firewall-hijacks-javascript-to-ddos-github) （编程随想注：这是著名极客网站 Slashdot 对此事报道）

[中国劫持百度广告流量攻击GitHub @ 纽约时报](https://cn.nytimes.com/china/20150331/c31hack/)

[GitHub under ongoing DDoS attack @ Ycombinator News](https://news.ycombinator.com/item?id=9284226)

（编程随想注：这是老外在 Ycombinator 上的讨论，挺热烈滴。以下这段是出口转内销，介绍了朝廷对 GitHub 进行 DDOS 攻击的4个阶段）

> I saw this on Weibo earlier, NOT from a trusted source. But the first and third rounds have been confirmed. 第一轮外域JavaScript，一个alert防住； 第二轮外域img，Referer挡外面； 第三轮GitHub Pages被D； 第四波正在进行，是TCP SYN Flood攻击。 My translation: The first round was cross-domain JavaScript, stopped with an "alert()". Second round was cross-domain <img>, stopped with referrer. Third was DDoS-ing GitHub Pages.
> 
> Fourth is the ongoing TCP SYN Flood attack.

  
[对GitHub的DDoS攻击在继续，百度否认与其有关 @ Solidot](https://www.solidot.org/story?sid=43500)

[对GitHub的大规模DDoS攻击已超过80个小时 @ Solidot](https://www.solidot.org/story?sid=43506)

  

> 对GitHub的大规模DDoS攻击已超过[80个小时](https://status.github.com/messages?latest)，攻击者此举显然是为了迫使GitHub[移除](http://weibo.com/5488749285/CaGZLsvc0?from=page_1006065488749285_profile&wvr=6&mod=weibotime)反审查项目Greatfire。DDoS攻击产生的史翠珊效应（Streisand effect）反而让更多人知道了Greatfire。攻击者先后使用了四种DDoS技术[攻击](https://news.ycombinator.com/item?id=9284226)GitHub（未完全确认）：第一波是创造性的劫持百度JS文件利用中国海外用户的浏览器每2秒向托管在GitHub上的两个反审查项目发出请求，这一手段被GitHub用弹出JS警告alert()防住；第二轮是跨域 <img>  攻击，被GitHub检查Referer挡住；第三波是DDoS攻击GitHub Pages；第四波是正在进行中的TCP SYN洪水攻击，利用TCP协议缺陷发送大量伪造的TCP连接请求，让GitHub耗尽资源。对于Greatfire所实现的[collateral freedom](https://openitp.org/pdfs/CollateralFreedom.pdf)（PDF），也有许多人对此表达了不满，Greatfire的做法让一些CDN服务商遭到了封杀，而GitHub是最新的受害者。

  
[中国对GitHub发动的是Man-on-the-side攻击 @ Solidot](https://www.solidot.org/story?sid=43530)

[寻找DDoS攻击GitHub的幕后组织 @ Solidot](https://www.solidot.org/story?sid=43569)

  

> 为了防止数据在网络中无限循环，名为[存活时间（Time to live，TTL）](https://en.wikipedia.org/wiki/Time_to_live)或跳数限制（hop limit）的机制限定了数据包的寿命。当TTL=0，数据包将被丢弃。大多数系统发送IP包时都是从TTL=64开始，如果该数据包抵达你时TTL=46，那么你和发送者之间经过了18跳（64-18=46）。在对GitHub发动大规模DDoS攻击时，攻击者劫持了百度的JS文件。如图所示，百度服务器所发送数据包的TTL=64，第一次抵达用户浏览器时TTL=42（不同位置这一数字会有所不同），经过了22跳，用户发回的请求包的TTL值也是64，但接下来的响应包的TTL值非常怪异，显然有个中间人设备注入了伪造包。如何识别这个中间人设备的IP？你可以借助Traceroute工具。利用该工具发送TTL=1，2，3....的请求包，因为TTL的值很小，在到达目的地前跳数就会变为零被沿路的路由器抛弃，而此时路由器会使用其IP地址发回时间超时的报文，如果某两跳之间发现了伪造包，那么注入设备应该就藏在其中。一位研究人员用定制Traceroute工具测试发现，注入设备位于第11跳和第12跳之间，通过查询第12跳设备的IP地址，作者发现它[位于中国联通骨干网](http://blog.erratasec.com/2015/04/pin-pointing-chinas-attack-against.html)，因此得出了中国政府与此有关的结论。

上述几篇，是国内极客网站 Solidot 对此事的报道。

[中国翻墙者被劫持为黑客 Github遭史上最大攻击 @ 泡泡网](https://pao-pao.net/article/404)

　　很显然，是咱们天朝大名鼎鼎的 GFW 干的。 　　这可【不是】冤枉它——从前面转载的几篇，已经能看出是 GFW 所为。另外，你还可以看文本的后续章节——★对“攻击手段”的技术分析——里面有各路网友的分析。 　　那么，对 GitHub 进行 DDOS 的动机何在捏？ 　　此次攻击针对的页面是 https://github.com/greatfire。该页面是 GreatFire 在 GitHub 上的主页。攻击者这么做，就是为了让 GitHub 的服务器不堪重负，从而逼迫 GitHub 移除 GreatFire 的相关内容（甚至注销该帐号）。 　　为啥 GreatFire 会跟 GFW 结仇捏？最大的一个原因是：GreatFire 最近几年开始提供墙外知名网站的【免翻墙镜像】（很多读者应该知道，俺博客的镜像也是其中之一） 　　以下是 GreatFire 目前提供镜像的网站列表：

> Google 搜索 纽约时报 BBC 德国之声 自由微博 中国数字时代 博讯网 泡泡网 编程随想
> 
> 人民监督网

　　以下是 GreatFire 发出的呼吁：

> GreatFire.org：  
> 既然GFW想让全球的中文用户DDOS我们的网页 https://github.com/greatfire/wiki 大家把这个转给朋友访问吧。

　　到目前为止，GitHub 并没有删除 GreatFire 帐号的内容。所以，朝廷的企图，暂时还没有得逞。 　　在接下来的几天，咱们还要继续关注，看看 GitHub 的骨气，到底有多硬？ 　　虽然 GitHub 暂时还没有向朝廷妥协，但是 DDOS 攻击，已经给 GitHub 造成了一些影响。最近几天，你如果访问 GreatFire 在 GitHub 的主页（https://github.com/greatfire），会看到如下报错信息：

> ![不见图 请翻墙](https://lh4.googleusercontent.com/jkC-9LMR98na1gzs80ylDHF4P_LbUkUhqUTrcRKCugBrmziblg_05fQbutM_-Rd_k0dSqzSOE6OhEEA7JNPfOtPm7pzvo6KKM7hWSRhWgXS0kNRRoYEUOPiOZ4hLRfrEZLBIs-3y-A)
> 
> Something went wrong and we cannot service your request.
> 
> Sorry about that. Please try refreshing and contact us if the problem persists.

　　另外还有墙内读者给出了 GitHub 访问速度受到的影响。

> 比特客栈的寻行数墨： 再次强调，Github没有因为DDoS封中国的IP。 但由于攻击，整个线路的访问速度受到很大影响，某程度上GFW做到了它们想做的事情。 而且这次，没有李开复来救火。
> 
> ![不见图 请翻墙](https://lh5.googleusercontent.com/8hCPo4cNgjhFxZ8ObP-zCj_qCEWAFRNV-nVYcrgCt1zpoVfnQ4oxukxQZPvnaixMvwu7u3cMj53mEDfz-9CseNMUiNJ5UOOKeAWc7gK0vAn0gpqPWCW8aM5KiOtwh0jsW3zXgSAGyg)

　　如果拿 GitHub 跟全球顶级的 IT 公司作一下对比，会发现它在对抗 DDOS 方面，还是有欠缺。以下是某知名博主的评论，谈及“朝廷御用骇客”攻击 Google 和 Facebook 遭遇的尴尬挫败。

> Eric Xu, PhD (徐宥)： 硅谷小道消息。某国政府不是没 DDoS 过G和F。 这两家公司的 CDN, EdgePOP 和负载均衡做得很好，以至于某国政府无法伤害。 话说某国政府上次搞的时候，搞完好久G才发现，因为流量还没凯特王妃结婚直播时候高。 这种没回应的攻击好伤人家感情的，从此没脸再搞这些大鳄。 Eric Xu, PhD (徐宥)： 依然小道消息。搞 F 的时候也是不疼不痒，负载均衡系统直接吸收了流量。 相比之下有次 Facebook 客户端程序员出了个大Bug, 自家客户端不断访问某资源以至于自己 DDoS 自己。
> 
> 除此外其他攻击都没达到类似量级，也就无所谓了。

　　曾经有好几个读者问俺：为啥要选择 Google 的 Blogger/blogspot 作为博客平台？为啥不用 WordPress 或者干脆自己在 VPS 上搭建博客。 　　通过这次事件，你或许就能体会到——俺选择 Blogger 搭建博客的优势（基本不用担心朝廷的 DDOS 攻击）。像俺这种长期抹黑朝廷的反党分子，对 DDOS 攻击还是需要防范于未然。 推倒柏林墙： 自从GitHub反击之后我上国内网站就老是跳出恶意脚本警告，忍无可忍只好把百度的JS给屏蔽了（我之前从来不用广告屏蔽软件）。 上GitHub看了一眼貌似人家屁事都没有，根本没给GFW击沉，百度就这么白白做了炮灰，真是凄凉。 Shippo7： 百度网盘的页面有脚本正在ddos github，录了一段视频 https://www.youtube.com/watch?v=l6eAtcwT5Pc 比特客栈的寻行数墨： 如果你没能测出这次基于百度CDN劫持的Github DDoS，别担心，这有个视频演示。 https://www.youtube.com/watch?v=l6eAtcwT5Pc 比特客栈的寻行数墨： 值得一提，这个视频也演示了Github对策攻击的高明之处—— 在你点击确认alert或无视alert之前，浏览器的js会block，不再执行，也就有效降低了自动发请求的次数。 Tianran Ding： 访问新浪网的某些JS也被劫持夹带代码去攻击 Github http://news.sina.com.cn/w/2015-03-29/133631657611.shtml … @GreatFireChina

![不见图 请翻墙](https://lh6.googleusercontent.com/fScD4D9uWaQ1RUUjH2qS3ZKt6x4l3UdFPVm_on75FUXfxzytIRDfoQofHz4gEqHCS9XwHTJ3hkF8YFSpZa6NCGvGaMSn7-ZcJSM6oJBVDgVW9jUwBLwvhA4WRnbS50uDfxDkh7j3EA)

xxoo： @dingtianran @iaskfq @GreatFireChina RT @bitinn: 建议将“DDoS attack has shifted again...”翻译为“强奸犯又换了一个姿势”。 余晟： GFW本着“利用和破坏正常信任关系”的精神，突破了恶心下作的底线 wzyboy： GFW 利用百度 CDN 来 DDoS GitHub，这「创意」 -\_- 陈少举： @cxqn @yegle @Arctosia @wenyunchao https://twitter.com/mac\_zhou/status/581321375773667328 从TTL的变动来看，极高的可能性是GFW引起的。相同IP的通信不可能发生剧烈的TTL变化。 Mac\_Zhou： @chenshaoju @cxqn @yegle @Arctosia @wenyunchao 不排除百度的可能性。 TTL只相差了3，这说明百度服务器和这台中间设备可能靠得很近。 当然更有可能不是伪造报文，而是直接在线路中插入的。 Mac\_Zhou： 对@yegle 发现的百度JS被植入greatfire的现象进行了抓包跟踪，正常百度服务器返回给我日本VPS的TTL为51， RESP返回HTTP 200 OK的报文的TTL是 47，可以确定的是有中间设备对VPS发了伪造报文。

![不见图 请翻墙](https://lh3.googleusercontent.com/rw8AwvSQbbhCi5cvyYjDRRSH_LkYlE-A02GXOTuWo9QsH2jvxUgWARRCvWsqkkOBIw5GBfibGWzoL23_M3LX3WM7O3YLaX4o1ZLkqeW444QGNDHohJKsffrFXHeL1BqW2m5CdfNUTQ)

Danny Chen： @yegle @Arctosia @chenshaoju @wenyunchao 可以直接说是操纵众多浏览器向github发起请求，因而造成DDoS。还不能确认是Gfw所为，要仔细实验排除百度公司所为的可能。 北风（温云超, Yunchao Wen）： @mac\_zhou @chenshaoju @cxqn @yegle @Arctosia 百度自己出面干这种事的可能性不大。 陈少举： @wenyunchao @mac\_zhou @cxqn @yegle @Arctosia 劫持和被劫持的时候，HTTP返回的头部信息里的Server字段是完全不一样的。被劫持的时候是Apache，正常的时候是JSP3/2.0.6。

![不见图 请翻墙](https://lh6.googleusercontent.com/fZbYFggN-n3WM8meI766SsSGRqEi-cgInMyGkGJ2aKHchz-_xK3QCLQ2vsejkPBTs8bJvO3BcyNxRybfZsbcwYRLEbEPpyEfZ9CiKxHI-UXZkFku2VacnvBkaeQZJbn3hr8tiBqaWw)

九条凛： 牆外訪問百度時確實可以在m.js中發現github，greatfire和cn-nytimes等字樣，有理由相信中國本次針對github的國家級攻擊是真實可信的。

![不见图 请翻墙](https://lh3.googleusercontent.com/4LxQCn6R9WtkSctcPhwfD-ZfWxuxcwd-A2q3Cm83wC-L7ZoWLIMVmbfZl3Nf2MbQFCsBgn4zYD-pBBgn12u40tVzVEoCwyvFSHvHi_qbhg2DWvUYAoE2RgKzTwUyeeqW8h8Q-Lg1Og)

28小盆友： 这次的事情其实也不复杂…… 就是 GFW 利用很多网站都有百毒的广告联盟之类，发假包，给他们的 JS 插了个攻击代码，用户读取之后就去攻击 GitHub 了。 因为国内用户访问百毒不用过墙，所有只有国外的访问才会有效……贱格 C.A. Yeung： 为何要劫持百度来攻击GITHUB： 1. 这方式的优点是可以无需劫持大量电脑，也可以让网站访客在不自觉的情况下成了攻击行动的帮凶 2. 让人产生攻击是来自中国境外的错觉 3. 希望透过服务供应商向外国媒体施压，删除中共官方不喜欢的内容。 https://thenanfang.com/why-baidu-was-hijacked-to-attack-github/ 一阁： 看起来似乎是这样的： 国内好多网站上嵌入的某个js会自动载入 http://github.com/greatfire/ 和 http://githu.com/cn-nytimes/ ，达到DDoS效果。 GitHub看到大量流量和referer信息后决定这两个URL返回javascript Jian Alan Huang： GFW之所以越来越忙，因为 最开始只需要封锁敌对势力网站， 接着发现还要封锁提供翻墙软件登录敌对网站的网站， 后来连曝光封锁敌对势力网站和曝光封锁提供翻墙软件网站的网站都需要封锁， 随后连提供资源、提供平台的网站都被当作潜在的敌对势力需要封锁…… 反正最后肯定是：只要不舔菊的都需要封锁。 青萝卜： 自由在哪，GFW 就去哪，Google 到哪，GFW 也到哪。 GitHub 有无数个知名或不知名的翻墙工具，还有很多研究 GFW 的项目，加上近期 Google code 项目开始迁移到 GitHub，对于作恶多端的 GFW 来说，GitHub 就是眼中钉，肉中刺，不灭不消气。 clowwindy： 今天是个值得纪念的日子，墙的角色已经不再只是一个保护主义的工具。 墨守于长城内几千年的伟大民族终于穿过长城走向世界，开始挑战西方价值和规则。 不管你是翻墙也好，肉翻也好，你都躲不开这个民族不断扩张的世界影响力。 中国第一份电子邮件里的那句话一语成谶。 人生露点服务中心： 咦，这么来看，GFW已经成了码农界的ISIS了 lovegoodbest： HTTP 协议 #GFW 说：我们有能力让全世界范围内，访问了中国大陆网站的人（主要是海外华人），在不知情的情况下对全世界内任何网站发动 #DDOS 攻击。 HTTPS 协议 #GFW 说：我们有顶级CA可以签任意证书哦~~ 北风（温云超, Yunchao Wen）： GFW劫持百度来攻击GITHUB，不过是提醒大家，访问中国网站，就有可能成为网络攻击的帮凶。 想不做帮凶，最好不要碰中国网站。 （利用JS在客户端执行的特性，让攻击显示来自四面八方，这种攻击真的很聪明，可惜当局的聪明都用在了这种无耻的地方。） 28小盆友： 听说 GFW 对 GitHub 发动了 DDoS 核打击…… 那也是，自从上次想封掉谁知引发激烈反弹后被迫解封，就一直耿耿于怀了吧？ 比特客栈的寻行数墨： 利用平民上网的正常流量进行DDoS已经成为中国全新的政治武器。 新的被害者是：GitHub。 换而言之，我们已经从Defensive变为Offensive了。 东先生： GFW调用民间流量攻击境外网站，这是挟持中国网民对抗整个文明世界，是一种流氓行径。 不是百度流氓，也不是GFW流氓，而是这个国家真的很流氓。 #你国 lovegoodbest： 以前 “Across the Great Wall, we can reach every corner in the world” 现在 “Reinforcing the Great Wall, we can attack every corner in the world” Velaciela： 较量无声：全球最大成人搜索网站正在攻击全球最大同性交友网站 zmt： 说句公道话，GFW的领导真的没兴趣ddos一个同性交友网站。 我觉得应该是GFW里的码农和github上的码农因基生恨，将怒火发泄在github上了。。。 归根到底，还是码农内部矛盾 clowwindy： GitHub 其实可以在这个弹框里写点吓人的话，对国内网站的声誉造成足够恶劣的影响和不可挽回的损失。 nekoworkshop： 要我说github应该把那个alert换成： “天灭共产党 退党保平安 1·发表三退声明的其他途径：(1)电子邮件: tuidang@epochtimes.com(2)美国热线电话:001-7…………” #然后看好戏 lovegoodbest： 话说如果现在 #Github 把那个alert信息改为google ads，那么它不就是可以坐着收钱了么.... 东哥： github要不是alert，直接再重定向到我朝的任意一个gov站点，那会是什么效果？ 东哥： 这次对github的攻击刷新了肉鸡的概念，从此没人敢NB哄哄的说自己的电脑不可能成为肉鸡了。 流觴： 看GFW这种二逼机制，以及国企式的维护水平，如果哪一天被牛逼黑客利用，搞出个全球网络大灾难来，千万不要奇怪。 GFW这次搞GitHub等于在全球程序员中给自己打了个广告，感觉丫正在慢慢走向那一步。 Ukyoi (右京样一)： GFW这次做得好下流…… 千万别说是井外敌对势力故意栽赃陷害。

![不见图 请翻墙](https://lh3.googleusercontent.com/cHr2Z8IdpMGPYgwsALs0r_DaCDMReeV2zvndMzYoXLm3Ctr11eJqiiwws6hzFjXqpQ1ezrXGtGI96EzmQ-A4M31M0OhtQNGuTwK17DsbMbyTp2f5xyKsmYWaFRnc7_ElhA9Um1i-TQ)

Arctosia： 如果程序员不管在哪里工作都是所谓讨碗饭吃求生计，“只是执行命令而已”。 那这么有创意的手法，也一定是五六十岁的领导们想出来的了，绝对和程序员们没关系。 小果汁： 被GFW刷屏从昨晚现在了…环境似乎越来越糟了呢。 我一直说，一个Google Scholar都打不开的国度，有什么资格谈学术？！ 老杨： 全世界程序员的切磋之地被我天朝端了，这算扬我国威壮我国魂么？ 换一句话说，全世界程序员都没想出来怎么把墙搞死？ Shell.E.Xu： GFW的新思路看来是利用全中国人的流量在国外揍人。这样就算GFW不封你们，也没有啥外国网站敢放行中国IP了。。。 Shippo7： 这次gfw攻击github，最逗之处在于选择了一个程序员网站。 这相当于一个平时劫财劫色的猖狂流氓去武术学校里找教练打架，把全校师生都被吸引过来了。 就看github见招拆招从来没完全中断过服务，gfw有匕首没人能一下制服他，但是衣服已经被众人扒光了... 就看他是继续表演下去还是默默离开 青萝卜： 这几天 GitHub 在其官网上不断公告受到超大流量的持续性 DDoS 攻击，但网站在数天内一直保持正常。 通过安全研究员 宫一鸣 提供的信息，这背后是一家名为 Prolexic 的公司帮助 GitHub 抵御 DDoS 攻击。 http://36kr.com/p/531307.html Get： 逼人删项目自我审查，干脆让github被封掉算了吧。 影响中国IT业的发展水平？切，老子现在才不关心这个！ 翻个墙都搞不定说明缺乏做程序员好奇心，筛掉一大部分滥用者以及低水平码农，合格的程序员自然供不应求，工资水涨船高，这明显是好事。 zmt： 要是封了github，下一届“国家自然科学一等奖”从哪抄？ （编程随想注： 咱们天朝有些奇葩的程序员。当 GitHub 被 GFW 骚扰了之后，他们不去责怪 GFW，却抱怨 GitHub 没有把那些“不和谐的内容”清理掉。 这就好比——有歹徒持刀行凶，不去责怪歹徒，反而去责怪那些卖刀的。

抱有这种观点的人，很多已经深陷于“斯德哥尔摩综合症”。如果你没听说过这种病症，请看俺之前的博文《[天朝民众的心理分析：斯德哥尔摩综合症](http://program-think.blogspot.com/2012/06/stockholm-syndrome.html)》。）

☂XiaoLan： 跪久了,站不起来了...

![不见图 请翻墙](https://lh6.googleusercontent.com/pwpHvXubSzAl0dHRaNksuZogRgV1FRAi1v234aBB_JtnXVMJrSk2CcVV3JxcllyXZHrPj2-5zutOvdW_r61RbUrxhFezp4aaVuZoTtkN1U2dgorDiT97HADhZSwnNQSRLuXqpjTm8g)

（编程随想注：上述这些，就是墙内奇葩程序员在 GitHub 上的留言，要求 GreatFire 撤出 GitHub）

青萝卜： GitHub 被攻击， 网络墙国的程序员说 @GreatFireChina 在作恶。 来自自由世界的程序员说 CNGov 在作恶。 同一个计算机世界，不同的程序员。 （匿名网友）： 这是光明程序员和黑暗程序员的斗争！ Chunlin Zhang： 你们觉得那些技术人员无骨，他们觉得"扬我国威！" 大家思考的基准根本就不一样。 //China's national firewall hijacks JavaScript to DDoS GitHub - Slashdot http://t.cn/RAy86Fu Jian Alan Huang： 你国的程序员长期以来一直以技术小清新居多，不过最近几年确实有很大长进。 标榜自己技术中立、不碰政治、不反共的，以前很常见，现在基本上已经属于恐龙了。 没办法，都是被逼的，每天上网都被政治糊一脸屎，再怎么装小清新都是要爆发的。 在残酷的现实面前，任何启蒙都是多余的！ Hsiaoming Yang： 每次发生什么网站被封，就会有一大群国人跑过去让别人删内容，仿佛接到了省政府新闻办的删帖令。 你们什么时候才能醒悟，作恶的是你们政府，而不是几篇文章几个项目。 而且你永远也抓不住政府的G点，你以为删掉这删掉那就没事了？想的美。 qubicllj： GitHub用戶taogogo（bio顯示為百度職員）發文讓Greatefire項目離開Github，這個國家沒有救 （编程随想注：这位taogogo用户，不光“自我阉割”，还想让别人也“自我阉割”） 御宅暴君： 谁说 GitHub 本身就不适合 GreatFire 这「政治组织」活动？ GitHub 来打你们脸了：https://government.github.com/ 别国政府都用 GitHub 为公民服务了，中国政府就会 DDoS; 更还有人作伥地叫 GreatFire 滚。 差距令人悲哀！ 御宅暴君： @akar1nchan 前几天有个新闻，某男性强暴了女性，还振振有词地说，要怪就怪她「晚上乱外出」。你这归因法和他一致。 什么叫晚上外出？现代公民天生就应该有在公共场所活动的自由，并享有人身安全受到保障的权利。 同理，GitHub 的 ToS 上也没有禁止 GreatFire. 土木坛子： 知乎的自我阉割是不是越来越厉害了？—— 如何评价百度广告代码和统计代码被劫持攻击GitHub 的事件 https://www.zhihu.com/question/29086378 数字时代“真理部指令”项目： \[真理部指令\] Github遭遇大规模ddos攻击: 对Github遭遇大规模ddos攻击一事，在权威媒体没有报道之前不要自行揣测和评论，也不要转载境外信息。 http://bit.ly/1MiaNAg \[中国数字时代\] 陈少举： @CasperYang 如何评价知乎删除《如何评价知乎删除《如何评价知乎删除《如何评价知乎删除《如何评价知乎删除《如何评价知乎删除《如何评价知乎删除《如何评价知乎删除《如何评价知乎删除《如何评价知乎删除百度统计代码被用于攻击GitHub的事件？》》》》》》》》》 无名☂： 刁呆呆：“中国一不输出革命，二不输出饥饿和贫困，三不去折腾你们，还有什么好说的。” 话音刚落，GFW分分钟扇刁呆呆的老肉脸。 Jian Alan Huang： 小组长上台以后，尽管网络管制思路跟之前一致，但路子毕竟野了很多。 CNNIC颁发官方假证书进行中间人攻击、GFW劫持全球网络流量发动DDoS攻击、强调网络主权等等的事... 如果从积极方面看的话，那就是在当局看来，单纯的砌墙防御已经不够用了，翻墙途经越来越多，不主动出击就是等死。 （编程随想注：就在昨天，朝廷外交部已经郑重声明，彻底撇清和此次事件的关系。对这种耍赖，俺毫不意外。） Kgen Bao： 外叫部否认攻击 Github 了，其实这种掩饰毫无意义。 因为能在中国网络出入口处，劫持百度的JS脚本的，除了墙，还有谁呢？ 可是中国说自己没有墙的，要是承认了这次攻击，就等于承认了墙的存在。 所以撒了一个谎，就要用另一个谎来圆场，发炎人不好当。 九条凛： 為什麼中國政府能一邊聲稱自己是網路犯罪受害國，在外交部發言中否認一切攻擊的行為。 然後還一邊明目張膽肆無忌憚的進行偽造證書，中間人攻擊竊取國民資料，DDoS攻擊他國的行為。 因為謊言是專制政權的根基，這和宇宙真理邪教的本質是一脈相承的。 比特客栈的寻行数墨： Github DDoS进入第三天（超过72小时），已不对Github服务造成多大影响。 我不知道GFW的人作何感想。他们只剩下砍掉Github这个选项。 但正如中国政治：一刀切，恰恰体现了管理者的愚昧和失败。 Eric Xu, PhD (徐宥)： 号召大家趁这个机会花点钱买 GitHub 的服务。你交给流氓政府的每一块钱税都可能成为攻击人类文明的子弹。 九条凛： 你國建GFW和搞DDoS都是用納稅人的錢唉，人民不投票也就罷了，人大代表也沒舉手表決一下就開搞了嗎？ heely： 别一惊一乍的，或许是我党想考验一下网络作战部队的真实水准，于是某领导在喝醉了之后，对部下悄悄说了一番话。 拿Github练练手而已，主要目的是为了进一步防止美帝窥探我国网络隐私而采取的演习。 \*っぽい\*： 我国仍处于并将长期处于社会主义初级阶段，我们现阶段所面临的主要矛盾是： 人民日益增长的智商同落后的洗脑教材之间的矛盾。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
[每周转载：关于 GitHub 和 GFW 的 PK（第1季）](https://program-think.blogspot.com/2013/02/weekly-share-39.html)  
[每周转载：关于“Gmail 彻底被墙”的网友评论](https://program-think.blogspot.com/2014/12/weekly-share-78.html)  
[天朝民众的心理分析：斯德哥尔摩综合症](https://program-think.blogspot.com/2012/06/stockholm-syndrome.html)

