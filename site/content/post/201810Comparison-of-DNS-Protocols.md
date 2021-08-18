---
layout: default
title: '对比4种强化域名安全的协议&#8212;&#8212;DNSSEC&#65292;DNSCrypt&#65292;DNS over TLS&#65292;DNS over HTTPS'
date: None
author:
    display_name: 
---

![不见图 请翻墙](https://lh6.googleusercontent.com/4QaghUJDZ1GkjAsoVyFbCnhNchM7YYswTgIuk9MWSA3NNW6xBh6P4VJ1NRAjJcqFJXiee6VhkCkI8UuP8eJLSd7Ka0dyOekEHVc0_GDVWvHOUOrSH0CL7T2JXqka3dZdG6VNLo--vkU)

  
  
　　俺在写前一篇博文（也就是 [Firefox PK Chrome 那篇](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)）的时候，碰巧看到 Mozilla 官方博客提到说：目前最新的 Firefox 62 版本开始支持【DNS over HTTPS】这一特性（链接在“[这里](https://blog.nightly.mozilla.org/2018/06/01/improving-dns-privacy-in-firefox/)”）。 　　本来想顺便聊一下“DNS over HTTPS”这个玩意儿。但是查了一下，发现它的 RFC 目前还只是【草案】，尚未正式发布。

　　所以俺就把本文的主题改成：对比4种强化 DNS 安全的网络协议。然后借此机会普及一些信息安全知识。

  
  
　　简而言之，DNS 是用来查询域名的协议。关于它的原理（工作机制），俺已经写过一篇教程（在“[这里](https://program-think.blogspot.com/2014/01/dns.html)”），所以今天就不重复浪费口水啦。 　　另外，如果你是技术菜鸟，在看这篇博文之前，确保你已经【看完】如下这篇：

《[计算机网络通讯的【系统性】扫盲——从“基本概念”到“OSI 模型”](https://program-think.blogspot.com/2021/03/Computer-Networks-Overview.html)》

　　传统的 DNS 是一个【比较古老】的协议。最早的草案可以追溯到1983年。1987年定稿之后，基本上没啥变化。算起来，它的年龄比俺博客的很多读者都要大。 　　设计 DNS 的时候，互联网基本上还是个玩具。那年头的互联网协议，压根儿都没考虑安全性，DNS 当然也不例外。所以 DNS 的交互过程全都是【明文】滴，既无法做到“保密性”，也无法实现“完整性”。 　　缺乏“保密性”就意味着——任何一个能【监视】你上网流量的人，都可以【看到】你查询了哪些域名。直接引发的问题就是隐私风险。 　　缺乏“完整性”就意味着——任何一个能【修改】你上网流量的人，都可以【篡改】你的查询结果。直接引发的问题就是“DNS 欺骗”（也叫“DNS 污染”或“DNS 缓存投毒”）

　　关于“域名欺骗/域名污染”，可以参见俺的另一篇博文《[扫盲 DNS 原理，兼谈“域名劫持”和“域名欺骗／域名污染”](https://program-think.blogspot.com/2014/01/dns.html)》。

　　为了解决传统 DNS 的这些弊端，后来诞生了好几个网络协议，以强化域名系统的安全性。俺挑选其中4个来介绍。除了这4个，其它一些协议的名气和影响力太小，不值一提。 　　下面俺以出场时间的先后，分别介绍这4个协议。  
  
　　这玩意儿是“Domain Name System Security Extensions”的缩写。在今天介绍的4个协议中，DNSSEC 是最早诞生的（1997）。从最先的 [RFC 2065](https://tools.ietf.org/html/rfc2065) 进化为 [RFC 2535](https://tools.ietf.org/html/rfc2535)，再到 [RFC 4033](https://tools.ietf.org/html/rfc4033)、[RFC 4034](https://tools.ietf.org/html/rfc4034)、[RFC 4035](https://tools.ietf.org/html/rfc4035)。  
　　在今天介绍的4个协议中，DNSSEC 也是最早大规模部署的。在2010年的时候，所有[根域名服务器](https://zh.wikipedia.org/wiki/%E6%A0%B9%E5%9F%9F%E5%90%8D%E6%9C%8D%E5%8B%99%E5%99%A8)都已经部署了 DNSSEC。到了2011年，若干顶级域名（.org 和 .com 和 .net 和 .edu）也部署了 DNSSEC。  

\--------
 DNSSEC
--------
  UDP
--------
  IP
--------

  
　　当初设计 DNSSEC 的一个考虑是“尽可能兼容 DNS 协议”。所以 DNSSEC 只是在 DNS 协议的基础上增加了一个【数字签名机制】。 　　有了数字签名，如果域名查询的结果被人篡改了，DNSSEC 客户端就可以通过【校验签名】，判断查询结果是假的。套用信息安全的行话——DNSSEC 实现了【完整性】（也叫“不可篡改性”）。 　　由于 DNSSEC 引入了【数字签名】，就需要有【公私钥对】。私钥是保密的，用来生成签名；公钥是公开的，用来验证签名。DNSSEC 客户端可以向 DNSSEC 服务器发出请求，获得一个 DNSKEY 记录，里面含公钥；然后用这个公钥校验每次的查询结果。 　　有些聪明的读者会问了：DESSEC 客户端在向服务器请求公钥的过程中，如果被攻击者篡改了，得到一个假的公钥，那该如何是好？ 　　为了解决此问题，DNSSEC 体系要求【上级域】来担保。比如想要证明 program-think.blogspot.com 这个域名的公钥是否可信，就依靠 blogspot.com 这个域名的公钥来验证。通过层层追溯，最后达到【根域名服务器】。而“根域名服务器的公钥”是事先就部署在客户端的——这玩意儿就是整个信任链的根源，称之为“信任锚”（洋文叫“Trust Anchor”）。  
　　在今天聊的4个协议中，DNSSEC 应该是最成熟的。除了前面提到的广泛部署，大多数公共的域名服务器也都支持它。维基百科上有一个对照表（链接在“[这里](https://en.wikipedia.org/wiki/Public_recursive_name_server)”），对比了有名气的几个公共域名服务系统。在今天聊的4个协议中，支持 DNSSEC 的最多。 　　虽然 DNSSEC 最成熟，但它有个天生的缺陷——【没有】考虑到【保密性】。

　　DNSSEC 虽然对传输的数据做了数字签名，但是【没有】进行加密。这就意味着——任何能监视你网络流量的人，也可以看到你通过 DNSSEC 查询了哪些域名。**隐私风险大大滴！**

　　Chrome 曾经在 14 版本支持过 DNSSEC，后来又【移除】了；而 Firefox 官方从未支持过 DNSSEC 协议。俺猜测：大概就是这个缺点给闹的。  
　　第2个出场的是 DNSCrypt。这个协议是由 Frank Denis 和 Yecheng Fu（付业成）两人设计的。

　　这个协议从来【没有】提交过 RFC（征求意见稿），要想看它的协议实现，只能去它的官网（链接在“[这里](https://dnscrypt.info/protocol/)”）。

　　历史上有过两个版本，分别称：Version 1 和 Version 2。如今主要使用“版本2”  

\----------------
    DNSCrypt
----------------
   TCP or UDP
----------------
       IP
----------------

  
　　前面俺提到 DNSSEC 协议强调兼容性。而 DNSCrypt 则完全是另起炉灶搞出来的协议。在这个协议中，域名的“查询请求”与“响应结果”都是加密的。这就是它比 DNSSEC 高级的地方。 　　换句话说，DNSCrypt 既能做到【完整性】，也能做到【保密性】；相比之下，DNSSEC 只能做到【完整性】。 　　DNSCrypt 的信任链比较简单——客户端要想使用哪个 DNSCrypt 服务器，就需要预先部署该服务器的公钥。 　　另外，DNSCrypt 还支持客户端认证（作为可选项）。如果需要的话，可以在服务器上部署客户端的公钥。此时，服务器只接受可信的客户端的查询请求。 　　如前所述，DNSCrypt 同时支持【完整性】与【保密性】。在隐私方面完胜 DNSSEC。 　　在下层协议方面，DNSCrypt 同时支持 TCP 和 UDP，显然比 DNSSEC 灵活（DNSSEC 只支持 UDP）。 　　顺便提醒一下：虽然 DNSCrypt 协议默认使用 443 这个端口号，但该协议与 HTTPS 毫无关系。 　　（俺个人认为）DNSCrypt 最大的缺点就是前面提到的：【从未】提交过 RFC。没有 RFC 也就无法通过 IETF（互联网工程任务组）进行标准化。一个无法标准化的协议，其生命力要打很大的折扣。 　　另一个比较小的缺点是——虽然 DNSCrypt 协议是加密的，但可以被识别出来。换句话说：如果有人监控你的流量，可以识别出哪些流量属于 DNSCrypt 协议。为啥说这是个缺点捏？在本文末尾讨论 “DNSCrypt 与 TLS 的安全性对比” 的时候，会详细加以说明。

　　再来说说【公共 DNS 系统】。截至俺写本文时，Google 和 Cloudflare 的公共域名系统【尚未】支持 DNSCrypt（参见[这个页面](https://en.wikipedia.org/wiki/Public_recursive_name_server)的对照表）。这也是一个缺点。

　　“DNS over TLS”有时也被简称为【DoT】。为了打字省力，本文以下部分用 DoT 来称呼之。  
　　DoT 已经正式发布了 RFC（参见 [RFC 7858](https://tools.ietf.org/html/rfc7858) 和 [RFC 8310](https://tools.ietf.org/html/rfc8310)）。 　　从时间上看，RFC7858 是2016年发布的，RFC8310 是今年（2018）发布的；显然，这个协议出现得比较晚（相比前面提到的 DNSSEC 和 DNSCrypt）。  

\--------
  DoT
--------
  TLS
--------
  TCP
--------
  IP
--------

  
　　顾名思义，DNS over TLS 就是基于 TLS 隧道之上的域名协议。由于 TLS 本身已经实现了【保密性】与【完整性】，因此 DoT 自然也就具有这两项特性。

　　至于 TLS 协议是如何实现完整性与保密性滴？可以参见俺的系列博文：《[扫盲 HTTPS 和 SSL/TLS 协议](https://program-think.blogspot.com/2014/11/https-ssl-tls-0.html)》

　　DoT 的信任链依赖于 TLS，而 TLS 的信任链靠的是 CA 证书体系。

　　关于 CA 证书体系，可以参见8年前的博文：《[数字证书及 CA 的扫盲介绍](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)》

　　相比 DNSSEC，DoT 具备了【保密性】；相比 DNSCrypt，DoT 已经标准化。 　　另外，由于 DoT 协议是完全包裹在 TLS 里面，即使有人监视你的上网流量，也无法判断——哪些 TLS 流量是用于域名查询，哪些 TLS 用于网页传输。换句话说，DoT 协议的流量无法被【单独识别】出来。 　　支持 DoT 的客户端还不够多。尤其是主流的浏览器还没有计划增加 DoT 的支持。 　　“DNS over HTTPS”有时也被简称为【DoH】。为了打字省力，本文以下部分用 DoH 来称呼之。  
　　在今天介绍的4个协议中，DoH 是最新的（最晚出现的）。RFC 方面，它已经有了相应的草案，但还【没有】正式发布。截至俺写本文时，DoH 的草案已经发了 15 个版本（从 00 到 14），最新版的链接在“[这里](https://tools.ietf.org/html/draft-ietf-doh-dns-over-https-14)”。 　　很多人把 DoH 与 DoT 混为一谈，实际上这是两种不同的协议。你可以对比这两者的协议栈，（只要你眼睛不瞎）就可看出其中的差别。  

\--------
  DoH
--------
  HTTP
--------
  TLS
--------
  TCP
--------
  IP
--------

  
　　顾名思义，DNS over HTTPS 就是基于 HTTPS 隧道之上的域名协议。而 HTTPS 又是“HTTP over TLS”。所以 DoH 相当于是【双重隧道】的协议。 　　与 DoT 类似，DoH 最终也是依靠 TLS 来实现了【保密性】与【完整性】。

　　至于 TLS 协议是如何实现完整性与保密性滴？可以参见俺的系列博文：《[扫盲 HTTPS 和 SSL/TLS 协议](https://program-think.blogspot.com/2014/11/https-ssl-tls-0.html)》

　　DoH 类似于 DoT，最终是靠 TLS 所使用的“CA 证书体系”来实现信任链。

　　关于 CA 证书体系，可以参见8年前的博文：《[数字证书及 CA 的扫盲介绍](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)》

　　基本上，DoT 具备的优点，DoH 也具备。 　　相比 DoT，DoH 还多了一个优点： 　　由于 DoH 是基于 HTTP 之上。而主流的编程语言都有成熟的 HTTP 协议封装库；再加上 HTTP 协议的使用本身很简单。因此，要想用各种主流编程语言开发一个 DoH 的客户端，是非常容易滴。 　　如前所述，DoH 目前还只有 RFC 的草案，尚未正式发布。这算是一个缺点。 　　相比 DoT，DoH 还有一个小缺点——由于 DoH 比 DoT 多了一层（请对比两者的协议栈），所以在性能方面，DoH 会比 DoT 略差。为啥说这是个【小】缺点捏？因为域名的查询并【不】频繁，而且客户端软件可以很容易地对域名的查询结果进行【缓存】（以降低查询次数）。所以 DoH 比 DoT 性能略差，无伤大雅。 　　为了给列位看官一个直观的印象，放一个综合的对照表。

协议类型

标准化

完整性  
（防篡改）

保密性  
（防偷窥）

抗协议识别

主流的  
浏览器支持

知名的  
公共服务器

DNSSEC

有

有

无

无

无

Google Cloudflare

Quad9

DNSCrypt

无

有

有

无

无

OpenDNS  
Quad9

DNS over TLS

有

有

有

有

无

Cloudflare  
Quad9

DNS over HTTPS

进行中

有

有

有

有

Google Cloudflare

Quad9

　　接着来聊一下：4个协议中，谁的前景最看好？（以下是俺个人观点，仅供参考） 　　如果要讨论这4种协议的优劣，首先【出局】的是 DNSSEC。因为这玩意儿连【保密性】都不具备，无法保护网民的隐私。相比之下，另外三种协议都具备了“保密性”。 　　（注：DNSSEC 具备“完整性”，不具备“保密性”） 　　DoT 与 DoH 这两个协议，本质上都是依赖 TLS 来保证安全性（完整性＆保密性）。所以剩下三种协议的对比，首先是 DNSCrypt 与 TLS 之间的 PK。 　　俺认为 TLS 具有如下几个优势：

　　**优势1——关于“标准化”**

  
　　SSL/TLS 老早就已经标准化了，距今已超过20年。（关于 SSL/TLS 版本的演变历史，可以参见[这篇博文](https://program-think.blogspot.com/2018/09/https-ssl-tls-4.html)） 　　而 DNSCrypt 发布这么多年，连 RFC 都没有提交过——这玩意儿看来【没希望】成为互联网标准了。

　　**优势2——关于“客户端部署”**

　　TLS 的公钥体系（CA 证书体系）早就已经普及。所有主流的操作系统都内置了一系列 CA 根证书。 　　相比之下，DNSCrypt 另起炉灶搞了一套公钥机制，只有它自己在用。 　　所以，在【部署客户端】的时候，DNSCrypt 会比 TLS 麻烦。虽然某些 DNSCrypt 的客户端已经内置了一些知名的公共服务器的公钥，但如果你要切换到另一个 DNSCrypt 服务器，并且该服务器的公钥没有内置在客户端里面，那你就需要手动部署。

　　**优势3——关于“协议识别”**

　　这个话题前面已经谈过了。此处再重复唠叨一下。 　　如果网络流量被监控，监控者可以根据协议特征，把 DNSCrypt 识别出来；而 DoT 与 DoH，在流量外观上，与其它的 TLS 流量【毫无差异】。也就是说，监控流量的人，无法判断某个 TLS 流量是否属于 DoT 或 DoH。 　　以咱们天朝为例： 　　天朝的国际出口被 GFW 严密监视。如果 GFW 愿意的话，它完全可以根据协议特征，把 DNSCrypt 协议的流量识别出来并阻断掉。 　　再来看 TLS，该协议已经被广泛应用于 HTTPS，GFW 不可能把所有 TLS 流量都阻断；再加上 TLS 协议设计严密，GFW 无法判断 TLS 承载的【上层协议】是啥。所以，对于流经国际出口的 DoT 或 DoH，GFW 是判断不出来滴。 　　综上所述，TLS 完胜 DNSCrypt。所以，剩下的协议就只有 DoT 与 DoH。 　　前面谈 DoH 优缺点的时候，其实已经可以看出这两者谁更有前途了。 　　DoT 因为协议栈少了一层，性能会比 DoH 更好。但是俺前面也说了，域名查询的频度是比较低的，而且还可以利用客户端软件的【DNS 缓存】，进一步减少域名查询的频度。所以 DoT 虽然性能更好，但优势不明显。 　　DoH 的强项体现在如下几方面：

　　**1\. 编程接口更简单**

　　（关于这点，前面提到过）这是个很重要的优势——有助于让更多软件切换到 DoH 之上。

　　**2\. 可以利用 HTTP 协议已有的特性**

　　由于 DoH 是基于 HTTPS 之上，可以无缝地支持 Proxy； 　　DoH 可以充分利用 HTTP 2.0 的特性（HTTP/2 在 HTTP/1.1 基础上加了很多功能）。 　　正是因为 DoH 的这些优势，浏览器厂商对 DoH 的支持更积极。对比一下就可以看出来——DoT 在两年前（2016）正式发布 RFC，主流的浏览器没一个支持；而 DoH 目前才仅仅是 RFC 草案，Firefox 与 Chrome/Chromium 都开始支持了。 　　经过层层淘汰，目前看下来最有前途的应该 DoH（DNS over HTTPS）。 　　DoH 未来的发展势头取决于如下几点： 1. 标准化的时间进度（看目前的架势，正式发布应该快到了） 2. 其它浏览器跟进的速度  
　　分享几篇 DoH 相关的文章：

《[A cartoon intro to DNS over HTTPS](https://hacks.mozilla.org/2018/05/a-cartoon-intro-to-dns-over-https/)》

（注：这是 Mozilla 官方博客的一篇文章，深入浅出地扫盲了 DNS 和 DoH 的原理）

《[The Benefits of HTTPS for DNS](https://bitsup.blogspot.com/2018/05/the-benefits-of-https-for-dns.html)》

（注：这是某个老外写的技术文章，讨论 DoH 可以借助 HTTP 协议的哪些好处）  
　　**Firefox**  
　　Firefox 从 62 版本开始支持 DoH，具体参见 Mozilla 官方博客（链接在“[这里](https://blog.nightly.mozilla.org/2018/06/01/improving-dns-privacy-in-firefox/)”）。  
　　由于 DoH 功能刚刚加入，还没有提供相应的配置界面。如果你想体验该功能，需要定制 Firefox 的配置选项（Preferences）以初始化 DoH 的相关参数。定制 Firefox 的方法参见博文：《[扫盲 Firefox 定制——从“user.js”到“omni.ja”](https://program-think.blogspot.com/2019/07/Customize-Firefox.html)》

　　**Chrome/Chromium**

  
　　Chrome/Chromium 从 66 版本开始支持 DoH。具体参见 Chromium 官网的 issue（链接在“[这里](https://bugs.chromium.org/p/chromium/issues/detail?id=799753)”）。 　　虽然 Firefox 和 Chrome/Chromium 都已经开始支持 DoH，但大伙儿别急着用。 　　按照历史经验，刚加入的新功能，可能还不够稳定，没准儿还存在未曝光的安全漏洞。多等几个版本之后再说。 　　常规的翻墙软件，无非就是“代理软件”与“VPN 软件”。

　　**对于“VPN 软件”**

　　由于 VPN 具有【全局代理】的性质，DoH 当然可以无缝地整合到 VPN 翻墙中。

　　**对于“代理软件”**

　　常见的代理软件，要么是 HTTP 代理，要么是 SOCKS 代理。只要这些代理能支持 HTTPS，也就天然地支持 DoH。 　　注：GAE 没有原生支持 HTTPS 代理。所以基于 GAE 的翻墙软件，就不能走 DoH 协议啦 :(  
　　在 curl 官方的代码仓库，有一个[关于 DoH 的 wiki 页面](https://github.com/curl/curl/wiki/DNS-over-HTTPS#doh-tools)，里面列出了一些 DoH 的客户端小工具。 　　喜欢折腾技术的同学，可以先去玩一玩。 　　因为 DoH 的标准还没有正式发布，关于它的讨论就到此为止。等到啥时候发布了，俺再专门发一篇 DoH 如何使用的博文。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[计算机网络通讯的【系统性】扫盲——从“基本概念”到“OSI 模型”](https://program-think.blogspot.com/2021/03/Computer-Networks-Overview.html)》  
《[扫盲 DNS 原理，兼谈“域名劫持”和“域名欺骗／域名污染”](https://program-think.blogspot.com/2014/01/dns.html)》  
《[扫盲 HTTPS 和 SSL/TLS 协议](https://program-think.blogspot.com/2014/11/https-ssl-tls-0.html)》（系列）  
《[数字证书及 CA 的扫盲介绍](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)》  
《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》（系列）  
《[扫盲 Firefox 定制——从“user.js”到“omni.ja”](https://program-think.blogspot.com/2019/07/Customize-Firefox.html)》

