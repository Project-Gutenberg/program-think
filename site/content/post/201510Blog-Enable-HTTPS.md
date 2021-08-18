---
layout: default
title: '博客全程启用 HTTPS 加密'
date: None
author:
    display_name: 
---

![不见图 请翻墙](https://lh6.googleusercontent.com/2UOkEgaXLx6jfjKYBC_LZ38TA8ferB9CZBFCYY5mXQqxtdb7yxvyt_OPCs-yXu4vNq6F7zUji5BQpzdtC9XmBizQn0Ody2Jwd6VDM_v9SOrilIOcIJZSmreiXNPi_7vCwnoOVN6qdg)

  
  
　　沦陷日长假的第一天，俺打算上博客回复读者评论。通常俺会先登录到 Blogger 的管理界面，清理一下被 Google 误判为垃圾广告的读者评论。结果在管理界面的首页，就看到了 Blogger 的最新消息——[HTTPS support coming to Blogspot](https://googleonlinesecurity.blogspot.com/2015/09/https-support-coming-to-blogspot.html) 　　可把俺高兴坏了（好几年前，俺就盼着这一天）

　　在长假的头两天，俺对博客界面做了一些升级（具体下面会说）。第3天观察了一下，看大伙儿有没有碰到啥问题或 Bug，然后今天发一篇“博客通告”，跟大伙儿打个招呼。

　　简而言之，今后搭建在 Blogspot 上的博客，都可以使用 HTTPS 方式访问。原有的 HTTP 方式依然保留，所以实际上同时支持这两种协议。 　　对于博客的博主，需要先到管理界面，启用一下 HTTPS 的选项，就 OK 了。 　　这两天做了如下几处修改。

　　（**俺仅仅针对博客的【桌面版】界面进行定制。俺一直没有时间去定制【手机版】的界面**）

　　如果你以 HTTP 协议打开任何一个博客页面，俺会使用 JS 脚本自动重定向到同一个页面的 HTTPS 协议。 　　因为俺是基于 JS 实现重定向，如果浏览器禁用了 JS，俺就没辙了。 　　博客的老读者应该知道，俺经常在博文中添加交叉链接，方便你从一篇博文跳转到另一篇相关的博文。 　　当读者点击某个站内链接之后，如果该链接是 http:// 开头的，在新页面打开之后，就会多增加一次跳转。为了节省大伙儿的时间，俺就预先把站内链接全部替换为 https:// 开头。 　　这个功能是在博文加载时，用 JS 脚本实现的。（该功能同样需要依赖 JS 脚本） 　　这个改造跟前一个类似。 　　因为某些读者可能会在评论中贴出某篇博文的链接，而且是 http:// 开头的。俺也用 JS 脚本统一替换为 https:// 开头 　　（该功能同样需要依赖 JS 脚本）  
　　经过上述改造之后，所有的站内链接都是 HTTPS 的。因此，**读者在博客中浏览或者发评论时，网络流量【全都是】加密的**。  
　　简而言之，HTTPS 是【强加密】滴。因此，当你浏览 HTTPS 协议的网页，从“你的浏览器”到“目标网站”之间的数据传输，都是强加密的。 　　传输过程的强加密带来如下好处： 　　1. 可以防止对你的上网行为的偷窥（术语称为“嗅探”） 　　举例： 　　俺博客的读者，大部分都在墙内，因此都是采用翻墙的方式访问本博客。原先 Blogspot 不支持 HTTPS，所以你在俺博客浏览的时候，相关的网络流量，会被翻墙工具看到。如今有了全程 HTTPS 加密，翻墙工具（包括对应的代理服务器或 VPN 服务器）就无法看到你（访问俺博客）的网络流量。 　　2. 可以防范“流量注入”的攻击行为 　　举例： 　　天朝的某些流氓的 ISP 会在你上网的页面中植入广告。他们用的就是“流量注入”的伎俩。 　　一旦你访问的网站是全程 HTTPS 加密的，ISP 就【无法】针对该网站的内容进行注入。

　　HTTPS 的底层实现依赖于 TLS/SSL。具体的技术细节可以参见俺的另一个系列《[扫盲 HTTPS 和 SSL/TLS 协议](https://program-think.blogspot.com/2014/11/https-ssl-tls-0.html)》（该系列尚未写完）

　　除了前面提到的安全性，启用 HTTPS 还有助于 SEO。

　　大约一年前（2014年8月），Google 调整了搜索引擎的算法，提升了 HTTPS 网址的权重。具体介绍参见 Google 的公告（在“[这里](http://googlewebmastercentral.blogspot.com/2014/08/https-as-ranking-signal.html)”）。

　　所以，启用 HTTPS 有助于稍微提升一下你的网站在 Google 搜索结果中的排名。 　　（除了 Google，其它搜索引擎说不定也会采取类似的算法调整）  
　　如果你曾经在浏览器的“书签/收藏夹”中收录了俺博客，你需要重新修改一下博客对应的网址（把 http:// 改为 https://） 　　（其实不改的话，也可以照样打开。但是会多一次跳转，多浪费了你一丁点时间） 　　这次升级之后，如果你发现博客界面或功能有啥异样，恳请给个反馈（到博客留言）。俺先行谢过。 　　（如果你【不是】 Blogspot 上的博主，本节就不用看了） 　　Blogspot 有一个“绑定域名”的功能。很多博主用到了这个功能，把 Blogspot 上的博客内容绑定到自己的域名。 　　根据 Blogger 界面上的提示：在绑定的域名上，【不】支持 HTTPS 的访问。 　　因为俺博客没有绑定到自己的域名，所以这个限制与俺无关。（当年开博时，因为担心泄露身份，没有购买自己的域名） 　　根据俺这两天的观察，发现如下几个问题，有可能是 Blogspot 系统本身的 Bug。 　　1. 　　以 HTTPS 方式打开某篇博文，博文评论中的用户头像，有少数还是通过 HTTP 方式载入。这种情况下会导致浏览器给出警告（对于 HTTPS 加密页面中含有非加密的内容，比如图片，浏览器都会在地址栏显示一个警告）。 　　2. 　　使用 HTTPS 方式调用评论的 API，得到的 JSON 格式中，某些用户头像的网址，依然是 http:// 开头的。 　　这几个问题，可能会在几天之后被修复，也可能会一直存在。 　　俺等不及问题的修复，直接去改了“HTML 模板”中的一段 JS 脚本（这段脚本与加载评论有关），把头像的网址强制替换为 https:// 开头。

　　如果你也碰到类似问题，可以参考俺的修改——查看俺博客页面源代码，然后搜索：**Avatar URL force HTTPS** （只要略懂 JS 代码，应该能看明白）

  
  
　　这是一个 Web 工具，网址是：[https://www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/) 　　该工具可以用来测试任何一个支持 HTTPS 的网站，并给出很详细的技术评估结果（包括潜在的安全隐患）。  
　　经某热心读者提醒，顺便再推荐一个浏览器扩展——[HTTPS Everywhere](https://en.wikipedia.org/wiki/HTTPS_Everywhere) 　　如果某个网站同时支持 HTTPS 和 HTTP（并且该网站包含在它的 ruleset 中），它会强制用 HTTPS 方式访问。

　　该扩展同时提供 [Firefox 版本](https://addons.mozilla.org/en/firefox/addon/https-everywhere/) 和 [Chrome 版本](https://chrome.google.com/webstore/detail/https-everywhere/gcbommkclmclpchllfjekcdonpmejbdp)。

　　补充说明：

　　为啥 HTTPS Everywhere 要依靠一个规则集，为啥不对任何网站自动检测是否有 HTTPS？其官网的回复在“[这里](https://www.eff.org/https-everywhere/faq#faq-Why-use-a-whitelist-of-sites-that-support-HTTPS?-Why-can%27t-you-try-to-use-HTTPS-for-every-last-site,-and-only-fall-back-to-HTTP-if-it-isn%27t-available?)”

**俺博客上，和本文相关的帖子（需翻墙）**：

  
[扫盲 HTTPS 和 SSL/TLS 协议](https://program-think.blogspot.com/2014/11/https-ssl-tls-0.html)（系列）

