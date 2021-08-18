---
layout: default
title: '&#8220;如何翻墙&#8221;系列&#65306;双管齐下的赛风3'
date: None
author:
    display_name: 
---

　　话说今年赶巧是辛亥革命100周年，而天朝的中宣部对“革命”二字向来十分忌惮。所以，从9月底“沦陷日”前夕一直到现在，GFW 就没消停过。以前俺一直推荐大伙儿使用的自由门，近期虽然发布了 7.1.8、7.1.9和7.2.0这几个新版本，但是都不给力。俺在9月30日写了《[扫盲 VPN 翻墙——以 Hotspot Shield 为例](https://program-think.blogspot.com/2011/09/gfw-vpn-hotspot-shield.html)》一文，结果10月10日下午，Hotspot Shield就英勇牺牲。好在半年前介绍的“[世界通+Skype](https://program-think.blogspot.com/2011/05/through-gfw-with-skype.html)”依然坚挺，只是偶尔会掉线（从掉线的时间分布判断，可能是用的人太多导致）。但是大伙儿要牢记：在天朝从事翻墙运动，千万不能在一棵树上吊死。为了让大伙儿多一条翻墙的路，今天再来普及另外一款翻墙工具——赛风。  
　　赛风是由多伦多大学的[公民实验室（Citizen Lab）](http://citizenlab.org/)搞出来的一款翻墙软件，专门用来帮助各国网民突破政府的网络限制和网络审查。赛风的官网在“[这里](http://psiphon.ca/)”，可惜是洋文的。 　　早期的赛风2是纯网页代理，只有服务端软件，没有客户端软件。前不久推出赛风3之后，开始提供客户端软件。你只要在自己的电脑上运行客户端，就可以翻墙。  
  
　　为啥说赛风是双管齐下捏？因为它同时支持 VPN 翻墙和代理翻墙。（尚不清楚这两者区别的同学，请看俺在《[如何翻墙](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)》一文的扫盲）这种玩法在翻墙界比较少见，可以说是赛风3的一大特色。具体的操作后面会介绍。 　　赛风的客户端是绿色软件，无需安装。它只有一个300多 KB 的 EXE 文件，堪称小巧。而且这个 EXE 文件带有数字签名。简单验证一下数字签名，就可以确保该文件没有中毒或者被恶意篡改。 　　赛风的界面极其简单，没有任何可配置的东西。你只需用鼠标双击 EXE，把它运行起来，就 OK 了。如果它运行在 VPN 模式，你连浏览器都无需设置；如果它运行在代理模式（SSH 模式），你顶多只要设置一下浏览器的 HTTP 代理。  
　　最后，非常难能可贵的是，该软件还是开源滴，遵循 GPL 协议。虽然目前“赛风3”的客户端目前只有 Windows 版本，相信不久就会有热心网友通过改造源代码，把它移植到 Linux 系统和 Mac OS 系统。如果你用的是苹果系统或者 Linux 系统，暂时可以采用 [Wine](http://www.winehq.org/) 来运行赛风。  
　　赛风3的获取，也很简单。你只需往赛风官网提供的邮箱 **`get@psiphon3.com`** 发送任意邮件，即可收到自动回复。以前，自动回复的邮件仅仅包含下载链接（而且链接往往被 GFW 封杀）；如今，**自动回复的邮件直接就附上了赛风**的可执行程序（邮件里的附件名叫 `psiphon3.asc`，改为 `psiphon3.exe` 即可直接运行）。 　　说到发邮件，俺又要啰嗦了。千万别用国内的邮箱发，容易被墙而且不安全。国内那几大门户网站，迫于党的淫威，都会配合党的走狗进行邮件内容的审查。国外的邮件，俺首先推荐 Google 的 Gmail 邮箱，其次可以用微软的 Hotmail 或 Outlook 邮箱。 　　先说明一下，赛风【无需管理员权限】即可运行。这下，喜欢上网吧的同学有福了。 　　你用鼠标双击 EXE 文件之后，会出现如下界面。左上角的箭头不停旋转，表示在尝试连接。

![不见图 请翻墙](https://lh3.googleusercontent.com/r_Rt2wpOm5GqXKJzRQnVGlhwHpqx0RvSGTTt1QRC0vNNpZYo5XzBxkNHr0jAmkUPdjFWNuveo23R5wk4n4hn9Ckd1GB8J2sboIKJ3M7oRVs_Oe4ROt6t09ZjCvKorsuKlmQ)

  
  
　　如果 VPN 连接成功，会出现如下界面。左上角的图标变为绿色，且有 VPN 字样。这时候，你电脑中的每一个网络软件（包括浏览器、聊天软件、邮件软件）**无需任何设置**，即可通过 VPN 翻墙。非常爽！  

![不见图 请翻墙](https://lh4.googleusercontent.com/PHj9r-uhPmVuN-b-BxFknhWeSCERoVdi-MfbUab2F0-59Tbh3dturUtH2rgadXXVuHm7QSpwdrqxm1rcIy9Zwgy5_ecZP5grSAPaASlLSadXhhk6Hf408ndHbi7XQ81QktA)

  
　　万一 VPN 连不上，它会尝试用 SSH 方式连接墙外的赛风服务器。连接成功后，出现如下界面。左上角的图标变为绿色，且有 SSH 字样。

![不见图 请翻墙](https://lh4.googleusercontent.com/2mgqIJmb7MiYvNxKq15qca6EM0gtpIR3WaOca9xi0YtaHvQxQNpOMpA8h0R6sh4tFOppCyEtRqcVjlQoDHep6sWi0HqU8GLHLGSOl8wk3jSWNP_kxYRUH_f06TqPuRLutPY)

　　这时候，你只需把浏览器的 HTTP 代理设置成如下，即可浏览墙外的风景。

地址 `127.0.0.1`

  
端口 `8080` 　　在代理模式下，赛风3还支持 SOCKS 代理。打个比方，假如想让某个聊天软件通过赛风3翻墙，只需把聊天工具的 SOCKS 代理设置成如下：

地址 `127.0.0.1`

  
端口 `1080` 　　除了“聊天工具”，其它很多类型的网络软件，只要该软件支持 SOCKS 代理的，配置都大同小异。  
　　今天提到的某些内容，会增加到俺写的翻墙扫盲教程——《[如何翻墙](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)》以及《[常见翻墙问题答疑](https://program-think.blogspot.com/2011/09/gfw-faq.html)》。这两份文档，俺会不定期更新，力图做到与时俱进。  
　　另外，如果你是一位翻墙的新手，在看完本文之后，最好也看一下俺写的翻墙扫盲教程——《[如何翻墙](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)》。 　　如有其它翻墙方面的疑问，也可以到俺博客留言。 　　最后，祝大伙儿早日掌握各种翻墙姿势，呼吸到互联网上自由的空气！

**俺博客上，和本文相关的帖子（需翻墙）：**

  
[如何翻墙](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)（传说中的扫盲教程，定期更新）  
[常见翻墙问题答疑](https://program-think.blogspot.com/2011/09/gfw-faq.html)（传说中的 FAQ，定期更新）  
[获取翻墙软件方法大全](https://program-think.blogspot.com/2011/03/how-to-get-gfw-tools.html)（教你在无法翻墙的情况下拿到翻墙软件）  
[扫盲 VPN Gate——分布式的 VPN 服务器](https://program-think.blogspot.com/2013/04/gfw-vpngate.html)  
[关于 TOR 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)  
[自由門——TOR 被封之后的另一个选择](https://program-think.blogspot.com/2010/03/choose-free-gate.html)  
[新版本无界——赛风3失效后的另一个选择](https://program-think.blogspot.com/2011/12/gfw-wujie.html)  
[扫盲 VPN 翻墙——以 Hotspot Shield 为例](https://program-think.blogspot.com/2011/09/gfw-vpn-hotspot-shield.html)  
[戴“套”翻墻的方法](https://program-think.blogspot.com/2009/09/break-through-gfw-with-tor.html)  
[简单扫盲 I2P 的使用](https://program-think.blogspot.com/2012/06/gfw-i2p.html)

