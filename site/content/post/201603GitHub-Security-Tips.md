---
layout: default
title: '使用 GitHub 的几种方式&#8212;&#8212;兼谈安全性和隐匿性的经验'
date: None
author:
    display_name: 
---

　　先告诉大伙儿一个好消息：  
　　前几天俺把《太子党关系网络》开源到 GitHub 之后，头两天就获得大量网友的关注，以至于[俺这个项目](https://github.com/programthink/zhao)至少连续两天排到了 GitHub 的“每日 Trending”（这个排名汇总的是：每一天全球关注程度最高的那几个项目） 　　非常感谢捧场的 GitHub 用户！！！  
　　俺在博客上不止一次提到过，GitHub 是可以【免翻墙】使用的，而且这个网站/公司的管理层，相对来说还是比较靠谱的，不会轻易向咱们朝廷妥协。 　　因此，GitHub 非常适合用来搞一些敏感的活动（比如：提供翻墙工具、对朝廷/权贵的爆料、等等）

　　比如俺就[利用 GitHub 开源了《太子党关系网络》](https://github.com/programthink/zhao)，并提供下载。

　　如果你想用 GitHub 这个平台开发翻墙工具，本文值得你参考。 　　亦或者你也想效仿俺，在 GitHub 上进行反党活动/反政府活动，那本文更加值得你参考。 　　先举个反面教材，来说明本文的必要性及重要性。 　　前些年有一款很知名的翻墙工具叫做“Shadowsocks”。这个工具是开源在 GitHub 上的，用的人很多。 　　但是该项目的作者 clowwindy 非常缺乏安全意识，【没有】做好身份的隐匿。结果捏，大约半年前，项目作者 clowwindy 被六扇门叫去喝茶。期间估计受到相当程度威胁恐吓，以至于 clowwindy 后来把 GitHub 上的项目关闭了。 　　俺假定本文的读者已经了解如下几个方面的知识：

> 版本管理系统的基本概念 Git 的基本概念 GitHub 的基本使用（至少已经注册过帐号） Git 客户端的基本使用 Linux 或 Mac OS 命令行的基本使用
> 
> 常见翻墙工具的基本使用（不懂的同学，可以看[俺博客上](https://program-think.blogspot.com/)的各种教程）
> 
>   
> Tor 的使用（本文会重点聊到 Tor，俺写的 FAQ 在“[这里](https://program-think.blogspot.com/2013/11/tor-faq.html)”）

  
　　这是最基本的使用方式。只要你注册过 GitHub 帐号，自然就知道如何用浏览器访问它。 　　这种基于浏览器的方式，有时候也称之为“Web 方式”。 　　除了浏览器方式，你还可以通过 Git 客户端软件来操作 GitHub 上的代码仓库。这种方式称之为“客户端软件方式”（为了打字省力，以下简称“Client 方式”） 　　B/S 方式最大的好处是：无需安装额外的软件（通常而言，你的系统中已经有默认的浏览器可供使用）。 　　B/S 方式的另一个好处是：GitHub 几乎所有的功能，都可以在浏览器界面上搞定。 　　但是 B/S 方式也有如下一些缺点：

　　**1\. 安全性**

　　如果你经常在某个系统的某个浏览器上操作你的 GitHub 帐号。一旦该系统被入侵，很可能导致你的 GitHub 帐号也被入侵。

　　**2\. 易用性**

　　有些大批量的操作，在 Web 界面上不太好搞。比如俺前几天上线的项目【太子党关系网络】，里面涉及到上千个文件（包括文本文件，图片文件）。如果通过 Web 界面进行批量操作（添加、删除、改名），就会很麻烦。 　　相比之下，“Client 方式”正好可以弥补“Web 方式”的这几个缺点。至于如何弥补，下面会聊到。 　　当你通过“client 方式”访问 GitHub 的服务器，可以走几种不同的协议。下面俺简要聊聊。 　　此种协议，顾名思义，是 Git 专有的协议。除了用于 Git 客户端与服务端之间的通讯，其它场合用不到它。 　　注意：Git 协议本身是明文的（无加密）。 　　HTTP 协议，大伙儿应该都熟悉，俺就不浪费口水了。 　　HTTPS 协议，通俗地说就是：“加密的 HTTP”。如今很多网站都开始支持 HTTPS（包括俺博客所在的 Blogspot，从去年10月也开始支持 HTTPS）。大伙儿对它应该也不陌生。 　　这个协议，对技术菜鸟可能比较陌生。这玩意儿，早先是 Unix 系统管理员用来远程管理服务器的。 　　SSH 是“Secure Shell”的缩写。显然，这玩意儿是加密的。  
　　前面说了，此协议【没有】加密。如果你关注安全性，不应该用它。 　　首先，明文传输的协议，很容易遭受“旁路嗅探”（sniffer）——导致你丧失数据的【保密性】； 　　其次，明文传输的协议，很容易在传输过程中被修改（恶意篡改）——导致你丧失数据的【完整性】。 　　明文的 HTTP 协议，同样【不】应该使用。理由同上，不再罗嗦。 　　HTTPS 是加密协议，避免了前两个的弊端。 　　它还有如下几个优点：

　　**1\. 访客身份也可以使用**

　　即使你没有注册 GitHub 的用户，也可以通过 HTTPS 协议克隆某个项目

　　**2\. 更容易穿透防火墙**

　　很多公司内网的防火墙会屏蔽大部分端口，但是 HTTPS 所用的 443 端口通常是允许通过的（没有屏蔽）。 　　与 HTTPS 类似，SSH 也是【强加密】滴。该协议提供了如下几个额外的好处：

　　**1\. 提供了额外的认证方式**

　　对于 SSH 协议，GitHub 支持“公钥方式”（public key）的认证。当你设置好这种认证方式，就【不再需要】用你的帐号和密码，也可以操作你代码仓库。 　　这样的好处是——万一你的系统被入侵，顶多泄露你的 key，但【不会】泄露你在 GitHub 的帐号密码。而且 key 被泄漏之后，你可以去你账户的配置界面，把已经泄露的 key 撤销掉。撤销之后，入侵者就算拿到这个 key，也无法再操作你的代码仓库了。

　　**2\. 支持“项目级”颗粒度的控制**

　　通俗地说就是：你可以为不同的仓库配置不同的 SSH key。如此一来，一个 key 只能操作一个代码库。一旦 key 泄露，损失就小得多了。 　　在 Git 客户端支持的这几个协议中，俺重点来说一下 SSH 协议的配置。 　　以下配置以 Linux 环境来举例。 　　大部分知名的 Linux 发行版，其官方的软件库中都已经内置了【openssh】这个软件，你只需用该发行版提供的软件包管理器，一个命令就可以把 openssh 装好。 　　使用如下命令创建：

ssh-keygen -t rsa -b 4096 -f 文件路径 -C 邮箱地址

　　稍微解释一下：  
其中的 `-t rsa` 表示加密算法的类型是 RSA  
其中的 `-b 4096` 表示密钥是 4096 位/比特 （请注意，不同加密算法的位数，没有可比性。对于 RSA 加密算法，如果你没有指定 -b 参数，则默认值是 1024；以目前的破解水平，2048 应该够安全了。为了保险起见，咱们这里创建 4096 比特的密钥）  
　　上述命令中的【文件路径】表示：【私钥】文件存放的位置。然后 `ssh-keygen` 会自动在这个路径末尾附加 `.pub` 作为【公钥文件】的路径。  
　　比如说：你输入的私钥文件路径是 `~/.ssh/xxxx` 那么生成之后对应的公钥文件的路径就是 `~/.ssh/xxxx.pub` 　　如果你要创建不止一个“公钥私钥对”，要使用具有一定可读性的文件名，以免自己搞混了。 　　【私钥文件】非常重要，【不要】泄漏给外人。

　　（经热心读者推荐，补充一篇“保护私钥文件”文章，链接在“[这里](https://martin.kleppmann.com/2013/05/24/improving-security-of-ssh-private-keys.html)”），

　　GitHub 支持两种方式的 SSH key，分别是【用户级】和【项目级】。 　　所谓的【用户级】就是说，使用该 key 可以操作所有项目的代码仓库；而【项目级】的 key 只能操作所属项目的代码仓库。 　　要设置【用户级】的 key，需要先进入“User Profile”页面，然后进入“SSH keys”页面，点击“New SSH key”按钮。 　　要设置【项目级】的 key，需要先进入该项目的“Settings”页面，然后进入“Deploy keys”页面，点击“Add deploy key”按钮。

　　点击完上述按钮之后，你需要把【公钥文件】的内容，【**原封不动地**】 copy & paste 到页面中的那个多行文本框里面。

　　注意事项： 1. 别搞错文件了，需要复制的是【公钥文件】的内容！ 2. 粘贴的时候要小心，【不要】加入多余的空格或多余的回车。 　　如果你当前的系统无需代理就可以访问 GitHub，那么你可以先用命令行测试一下刚才配置好的那个 SSH。 　　运行如下命令：

ssh -i 公钥文件路径 -T git@github.com

　　运行之后，可能会出现如下提示：  

RSA key fingerprint is nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)?

　　你输入 `yes` 以便继续。之后你会看到一句 You've successfully authenticated 就表示该 ssh key 已经通过登录认证。 　　测试通过之后，你可以修改 SSH 的配置文件，就不用每次都在命令行参数中指定密钥文件的路径了。如果你用 SSH 方式操作2个以上的项目，很有必要进行如下定制，可以节省很多命令行输入。

　　SSH 配置文件的路径是： `~/.ssh/config`

　　如果你系统中没有这个文件，就创建一个。然后用你熟悉的文本编辑器修改这个文件。 　　下面俺给出一个示例： 你需要把示例中的“别名”改为你自己起的名字（用一个可读性好点的名字）； 把“私钥文件路径”也同样替换为你本机所使用的文件路径。 其它部分【不要】改动。

Host 别名
  HostName                  ssh.github.com
  Port                      443
  User                      git
  PreferredAuthentications  publickey
  IdentityFile              私钥文件路径

  
　　所谓的“别名”，用来替换 URL 中的主机名。比如俺那个 zhao 项目，俺在 `~/.ssh/config` 中使用的别名就是 zhao 　　之后俺如果要 clone 该项目，只需用如下命令：

git clone ssh://**zhao**/programthink/zhao

看到没？俺在 URL 中就不写 github.com 而改为 zhao，那么 openssh 就会去 `~/.ssh/config` 中找到 zhao 这个配置项，然后用对应的私钥文件进行 SSH 连接， 　　前面几个步骤都搞定之后，你就可以通过 ssh 协议把某个项目 clone 到本地，修改完，最后再 push 到 GitHub 上。整个过程都是通过【强加密的】 SSH 协议完成。  
　　为啥要使用代理？简而言之就是：不让 GitHub 的服务器看到你的公网 IP。 　　看这里，估计某些同学会问了：前面不是说，GitHub 是比较靠谱的公司吗？为啥还担心被它看到（自己的）公网 IP？ 　　俺来回答一下这个问题： 　　即使 GitHub 这个公司的管理层非常靠谱，丝毫不与朝廷合作，也不向朝廷妥协让步。如果让 GitHub 的服务器知道你的公网 IP，（对于高危人士）依然存在如下几种风险：

　　**风险1**

　　GitHub 有一个“Session”功能，可以显示你最近几次登录时使用的【访问者IP】。 　　万一某天你的帐号被入侵了，那么入侵者就可以利用该功能，看你的“访问者IP”，如果你没有走代理，那么你的“访问者IP”也就是本人的“公网IP”

　　**风险2**

　　即使 GitHub 公司的管理层非常有骨气，但是【不】保证该公司所有的员工也都是如此。万一某个服务器管理员被朝廷收买了，或许会把某些用户资料卖给朝廷。 　　（如果你没有走代理）然后六扇门的人就可以通过服务器上记录的“访问者 IP”来定位你的身份。

　　**风险3**

　　即使 GitHub 公司的全体员工都非常有骨气，还有一个风险是：朝廷的御用骇客有可能会入侵 GitHub 的服务器。 　　这可不是俺耸人听闻。即使牛B如 Google，依然在2011年遭遇了天朝御用骇客的【深度渗透】。那次渗透的程度之深，据说入侵者已经接触到 Gmail 的核心服务器，并拿到了几个敏感人士（民运人士）的邮件内容。这次事件后来被称为“极光行动”，此事直接导致了 Google 高层震怒并退出大陆市场。 　　综上所述，如果你是一个【高危】人士，并且通过 GitHub 进行敏感活动。访问 GitHub 的时候，一定要【全程代理】。不论你是用 B/S 方式还是 C/S 方式都要牢记这点。  
　　**代理有很多种，俺强烈建议用【基于 Tor 的双重代理】**。  
　　为啥俺特别强调用【Tor】，并且还强调要用【双重代理】，其中的技术分析，可以参考《[“如何翻墙”系列：关于 Tor 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)》。 　　由于那篇 FAQ 已经说得很具体了，俺在这里就不重复罗嗦了。简而言之，这么干可以极大增加追踪者对你进行逆向追溯的难度。追踪者的难度越大，你就越安全。

　　（关于“双重代理”的扫盲教程，可以参见《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》系列博文的其中一篇）

  
　　这种方式最简单——就跟你翻墙访问其它网站类似——只需要让你的浏览器通过 Tor 的线路访问 GitHub 的页面，就 OK 了。

　　没用过 Tor 的同学，先去看俺的扫盲教程《[戴“套”翻墻的方法](https://program-think.blogspot.com/2009/09/break-through-gfw-with-tor.html)》。

　　对于这种方式，你需要修改 Git 的配置参数，让 Git 知道 Tor 代理的 IP 和 端口。 　　具体的配置命令如下：

git config --global http.proxy SOCKS5h://代理地址:端口号

注意1：  
假如你的 Tor 客户端运行在【**本机**】，那么上述命令中的“代理地址”就替换为： `127.0.0.1` 否则就替换为：运行 Tor 客户端的主机的 IP 地址。 注意2：

如果你的 Tor 客户端用的是【**Tor Browser**】，“端口号”必须用 `9150`

  
如果你用的是 Tor 的其它软件包（比如：Tor Expert Bundle），则“端口号”使用 `9050` 　　要让 SSH 通过 Tor 的代理，稍微麻烦一点。因为 Tor 默认提供的是 SOCKS 代理，而 OpenSSH 客户端默认又【不】支持 SOCKS 代理。 　　因此，得依靠第三方的工具，来实现“SSH through SOCKS”。 　　这里要提醒一下列位看官： 　　俺说的是“SSH through SOCKS”，而【不是】“SOCKS through SSH”（这两者完全不同） 　　为了搞定“SSH through SOCKS”，俺选用大名鼎鼎的 netcat（俗称“网猫”）。 　　由于这个 netcat 名气很大，主流 Linux 发行版的软件仓库中都有它。你只需要用发行版自带的软件包管理器，把 netcat 装上。 　　说到 netcat，有一个“原版的”以及非常多的【变种】。“原版的 netcat”【不】支持代理，必须用某些支持代理的【变种】。俺推荐的是 OpenBSD 社区开发的 netcat 变种（也叫“OpenBSD netcat”或“netcat-openbsd”）。 　　如何判断你是否装对了捏？ 　　在装好 netcat 之后，先运行如下命令（命令中的 nc 就是 netcat 的缩写）。如果输出的第一行能看到 OpenBSD 这个单词，就说明你装对了。

nc -h

　　接下来，用如下命令测试“SSH through Tor SOCKS”是否成功。

ssh -o "ProxyCommand=nc -X 5 -x 代理地址:端口号 %h %p" -T ssh.github.com

注意1：  
假如你的 Tor 客户端运行在【**本机**】，那么上述命令中的“代理地址”就替换为 `127.0.0.1` 否则就替换为：运行 Tor 客户端的主机的 IP 地址。 注意2：

如果你的 Tor 客户端用的是 **Tor Browser**，“端口号”必须用 `9150`

  
如果你用的是 Tor 的其它软件包（比如：Tor Expert Bundle），则“端口号”使用 `9050`

　　上述测试命令如果最终显示 Permession denied 就说明已经通过 SOCKS 代理连接到 GitHub 了（也就是说，你的 SSH 已经能够走 SOCKS 代理联网了）。

　　如果没有显示这个信息，而是显示了其它其它信息，你再用如下命令重新试一次

ssh -o "ProxyCommand=nc -X 5 -x 代理地址:端口号 %h %p" -Tv ssh.github.com

这次俺加了一个 v 选项，可以打印出详细的诊断信息（不过都是洋文）。如果你略懂洋文并略懂网络技术，或许能判断出错的原因所在。

　　搞定之后，为了方便起见，同样可以把 SSH 的这个 `ProxyCommand` 命令行选项加入到 SSH 的配置文件。如此一来，以后每次你要连接 GitHub 的服务器，都会自动走 Tor 提供的 SOCKS 代理。

  
　　前面俺已经给出了 SSH 配置文件的示例，俺把之前那个示例文件，加上 `ProxyCommand` 选项之后，变为如下  

Host 别名
  HostName ssh.github.com
  Port 443
  User git
  PreferredAuthentications publickey
  IdentityFile 私钥文件路径
  ProxyCommand **nc -X 5 -x 代理地址:端口号 %h %p**

　　**注意1：**  
　　假如你的 Tor 客户端运行在【本机】，那么上述命令中的“代理地址”就替换为 `127.0.0.1` 　　否则就替换为：Tor 客户端所在主机的 IP 地址。

　　**注意2：**

  
　　如果你的 Tor 客户端用的是 **Tor Browser**，“端口号”必须是 `9150`  
　　如果你用的是 Tor 的其它软件包，则“端口号”使用 `9050` 　　引申阅读：

　　如果你对 netcat 感兴趣，可以参考博文《[扫盲 netcat（网猫）的 N 种用法——从“网络诊断”到“系统入侵”](https://program-think.blogspot.com/2019/09/Netcat-Tricks.html)》

  
　　要想做到【彻底隐匿】，你需要从一开始就是隐匿的。 　　所以，当你注册 GitHub 的时候，就得用【基于 Tor 的双重代理】进行注册。俺当年注册 GitHub 就是这么干滴。 　　最好不要公开你的邮箱，这样可以避免一些不必要的风险。

　　你可以在 GitHub 的用户配置界面中，设置自己的邮箱地址为“私密”。具体操作步骤参见 GitHub 官方的帮助（链接在“[这里](https://help.github.com/articles/keeping-your-email-address-private/)”）

　　由于俺前面介绍了基于 SSH 客户端操作 GitHub，当你把邮箱地址设置为【私密】之后，你记得设置一下 git 客户端的 email 选项（命令如下）

git config --global user.email 名称@users.noreply.github.com

　　把上述命令中的“名称”替换为你在 GitHub 上的帐号名。  
　　经过上述命令设置之后，别人看你的提交历史，看到的是类似与 `xxxx@users.noreply.github.com` 这样的邮箱地址，看不到你真实的邮箱地址。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》（系列）  
《[“如何翻墙”系列：关于 Tor 的常见问题解答](https://program-think.blogspot.com/2013/11/tor-faq.html)》  
《[“如何翻墙”系列：戴“套”翻墻的方法](https://program-think.blogspot.com/2009/09/break-through-gfw-with-tor.html)》  
《[扫盲 Arm——Tor 的界面前端（替代已死亡的 Vidalia）](https://program-think.blogspot.com/2015/03/Tor-Arm.html)》  
《[如何用 Privoxy 辅助翻墙？](https://program-think.blogspot.com/2014/12/gfw-privoxy.html)》  
《[扫盲 netcat（网猫）的 N 种用法——从“网络诊断”到“系统入侵”](https://program-think.blogspot.com/2019/09/Netcat-Tricks.html)》  
《[【太子党关系网络】开源到 GitHub——大伙儿一起来曝光赵国权贵](https://program-think.blogspot.com/2016/02/Zhao-at-GitHub.html)》

