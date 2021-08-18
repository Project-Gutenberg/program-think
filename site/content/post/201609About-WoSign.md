---
layout: default
title: '老流氓 CNNIC 的接班人&#8212;&#8212;聊聊&#8220;沃通/WoSign&#8221;的那些破事儿'
date: None
author:
    display_name: 
---

　　前一篇博文通告了“评论区的新功能——发帖不刷页面”。该功能上线后，发现了几个严重 Bug，大约在9月3日都已经解决了。 　　在此，向那些帮忙测试帮忙反馈问题的热心读者，表示衷心感谢 :) 俺这个博客走到今天，离不开许许多多热心读者的支持。 　　自从上线了这个功能，俺处理博文评论（尤其是评论很多的博文），效率至少提升了一个数量级。效率提升之后，俺最大的一个感慨是：早就该实现这个功能了 :( 　　另外， 　　为了实现此次的新功能，俺已经对 Blogspot 的评论区界面作了很多改动。所以俺考虑，干脆把 Blogspot 的评论区界面全部替换为俺自己的代码。如果这个能搞定，今后就无需在 Blogspot 评论系统的代码中进行修修补补了。初步计划在“十一假期”来搞这个改造。 　　下面言归正传。 　　最近两周，看到了很多关于沃通的丑闻，再加上也有热心读者建议俺聊聊此事。今天特来发一篇抹黑沃通的博文 :) 　　“沃通”，洋名叫做“WoSign”。简而言之，是咱们天朝的一家数字证书颁发机构。（“数字证书颁发机构”，洋文简称“CA”。为了打字省力，本文以下部分用 CA 来称呼“数字证书颁发机构”） 　　为了让大伙儿更加了解这家 CA 的底细，俺稍微说一下该机构的背景。 　　目前的 CEO 叫做王高华，经过某些网友的人肉搜索，此人曾经担任过【深圳市信息网络中心总工程师】。看样子是从体制内出来滴。 　　“沃通”是由“王高华、张千夫、某个奇虎360全资子公司”三方一起合资成立。这三方，据说是“奇虎360”占大头。这个“奇虎360”，也就是出品“360安全卫士/360杀毒”那家公司。它的老板周鸿祎，那可是流氓中的战斗机。当年就是靠做流氓软件（臭名昭著的“3721上网助手”）而发家的。大伙儿可别小瞧了他。  
　　（对 CA 及证书不太了解的同学，建议先看教程《[数字证书及 CA 的扫盲介绍](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)》） 　　想必大伙儿都听说过 HTTPS 协议（也就是“加密的 HTTP”协议）。如果你正在看俺博客的页面，你只需要瞄一眼浏览器地址栏，这篇博文的网址就是以 https:// 开头滴。 　　HTTPS 的加密，需要依赖于 CA 证书；而 CA 证书就是由 CA 颁发滴。 　　说到这儿，头脑清楚滴读者就已经意识到 CA 有多么重要了。 　　通俗地说，如果某个 CA 不靠谱，那么该 CA 颁发的证书也就不靠谱；如果某个网站使用了这个不靠谱的证书来部署网站的 HTTPS 加密传输，那么这个加密传输也跟着不靠谱了。当 HTTPS 的传输不靠谱，就意味着——加密流量有可能被【偷窥】甚至有可能被【篡改】。

　　（如果你想对 HTTPS 协议有更多的了解，可以看俺的另一个教程《[扫盲 HTTPS 和 SSL/TLS 协议](https://program-think.blogspot.com/2014/11/https-ssl-tls-0.html)》）

　　刚才介绍完背景，可能已经有人感觉到沃通是有问题滴。但是俺不能凭空污人清白，下面咱们要来摆事实，讲道理——介绍一下近期曝光的【沃通丑闻】。

　　话说有个英国程序员 Gervase Markham，他无意中发现了沃通的一些严重问题，并在[Mozilla 的安全讨论组](https://groups.google.com/forum/#!forum/mozilla.dev.security.policy)进行曝光（帖子链接在“[这里](https://groups.google.com/forum/#!msg/mozilla.dev.security.policy/k9PBmyLCi8I/mKSMaz9eCgAJ)”）。

　　他至少提到了三个与沃通有关的严重问题：

　　**问题1**

　　沃通 CA 允许证书申请者选择任意端口进行验证，违反了“限制端口和路径使用”的规定； 　　编程随想点评：这点说明沃通的“合规性”不够，相比后面两个，这已经是小问题了。

　　**问题2**

　　证书申请者如果能证明控制了某个子域名，那么就能获得根域名的证书；

　　已经研究人员利用沃通的这个失误，获得了一张沃通签发的【GitHub 网站主域名的证书】。关于此事的严重性，知乎上有讨论（链接在“[这里](https://www.zhihu.com/question/50298017)”）

　　编程随想点评：一个号称全国最大的 CA，竟然犯如此低级的错误，你觉得这家 CA 可能靠谱吗？

　　**问题3**

　　被沃通并购的 StartCom（也是一家 CA），被发现允许对证书的签署日期进行【倒填】。关于这个“倒填日期”的问题，俺稍微解释一下：

　　由于如今的运算能力越来越强，SHA1 散列算法的【可靠性】越来越【不够】啦（参见“[这篇博文](https://program-think.blogspot.com/2019/07/Security-News.html)”的密码学相关这个章节）。一些主流的浏览器，如果发现2016元旦之后签署的 CA 证书，依然采用 SHA1，会给出警告。

　　沃通的问题在于，它为了帮证书申请人规避浏览器警告，故意把签署日期伪造成2015年底。 　　编程随想点评：CA 象征着【权威认证】机构。如果一家 CA 去玩这种伪造日期的花样，它还有啥节操可言？！

　　**问题4**

　　除了英国程序员曝光的那3个问题，再来说一下其他人曝光的问题—— 　　沃通在2015年4月9日到4月14日之间，签发了392个【相同序列号】的证书。 　　编程随想点评：证书的序列号要确保唯一性。沃通竟然在短短5天之内，签发了几百个【相同序列号】的证书，足见其内部管理有严重问题。

　　**其它问题**

  
　　以上列举的4件事情，仅仅是已经曝光的丑闻的一部分。甚至可能是冰山一角。Mozilla 在其官网列出了沃通目前已经曝光的丑闻（链接在“[这里](https://wiki.mozilla.org/CA:WoSign_Issues)”）。 　　前面聊沃通的家丑，提到了 StartCom，下面俺来介绍一下两者的关系。先看几篇报道：

《[沃通被指秘密收购了StartCom @ solidot](https://www.solidot.org/story?sid=49555)》

  
《[沃通（WoSign）被指秘密收购以色列CA——StartCom @ cnBeta](https://www.cnbeta.com/articles/535661.htm)》  
《[韓國資安研究員踢爆：以色列StartSSL憑證主機竟在奇虎360中國機房 @ iThome](https://www.ithome.com.tw/news/103939)》 　　沃通作为商业机构，并购其它 CA，本来无可厚非的。但是这几篇报道中都提到了一个定语——【秘密】收购。 　　并购国外知名的 CA，本来是很风光的事情，沃通为啥要藏着掖着？这不禁让俺想起了抗日影片中的经典台词——悄悄滴进村，打枪滴不要。 　　沃通是天朝的 CA，其客户主要在国内；而 StartCom 是全球有名的 CA，客户遍布全世界。俺不禁邪恶地猜想：或许沃通想利用 StartCom 来干一些不为人知的勾当。如果真是这样的话，那曾经知名的 StartCom，就跟“沃通”一样，彻底不可信了。 　　聊完“沃通与 StartCom 的关系”，再顺便提一下“沃通”的另一个破事儿——采用“连哄带吓”的招数，诱骗用户放弃国外 CA（Let's Encrypt）颁发的证书，改用沃通的证书。 　　下面是某网友曝光的邮件截屏。

![不见图 请翻墙](https://lh4.googleusercontent.com/lI0CnNEsyoUiI_GbjWTDQwU79uuqjE1RxlYM2T9MXz2KVSuwJwm9mSCwAoP2wcYI7j53zWiniMmUeQ_wNZ44BAY2Jj3chmmZb50ccP00i5_6Bd6eF4bSj_c3v6nDxyUU-SV7FT8ARl4)

　　顺便说一下： 　　被沃通诋毁的【Let's Encrypt】，恰恰是一个比较靠谱的 CA，而且它【不是】商业机构，而是以【公益】的方式普及 CA 证书。向它提供赞助的包括：电子前哨基金会/EFF，Mozilla 基金会，Linux 基金会，思科，Akamai......（都是全球知名的机构）

　　关于它的更多介绍可以参见维基百科“[这里](https://zh.wikipedia.org/wiki/Let%27s_Encrypt)”。

　　（Mozilla 也就是开发火狐浏览器的非盈利组织） 　　由于沃通的家丑外扬，已经有很多热心网友要求 Mozilla 组织对沃通采取行动。所谓的“采取行动”，也就是把 Firefox 中默认内置的“沃通根证书”去掉。 　　假如这么干了之后，那么 Firefox 默认情况下就不再信任“沃通的根证书”，同时也不再信任“由沃通根证书签发的下级证书”。考虑到 Firefox 的市场份额，这对沃通将是一个打击。而且 Google 的 Chrome 也可能会跟进。 　　虽说 Mozilla 已经开始警告沃通，但是大伙儿也不可太乐观。

　　6年前（2010），俺曾经发文[狠批老流氓 CNNIC](https://program-think.blogspot.com/2010/02/about-cnnic.html)，并号召大伙儿[删除它的根证书](https://program-think.blogspot.com/2010/02/remove-cnnic-cert.html)。那之后又过了5年（2015），Mozilla 的 Firefox、Google 的 Android、还有苹果的 Mac OS，才终于把 CNNIC 根证书从信任列表中除掉了（由于被几大厂商拉黑，**如今 CNNIC 官网也【不用】自己的证书，改用国外的证书**，很讽刺吧）

　　如果 Mozilla、Google、微软这些浏览器厂商或操作系统厂商迟迟不采取行动，那么大伙儿就要靠自己动手了。

　　做法很简单——把不靠谱的 CA 证书禁用。具体的操作细节，可以参考俺6年前（2010）的博文《[CNNIC 证书的危害及各种清除方法](https://program-think.blogspot.com/2010/02/remove-cnnic-cert.html)》。当年那篇讲的是如何删除 CNNIC 证书，你只需要依葫芦画瓢就行了。

　　需要提醒一下： 　　你不光要禁用“沃通的所有证书”，还要禁用“StartCom 的所有证书”——前面说了，StartCom 已经被沃通并购。 　　由于沃通的根证书在国内用的比较多，当你禁用了沃通证书之后，访问某些国内网站，浏览器会给出证书警告。如果你嫌每次警告太麻烦，并且你确定该网站是可信的，你只需把当前网站的证书加入可信状态就可以了（沃通根证书依然保持禁用状态）

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[数字证书及 CA 的扫盲介绍](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)》  
《[CNNIC 干过的那些破事儿](https://program-think.blogspot.com/2010/02/about-cnnic.html)》  
《[CNNIC 证书的危害及各种清除方法](https://program-think.blogspot.com/2010/02/remove-cnnic-cert.html)》  
《[扫盲 HTTPS 和 SSL/TLS 协议](https://program-think.blogspot.com/2014/11/https-ssl-tls-0.html)》（系列）  
《[近期安全动态和点评（2019年3季度）](https://program-think.blogspot.com/2019/09/Security-News.html)》  
《[近期安全动态和点评（2019年2季度）](https://program-think.blogspot.com/2019/07/Security-News.html)》

