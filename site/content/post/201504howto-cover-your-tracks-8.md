---
layout: default
title: '如何隐藏你的踪迹&#65292;避免跨省追捕[8]&#65306;如何搭配&#8220;多重代理&#8221;和&#8220;多虚拟机&#8221;'
date: None
author:
    display_name: 
---

　　话说这个系列已经2年没更新了（之前的“[第7篇](https://program-think.blogspot.com/2013/01/howto-cover-your-tracks-7.html)”发布于2013年1月）。前几天看到有读者在博客评论区讨论“双重代理”如何部署在“双虚拟机环境”。于是俺借着这个话题，再发一篇。 　　今天这篇，主要谈谈——如何把“多重代理”和“多虚拟机”组合在一起。可能很多同学把这个问题想得过于简化。其实捏，不同的 Tor 前置代理以及不同的上网软件，有可能需要不同的部署方式。具体取决于——相关软件的靠谱程度，以及你对安全性的要求有多高。 　　事先声明： 　　如果你不了解啥是“多重代理”，或者你不了解啥是“多虚拟机方案”，建议先看完本系列的前面3篇：

《[如何隐藏你的踪迹，避免跨省追捕\[5\]：用多重代理隐匿公网IP](https://program-think.blogspot.com/2012/03/howto-cover-your-tracks-5.html)》

  
《[如何隐藏你的踪迹，避免跨省追捕\[6\]：用虚拟机隐匿公网IP（原理介绍）](https://program-think.blogspot.com/2013/01/howto-cover-your-tracks-6.html)》  
《[如何隐藏你的踪迹，避免跨省追捕\[7\]：用虚拟机隐匿公网IP（配置图解）](https://program-think.blogspot.com/2013/01/howto-cover-your-tracks-7.html)》 　　为了避免产生歧义，先界定一下相关的术语。 　　本文提及的“多重代理”，指的是——基于 Tor 的多重代理。在各种“多重代理”的方案中，这种形式是最实用的（兼顾了安全性和速度）。 　　顺便说一下： 　　去年（或者是前年）曾经有读者在博客评论中咨询“多重 VPN”。俺个人认为：多重 VPN 的方案，隐匿性【远远不如】基于 Tor 的多重代理。因为 VPN 服务器的的 IP 是相对固定的，即使你用了多重 VPN，被人反查（逆向追踪）的可能性还是比较大。在这方面，Tor 就远远好于 VPN。因为 Tor 的线路是【动态变化】滴（大约10分钟变化一次），导致逆向追踪非常困难。  
　　在本系列前面的博文《[用虚拟机隐匿公网IP（原理介绍）](https://program-think.blogspot.com/2013/01/howto-cover-your-tracks-6.html)》，俺介绍了两种虚拟机方案——“单虚拟机”和“双虚拟机”。 　　今天这篇博文，面向的是安全性要求比较高的读者；因此，【不】讨论“单虚拟机”方案。 　　在双虚拟机方案中，俺把充当网关的虚拟机称为“网关虚拟机”，把那个网卡设为“Host Only”模式的虚拟机称为“隔离虚拟机”。 　　既然说到 Guest OS，顺便再提一下 Host OS。 　　“Host OS 的安全性”本文所有方案的前提。换句话说：如果 Host OS 不安全，本文的任何方案都【没有】意义。 　　如果你对安全性的要求比较高，对如下几种情况，你需要额外考虑部署的问题。 　　“多个隔离虚拟机”是啥意思捏？

　　以俺本人为例，俺所有的日常工作都是在虚拟机中进行。（这么干的好处很多，具体参见“[这篇博文](https://program-think.blogspot.com/2012/11/system-vm-2.html)”）。所以，俺会有一个单独的虚拟机，用于“编程随想”这个身份的上网；并且会有另一个虚拟机，用于俺的真实身份的上网。如此一来，至少就有2个“隔离虚拟机”了。

　　那么，在这种情况下，Tor 是应该安装到“网关虚拟机”还是安装在“隔离虚拟机”捏？大伙儿先思考一下。 　　所谓的“网关虚拟机的环境不可靠”，有如下几种情况： 1. 网关虚拟机的操作系统不可靠 （比如说，你的网关虚拟机安装的是 Windows 系统。有些人可能会担心 Windows 存在 NSA/美国国安局 的后门） 2. Tor 的前置代理不可靠 （比如说，你用了国内 VPN 提供商提供的 VPN 做 Tor 的前置代理。该 VPN 需要安装客户端，而你对这款客户端不放心） （比如说，你用了 无界 和 自由门 作为 Tor 的前置代理。这两款工具【不是】开源的。所以你对这两款工具不放心） 3. 网关虚拟机安装了某些不可靠的软件 （比如说，有些电信提供商/ISP 的宽带拨号，需要在系统中额外安装一个拨号软件。而你对 ISP 提供的拨号软件不放心） 　　那么，在这种情况下，Tor 是应该安装到“网关虚拟机”还是安装在“隔离虚拟机”捏？大伙儿先思考一下。 　　最后一种情况是：上网软件不可靠。 　　所谓的“上网软件”，顾名思义就是你用来上网的软件。可以是浏览器，也可以是聊天工具或者下载工具。 　　为啥会碰到“上网软件不可靠”的情况捏？ 　　举例如下： 　　比如你想用 QQ 进行反党宣传。但是你又不想让腾讯知道你的公网 IP。于是你就需要组合“多重代理”和“多虚拟机”来确保你的公网 IP 不会暴露给疼逊的服务器。在这种情况下，QQ 客户端就属于“不可靠的上网软件”。 　　那么，在这种情况下，Tor 是应该安装到“网关虚拟机”还是安装在“隔离虚拟机”捏？大伙儿先思考一下。  
　　为了形象起见，俺直接画一个示意图，如下：

![不见图 请翻墙](https://lh3.googleusercontent.com/VP-KN73EzLZruUNOOnQDYDET6isWv_h5TJdHKAfujgtlS2MAdumtCHwe9fKgywmz_NWaDCrN-jUzeYjO18TKfV5vJ55agGg5laNVrfqUjZpj59-WREK43ejkTmz7SWePZQmu_rI-lg)

  
　　为了形象起见，俺直接画一个示意图，如下：

![不见图 请翻墙](https://lh3.googleusercontent.com/4uVt5aAdy_hFP5VnApgXJ1oZ3Q-E7MaDr9aBGIeCc2-vlQvtWZMP89OyCwyPnvlXY33HdGTmY_w-TIUVA2TXy7U9P0wTghmpktPtD4tJ56xXlyQ3FV56ohmnA8MTVaymIIL4BaARQg)

  
　　如下图所示，如果“网关虚拟机”的环境不可靠（比如说其中有恶意软件），那么该恶意软件有可能会监控“网关虚拟机”系统中的网络流量。如此一来，就会看到【原始流量】（图中的“红色虚线”）。

![不见图 请翻墙](https://lh5.googleusercontent.com/IDLvCLBnrqWnFXOTyrq7W45vekWTczJnuguUyP8pqyk5uUC7LT7g5b3U8VwOdjZ3w3L7355KnWadtcqN99nTHirCWDeXE_SQfOKNlWb8LOusSHKKU7BFftUnlRLWYW7gOCAj9O0xZw)

  
　　如下图所示，如果“上网软件”不可靠，那么该软件有可能直接尝试去连接“Tor 的前置理”（参见图中的“红色实线”），从而导致 Tor 被绕过。 　　虽然这种行为不会直接导致你的公网IP暴露，但是会大大降低你在网络层面的隐匿性。如果有人要对你进行逆向追溯，只要查出前置代理服务器上的访问日志，就【有可能】查出你的公网IP。

![不见图 请翻墙](https://lh3.googleusercontent.com/d7-d4k2z4jX42Wa1ahX3lk6l_27a6o6QmEd2YI9G1q_Pc5dp4oCPfiOihzbtmTC84pfVBbPAp1JQPubvjL-7yx5RjdtajvV_OUfzAK5Ys2kgLlt2-cLmxQl3SHwKGJsUmOy2qqm38w)

　　下面来说说应对的策略。 　　很显然，这种情况下，你必须采用“Tor 后置部署”的部署方式。示意图如下：

![不见图 请翻墙](https://lh3.googleusercontent.com/4uVt5aAdy_hFP5VnApgXJ1oZ3Q-E7MaDr9aBGIeCc2-vlQvtWZMP89OyCwyPnvlXY33HdGTmY_w-TIUVA2TXy7U9P0wTghmpktPtD4tJ56xXlyQ3FV56ohmnA8MTVaymIIL4BaARQg)

  
　　很显然，这种情况下，你必须采用“Tor 前置部署”的部署方式。示意图如下：

![不见图 请翻墙](https://lh3.googleusercontent.com/VP-KN73EzLZruUNOOnQDYDET6isWv_h5TJdHKAfujgtlS2MAdumtCHwe9fKgywmz_NWaDCrN-jUzeYjO18TKfV5vJ55agGg5laNVrfqUjZpj59-WREK43ejkTmz7SWePZQmu_rI-lg)

  
　　对这种情况，俺需要稍微费点口水。 　　首先，俺要唠叨一下： 　　之所以需要多个“隔离虚拟机”，就是想要达成某种【隔离性】。比如在本文开头提及俺本人的例子——俺把不同的上网身份隔绝在不同的虚拟机，就是为了尽可能避免两者的关联性。

　　**如果采用“Tor 前置”部署**

　　由于“网关虚拟机”只有一个。把 Tor 部署在网关导致你的多个“隔离虚拟机”共用【同一个 Tor 环境】。 　　“共用同一个 Tor 客户端”的风险在于：多个“隔离虚拟机”的上网流量，有比较大的可能性，这些流量会使用同一个（Tor）出口节点。由于的出口节点能够看到原始流量，万一原始流量是明文的HTTP，并且该节点是蜜罐，那么风险就会变大。 　　针对某热心读者的质疑，俺补充说明一下： 　　Tor 客户端会同时创建几个不同的虚拟链路，用于传输数据。每个链路包含三个 Tor 节点（分别是：入口节点、中间节点、出口节点）。只有“出口节点”能看到原始流量。 　　如果你正在使用的“隔离虚拟机”的个数超过 Tor 客户端创建的链路数量，那么就存在——“不同的隔离虚拟机共用同一个链路”——这种情况下，该链路的出口节点，有可能会发现这些不同的隔离虚拟机的原始流量之间的相关性。

　　反之，**如果采用“Tor 后置”部署**

　　由于每个“隔离虚拟机”都有自己的 Tor 客户端。所以这几个“隔离虚拟机”的上网流量，在同一个瞬间使用同一个（Tor）出口节点的概率小很多。就算碰巧都用了同一个“出口节点”，因为不同的 Tor 客户端建立的虚拟链路也是不同的，所以这个出口节点就会以为这些流量来自不同的上网用户（因此，你的多个网络身份【不会】被关联起来）。 　　本来不想写这一节。但是俺估计：某些喜欢抬杠的同学会这么问。 　　老实说，这种情况是比较蛋疼的（很罕见）。但是同样有办法搞定。而且方法有两种，具体如下：

　　**办法1**

　　把“双虚拟机”改为“三虚拟机”。多出来的那个虚拟机用来单独安装 Tor（不妨称之为“Tor 虚拟机”）。 　　注意事项： 　　为了防止上网软件绕过 Tor，直接去联前置代理，需要在“网关虚拟机”上配置防火墙规则，使得“隔离虚拟机”无法直接访问“网关虚拟机”。

　　**办法2**

　　把“双重代理”改为“三重代理”。也就是说——Tor 既部署在“网关虚拟机”，也部署在“隔离虚拟机”。 　　为了让大伙儿直观些，再画一张示意图，如下：

![不见图 请翻墙](https://lh5.googleusercontent.com/b6vak9DLTwYo9JPYbp1t7_nUbJtQYzX06PeNWvWEO6k4piGUkH-nLIBMseQqj7NAAsPS9TO-imZe245MHaLdP0hh1eaar4vPfXODnTuH7OktI6eD8zU8Ftc9DiGj3UfNzwRmWdtTXQ)

  
　　**小结** 　　这两个方法，各有缺点： 方法1：因为“三虚拟机”会增加 Host OS 的性能开销，让人感觉有点“杀鸡用牛刀”。

方法2：虽然只用到两个虚拟机（比 方法1 的性能好），但是出现了“Tor over Tor”的组合。Tor 官网的文档【反对】这种组合方式（链接在“[这里](https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO#ToroverTor)”）

　　描述了这么多种部署方式，不晓得大伙儿看了之后，会不会晕？ 　　为了防止大伙儿晕菜，俺在结尾作一个总结发言：

　　**不论是哪一种部署方案，出问题的根源都是因为【Tor 被绕过】**。

　　对于“Tor 前置部署”，如果网关中的软件偷窥了进入 Tor 之前的流量，其效果就等同于——绕过 Tor 获取了原始流量。 　　对于“Tor 后置部署”，就更加明显了——上网软件如果耍流氓，有可能直接去联前置代理（同样是绕过 Tor）。 　　对于“只部署一个 Tor 客户端”的情况，你要确保 Tor 运行在可靠的环境中。如果“网关虚拟机”不可靠，就把 Tor 放在“隔离虚拟机”；反之，如果“隔离虚拟机”不可靠，就把 Tor 装在“网关虚拟机”。 　　如果两边都不可靠，要么加出一个单独的虚拟机装 Tor（刚才所说的“三虚拟机”），要么两边都装 Tor（刚才所说的“三重代理”）。

**[回到本系列的目录](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html#index)**

