---
layout: default
title: '如何用 Privoxy 辅助翻墙&#65311;'
date: None
author:
    display_name: 
---

　　简而言之，Privoxy 是一款功能很强的，开源的，跨平台的 HTTP 代理工具。

　　其官网链接在“[这里](https://www.privoxy.org/)”；其维基百科的词条在“[这里](https://en.wikipedia.org/wiki/Privoxy)”。

  
　　从表面上看，Privoxy 只是一个 HTTP 代理。但是它提供了非常强大的【定制功能】。利用这些定制功能，可以完成很多你意想不到的事情。 　　简单列举一下，Privoxy 【至少】可以实现如下功能：

　　**1\. 根据定制的规则，进行代理转发（链式代理）**

　　在咱们天朝，这个功能主要是用来辅助翻墙。 　　先说明一下：此处提及的“链式代理”（洋文是“a chain of multiple proxies”），跟俺经常提及的“多重代理”，【不是】一回事儿。

　　这个“链式代理”，有时候也可以称之为“代理转发”。它跟“端口转发”有点类似（关于“端口转发”，俺在前两年的博文《[多台电脑如何共享翻墙通道](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)》中有介绍，不清楚的同学可以去看一下）。差别在于，“端口转发”工作在 TCP 层面（传输层），而 Privoxy 的“代理转发”工作在传输层之上（通常是“应用层”）。

　　这方面的功能，是本文重点要聊的。

　　**2\. 根据定制的规则，修改 HTTP 页面的内容**

　　这个功能主要是用来优化网页。比如“去除广告，精简页面，美化布局”等等。 　　（今天暂且不谈这方面的功能）

　　**3\. 根据定制的规则，修改 HTTP Header 的字段**

　　Privoxy 既可以修改 HTTP Request 的 Header，也可以修改 HTTP Response 的 Header。 　　这个功能有助于保护隐私。比如“禁用 cookie、限制 cookie 的生命周期、伪装 User Agent”等等。 　　（今天暂且不谈这方面的功能）

　　**4\. 根据定制的规则，对网络传输做一些优化**

　　比如“共享 TCP 连接”。 　　（今天暂且不谈这方面的功能） 　　刚才说的是功能特性，再来说一下其它的几个特性。 1. Privoxy 是完全开源的（采用的是 GPL 开源协议） 2. Privoxy 能够很好地跨平台（至少支持：Windows、Linux、Mac OS X、各种 UNIX） 3. Privoxy 很轻量级（看看它的安装包就晓得，不到 1MB） 4. Privoxy 是老牌的（诞生于2001年），用户很多，口碑不错。因此，安全性/稳定性/可靠性等方面有保障。 　　光靠 Privoxy 自己，是无法翻墙的——Privoxy 虽然能提供 HTTP 代理，但是 Privoxy 自己并【没有】对应的“代理服务器”。它仅仅是一款“客户端的代理工具”。 　　所以，本文标题用的是“辅助翻墙”——意思是说，Privoxy 起的是【辅助作用】。 　　（考虑到大部分读者用的是 Windows，所以俺拿 Windows 环境来说事儿；至于用 Linux 的同学，主流发行版的软件包应该都包含了 Privoxy，无需上 Privoxy 官网就可以安装）

　　用 Windows 的同学，到“[官网首页](https://www.privoxy.org/)”直接可以找到“下载页面”。进入该页面，然后选操作系统（Windows 用户就选 Win32）；然后再选版本（通常选最新的【稳定】版）。

　　选完 Win32，再选版本号。通常就选最新版本（截止俺写本文时，最新版本是 3.0.22）。话说 Privoxy 的版本跟其它软件不太一样——它在2002年就已经是 3.0.0 版本。这么多年，才升到 3.0.22，真够慢的。 　　选完版本号，然后你可以下载“exe 格式”或“zip 格式”。如果是“exe 格式”，就是一个安装文件，双击就可以安装（安装过程很容易，俺就不详述了）；如果你选“zip 格式”，就是一个【绿色免安装】的压缩包。你把这个 zip 随便解压到某个目录下，就可以用了。 　　俺本人比较喜欢“绿色软件”，所以每次都下载“zip 格式”。  
　　Privoxy 默认安装好就可以使用了。它默认会开启 HTTP 代理，端口号是 `8118`，绑定在 `127.0.0.1` 这个地址。 　　你把浏览器的 HTTP 代理作相应的设置，浏览器就会走 Privoxy 的 HTTP 代理。

　　为了检验你的浏览器是否正确配置了 Privoxy 的代理，你可以在浏览器的地址栏输入 `http://p.p/` 并回车。如果浏览器的页面上出现 Privoxy 的相关信息，说明你的浏览器已经走 Privoxy 的 HTTP 代理。

　　先介绍几个最基本的配置语法。难度不大，技术菜鸟应该也能看懂。

　　如果你喜欢折腾并且稍微懂点 IT 技术，不满足于俺介绍的“基本配置”，可以自行查看 Privoxy 的[官网文档](https://www.privoxy.org/user-manual/)，了解它的“高级配置”（比如：“Action”和“Filter”）。

　　前面说了——Privoxy 的定制功能超强，所以它的配置文件也不少。如果你是技术菜鸟，或者你只想了解“基本配置”，那么就只需要去编辑它的“主配置文件”。

　　**主配置文件**

  
　　对于 Windows 系统，主配置文件放置在跟 `privoxy.exe` 相同的目录下，文件名为 `config.txt`  
　　对于“Linux/Unix”，主配置文件放置在 `/etc/privoxy` 目录下，文件名为 `config`  
　　Privoxy 的配置文件，都是纯文本文件。如果某一行是以 井号 `#` 开头，说明这行是注释。 　　先来说最最基本的配置——设定 Privoxy 的监听端口号和绑定的地址。 　　介绍这个的目的，是让你先稍微熟悉一下——如何修改 Privoxy 的主配置文件。因为后面的定制，需要经常去修改它。

　　Privoxy 的监听端口号，默认是 `8118`，默认绑定的地址是 `127.0.0.1`（这个地址代表“当前系统的地址”）。由于默认是绑定在 `127.0.0.1` 这个地址，所以只有当前系统的软件才可以连接到 Privoxy 的监听端口。

  
　　如果你希望其它操作系统的软件也可以连接到 Privoxy 的监听端口，可以修改绑定的地址，把 `127.0.0.1` 改为 `0.0.0.0` 表示绑定在“任意地址”。 　　操作步骤如下： 　　找到“主配置文件”，用你比较顺手的文本编辑器打开，在尾部增加如下一行

listen-address  0.0.0.0:8118

　　如果你不喜欢 `8118` 这个端口号，也可以换成别的。  
　　修改完之后，启动 Privoxy，然后在命令行使用 netstat 命令，就可以看到多出来一个 `8118` 的端口（关于 netstat 的使用，可以参见《[多台电脑如何共享翻墙通道](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)》）。 　　刚才那个只是热身，下面来一个稍微复杂点的——“链式代理/代理转发”。 　　关于“链式代理/代理转发”的概念，本文开头部分已经大致解释了。这里就不再重复罗嗦了。 　　所谓的“HTTP 代理转发”就是说：Privoxy 把自己收到的 HTTP 请求转给另一个 HTTP 代理，再由该代理转到你最终访问的网站。 　　大致示意图如下（今天偷个懒，只画了“基于字符的示意图”）：

　　　｜＝＝＝＝＞｜　　　　　　　｜＝＝＝＝＞｜　　　　　　｜＝＝＝＝＞｜
浏览器｜　　　　　｜Ｐｒｉｖｏｘｙ｜　　　　　｜ＨＴＴＰ代理｜　　　　　｜目标网站
　　　｜＜＝＝＝＝｜　　　　　　　｜＜＝＝＝＝｜　　　　　　｜＜＝＝＝＝｜

示意图中的 ＝＝＝＝＞ 表示 HTTP 请求 示意图中的 ＜＝＝＝＝ 表示 HTTP 响应 　　HTTP 代理转发的语法如下（把该语法添加在“主配置文件”尾部）：

forward  target\_pattern  http\_proxy:port

　　语法解释： 　　该命令分3段，各段之间用空格分开（可以用单个空格，也可以多个空格）

　　第1段的 `forward` 是固定的，表示——这是 HTTP 转发

  
　　第2段的 `target_pattern` 是个变量，表示：这次转发只针对特定模式的 HTTP 访问目标  
　　第3段的 `http_proxy:port` 也是变量，表示：要转发给某个 HTTP 代理（IP 冒号 端口）。如果“第3段”只写一个单独的小数点，表示直连（不走代理）。

　　**举例1**

  

forward  /  127.0.0.1:8080

　　上述这句表示：  
把所有的 HTTP 请求都转发给本机（`127.0.0.1` 表示本机）的 `8080` 端口  
`target_pattern` 设置为“单个斜线”，表示匹配【所有 URL 网址】

　　**举例2**

  

forward  .google.com/  127.0.0.1:8080

　　上述这句表示：  
如果 HTTP 请求是发送给 `.google.com` 这个域名的下级域名，那么就把该 HTTP 请求转发给本机（`127.0.0.1` 表示本机）的 `8080` 端口  
使用 `.google.com` 这种（以小数点开头的）写法，可以匹配如下这类域名：  

> www.google.com mail.google.com plus.google.com
> 
> ......

（以此类推） 　　补充说明：

　　对于本例子，`target_pattern` 变量是 `.google.com/` 这个写法表示：该变量只匹配域名，【不】匹配网页的路径。

　　根据 Privoxy 的语法规则，最末尾的斜线可以省略。因此，本例子也可以等价地写为如下：

forward  .google.com  127.0.0.1:8080

　　**举例3**  

forward-socks5 .onion localhost:9050 .

　　上述这句表示：  
把顶级域名为 `.onion` 的 HTTP 请求都转发给本机（`localhost` 也可以用来表示本机，相当于 `127.0.0.1`）的 Tor 的 SOCKS 端口。 　　补充说明：

普通互联网的域名，顶级域名【不可能】是 `.onion` 。因为这个顶级域名是专门用于 Tor 暗网的。因此，本例子就是用来转发 Tor 暗网的 HTTP 请求，让 Privoxy 把这类请求转给 Tor 的 SOCKS 端口。

　　所谓的“SOCKS 代理转发”，就是说：Privoxy 把自己收到的 HTTP 请求转给另一个 SOCKS 代理；如果需要的话，还可以由这个 SOCKS 代理再转给另一个 HTTP 代理。

　　**示意图1**（先转发到 SOCKS 代理，然后转到目标站）

  

　　　｜＝＝＝＝＞｜　　　　　　　｜＝＝＝＝＞｜　　　　　　　｜＝＝＝＝＞｜
浏览器｜　　　　　｜Ｐｒｉｖｏｘｙ｜　　　　　｜ＳＯＣＫＳ代理｜　　　　　｜目标网站
　　　｜＜＝＝＝＝｜　　　　　　　｜＜＝＝＝＝｜　　　　　　　｜＜＝＝＝＝｜

　　　｜此阶段是　｜　　　　　　　｜此阶段是　｜　　　　　　　｜此阶段是　｜
　　　｜ＨＴＴＰ　｜　　　　　　　｜ＳＯＣＫＳ｜　　　　　　　｜ＨＴＴＰ　｜

  
　　**示意图2**（先转发到 SOCKS 代理，再转发到某个 HTTP 代理，最后才转到目标站）  

　　　｜＝＝＝＝＞｜　　　　　　　｜＝＝＝＝＞｜　　　　　　　｜＝＝＝＝＞｜　　　　　　｜＝＝＝＝＞｜
浏览器｜　　　　　｜Ｐｒｉｖｏｘｙ｜　　　　　｜ＳＯＣＫＳ代理｜　　　　　｜ＨＴＴＰ代理｜　　　　　｜目标网站
　　　｜＜＝＝＝＝｜　　　　　　　｜＜＝＝＝＝｜　　　　　　　｜＜＝＝＝＝｜　　　　　　｜＜＝＝＝＝｜

　　　｜此阶段是　｜　　　　　　　｜此阶段是　｜　　　　　　　｜此阶段是　｜　　　　　　｜此阶段是　｜
　　　｜ＨＴＴＰ　｜　　　　　　　｜ＳＯＣＫＳ｜　　　　　　　｜ＨＴＴＰ　｜　　　　　　｜ＨＴＴＰ　｜

　　SOCKS 代理转发，包括如下几种语法：

forward-socks4   target\_pattern  socks\_proxy:port  http\_proxy:port
forward-socks4a  target\_pattern  socks\_proxy:port  http\_proxy:port
forward-socks5   target\_pattern  socks\_proxy:port  http\_proxy:port
forward-socks5t  target\_pattern  socks\_proxy:port  http\_proxy:port

　　语法解释： 　　该命令分4段，各段之间用空格分开（可以用单个空格，也可以多个空格）

　　第1段是以 `forward` 开头的，表示 SOCKS 转发的类型。目前支持 4 种类型。

  
前3种（`forward-socks4 forward-socks4a forward-socks5`）分别对应不同版本的 SOCKS 协议（这几个版本的差异，参见“[这篇博文](https://program-think.blogspot.com/2019/04/Proxy-Tricks.html)”）  
最后一种 `forward-socks5t` 比较特殊，是基于 SOCKS5 协议版本，但加入了针对 Tor 的扩展支持（优化了性能）。只有转发给 Tor 的 SOCKS 代理，才需要用这个类型。  
　　第2段的 `target_pattern` 是个变量，表示：这次转发只针对特定模式的 HTTP 访问目标  
　　第3段的 `socks_proxy:port` 也是变量，表示：要转发给某个 SOCKS 代理（IP 冒号 端口）  
　　第4段的 `http_proxy:port` 也是变量，表示：在经由前面的 SOCKS 代理之后，再转发给某个 HTTP 代理（IP 冒号 端口） 第4段如果写成一个单独的小数点，相当于“示意图1”；如果第4段填写了具体的 IP 和端口，相当于“示意图2”。

　　**举例1**

　　如果你本机安装了 Tor Browser 软件包，可以使用如下语法，把 Privoxy 收到的 HTTP 请求转发给 Tor Browser 内置的 SOCKS 代理。

forward-socks5  /  127.0.0.1:9150  .

　　补充说明一下：  
　　Tor Browser 软件包开启的监听端口是 `9150`；如果你用的是 Tor 的其它软件包，需要把上述的 `9150` 端口号改为 `9050`  
（关于 Tor 的不同软件包的差异，参见《[“如何翻墙”系列：关于 Tor 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)》）  
　　VPN 翻墙，大伙儿应该都很熟悉了，俺就不再浪费口水解释了。 　　VPN 翻墙的特点是——只要你系统中的 VPN 通道建立了，那么【整个系统】中的软件，（无需配置）自动就会走 VPN 通道。因此，VPN 有时候也被称为是“系统全局代理”。这是“VPN 式翻墙”相比“代理式翻墙”优越之处。 　　但是 VPN 翻墙有一个缺点，就是不方便共享 VPN 的翻墙通道给【其它系统】。相比而言，“代理式翻墙”很容易跨系统共享翻墙通道。 　　要想解决 VPN 翻墙的这个缺点，Privoxy 再次派上用场。配置步骤如下： 1. 把 Privoxy 跟 VPN 安装到同一个操作系统中。 2.

配置 Privoxy 的监听选项，把监听地址设置为 `0.0.0.0`（表示监听端口绑定到任意地址）

  
至于端口号，你可以直接用默认的 `8118`，也可以自己另选一个（端口号的范围是 1~65535）。 （如何修改 Privoxy 的监听选项，刚才已经提及） 3. 把 VPN 和 Privoxy 都运行起来。确保 VPN 处于联通状态。 4. 配置其它系统中的网络软件的 HTTP 代理。 HTTP 代理的“IP 地址”指向安装 Privoxy 的系统的 IP 地址。 HTTP 代理的“端口号”设置为 第2步 里面配置的端口号。 　　为了傻瓜化一些，举个例子来说明： 　　假设你在电脑上安装了 Tor Browser 软件包，另外还安装了一个聊天工具。你想让这个聊天工具走 Tor 的线路（为了翻墙，或为了提高隐匿性）。但是你比较倒霉，你用的这款聊天工具，只支持 HTTP 代理，不支持 SOCKS 代理。而 Tor Browser 软件包，默认只提供 SOCKS 代理。这可咋办捏？ 　　这时候，Privoxy 就派上用场啦——使用前面提到 “SOCKS 代理转发”。 　　你可以设置聊天工具的 HTTP 代理，指向 Privoxy；然后在 Privoxy 上做些简单的配置（如何配，刚才已经讲过），Privoxy 就可以把聊天工具的 HTTP 请求，转换为 SOCKS 请求，然后通过 Tor 的 SOCKS 代理，传输到聊天服务器。  
　　如今翻墙工具有很多，各有特色。比如基于 Tor 的双重代理（教程参见《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》），隐匿性很强，但是速度不够快；而 GAE 翻墙速度会比较快，但是安全性很不好。 　　那么，如何充分利用不同翻墙工具的特长捏？你可以根据不同的上网情况，发挥不同翻墙软件的特长。 　　比如说，观看 Youtube 视频的时候，就走 GAE 的翻墙通道（GoAgent 之类）；而如果要在网上论坛发表敏感的政治言论，就走“双重代理”的通道。 　　面对这种需求，Privoxy 的特长就体现出来啦。你可以编辑 Privoxy 的主配置文件，让不同网站的网络流量，走不同的翻墙通道。具体的配置语法，也就是本文前面提及的“HTTP 代理转发”和“SOCKS 代理转发”。因为大部分翻墙代理，提供的代理方式，无非就是 HTTP 和 SOCKS 两种。 　　举例——设想如下的使用场景：

　　假设你手头有一个 Tor，已经可以基于 meek 独立联网（meek 的使用可以参考《[Tor 已复活——meek 流量混淆插件的安装、优化、原理](https://program-think.blogspot.com/2014/10/gfw-tor-meek.html)》），专门用来上俺博客发表敏感的政治评论；

  
　　另外，假设你手头还有一个 GAppProxy（GAE 翻墙），在本地开启了 `8000` 端口的 HTTP 代理，专门用来看 YouTube 视频； 　　除了上述两个网站，其它网站你都是直接访问（直连）。 　　那么，你可以使用如下配置，让 Privoxy 帮你进行分流。

forward  /  .
forward  .youtube.com  127.0.0.1:8000
forward-socks5  program-think.blogspot.com  127.0.0.1:9150  .

　　解释如下：  
第1行表示：因为匹配的目标是“单个斜杠” `/` 表示匹配“任意网址”。所以这条可以看成是“默认规则”。（注：“后面的规则”会覆盖“前面的规则”，所以“默认规则”总是写在开头）。  
第2行表示：凡是 `.youtube.com` 的下级域名都走 `127.0.0.1:8000` 的 HTTP 代理（注：以【小数点】开头的域名表示该域名的所有下级域名）  
第3行表示：访问 `program-think.blogspot.com` 站点都走 `127.0.0.1:9150` 的 SOCKS 代理。（注：此行末尾的【小数点】别漏看喽）  
　　（先插一句：很多同学习惯于称呼“代理插件”，其实更准确的叫法是“代理扩展”。关于 Plugin 和 Extension 的差别可以参见《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》系列的[第2篇](https://program-think.blogspot.com/2013/06/privacy-protection-2.html)）  
　　如果你是老读者，并且看过俺写的《[翻墙入门教程](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)》，应该对基于浏览器的“代理扩展”毫不陌生。比较知名的“代理扩展”包括 FoxyProxy 和 AutoProxy。  
　　表面上看，“浏览器的翻墙扩展”也可以达到跟 Privoxy 类似的效果。但是捏，“翻墙扩展”是依赖于具体的某款浏览器（假设你用的是 IE，那么就没法使用 FoxyProxy 和 AutoProxy）。而 **Privoxy 跟浏览器的类型完全无关**，可以跟【任何一款】浏览器结合——这就是 Privoxy 的优势之一。  
　　其次，“翻墙扩展”运行在浏览器内部。万一“翻墙扩展”有后门，会产生严重威胁（比如偷窥到你的密码输入）。而 Privoxy 是独立于浏览器的软件（独立的进程）。Privoxy 无法直接访问到浏览器进程的内存。如果你是个“安全控”，还可以把 Privoxy 和 浏览器 分别装到不同的虚拟机，实现“系统级隔离”。（没听说过“操作系统虚拟机”的同学，可以看俺写的系列《[扫盲操作系统虚拟机](https://program-think.blogspot.com/2012/10/system-vm-0.html)》） 　　本来计划把 Privoxy 的各种功能都介绍一遍。发现篇幅会很长。所以就先介绍和“翻墙”相关的部分。如果大伙儿感兴趣，俺再介绍 Privoxy 的其它用途（隐私保护、屏蔽广告、页面优化）。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[计算机网络通讯的【系统性】扫盲——从“基本概念”到“OSI 模型”](https://program-think.blogspot.com/2021/03/Computer-Networks-Overview.html)》  
《[如何翻墙？](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)》  
《[如何让【不支持】代理的网络软件，通过代理进行联网（不同平台的 N 种方法）](https://program-think.blogspot.com/2019/04/Proxy-Tricks.html)》  
《[多台电脑如何【共享】翻墙通道——兼谈【端口转发】的几种方法](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)》  
《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》（系列）  
《[扫盲操作系统虚拟机](https://program-think.blogspot.com/2012/10/system-vm-0.html)》（系列）  
《[“如何翻墙”系列：关于 Tor 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)》  
《[“如何翻墙”系列：扫盲 Tor Browser 7.5——关于 meek 插件的配置、优化、原理](https://program-think.blogspot.com/2018/04/gfw-tor-browser-7.5-meek.html)》  
《[“如何翻墙”系列：Tor 已复活——meek 流量混淆插件的安装、优化、原理](https://program-think.blogspot.com/2014/10/gfw-tor-meek.html)》

