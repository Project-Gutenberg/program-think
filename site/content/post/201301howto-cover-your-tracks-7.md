---
layout: default
title: '如何隐藏你的踪迹&#65292;避免跨省追捕[7]&#65306;用虚拟机隐匿公网 IP&#65288;配置图解&#65289;'
date: None
author:
    display_name: 
---

　　4天前发布了《用虚拟机隐匿公网 IP》，很多读者到博客留言，抱怨说讲得太简单。缺少傻瓜化的、带截图的配置教程。俺恭敬不如从命，今天再发一篇《用虚拟机隐匿公网 IP（配置图解）》，竭尽所能，写得尽量傻瓜化。 　　为了以示区分，前一篇的标题修改为《用虚拟机隐匿公网 IP（原理介绍）》。 　　顺便说一下： 　　前面那篇发到 G+ 上，貌似被顶到 G+ 热门榜，转发数很多。看来有不少网友关注“隐匿身份”这个话题 :) 所以俺今后会多花点时间，普及这方面的相关常识。  
  
　　首先，如果你对虚拟机软件不太熟悉，【**一定要先看完**】俺之前写的《[扫盲操作系统虚拟机](https://program-think.blogspot.com/2012/10/system-vm-0.html)》。  
　　其次，再把本系列的前一篇博文（链接在“[这里](https://program-think.blogspot.com/2013/01/howto-cover-your-tracks-6.html)”）**认真看完**。那篇博文是介绍“虚拟机隐匿公网 IP”的原理，配有精美示意图 :)  
　　既然要用虚拟机隐匿公网 IP，当然要先把虚拟机软件准备好。假如你不晓得该选哪种虚拟机软件，请看俺之前的一篇博文（请翻墙看“[这里](https://program-think.blogspot.com/2012/11/system-vm-3.html)”），专门介绍虚拟机软件的选择。 　　本文主要拿 VMware Workstation（以下简称 VMware）和 VirtualBox 来介绍。 　　先声明一下，本文提到的“代理”一词是广义的，包括：普通代理、VPN、多重代理。 　　由于本教程是拿虚拟机跟代理软件进行组合搭配，所以你还得懂得使用代理软件。这点应该不难——只要你有翻墙的经历，你就已经在同"代理软件"打交道了。如果你从来没玩过翻墙，请先学习俺博客上的诸多翻墙教程（包括：TOR、I2P、赛风、世界通、自由门、无界 ......）。

　　关于代理的类型，俺强烈建议用**多重代理**（教程在“[这里](https://program-think.blogspot.com/2012/03/howto-cover-your-tracks-5.html)”，需翻墙）。为啥捏？如果你对隐匿性的要求不高，根本都不需要看本教程。你来看本教程，就说明你对隐匿性有较高的要求。既然如此，当然要用多重代理啦——这可以大大增加逆向追踪的难度。

  
　　**注意事项：  
　　要确保你用的代理软件，是监听在 `0.0.0.0` 地址，而不是监听在 `127.0.0.1` 地址**。如果代理软件只监听在 `127.0.0.1` 地址，那么其它虚拟机的网络软件是【无法】连接到这个监听端口滴！ 　　如何查看代理软件在哪个地址上进行监听捏？ 　　用如下命令，就可以看到当前系统中开启的【所有】监听端口以及该监听绑定的地址。 　　注：前一个命令用于 Windows；后一个命令用于 POSIX 系统（Linux ＆ UNIX）

netstat -an | find "LISTEN"
netstat -an | grep "LISTEN"

  
　　那么，万一你的翻墙工具的监听端口【没】绑定到 `0.0.0.0` 该咋办捏？别担心，俺后来又专门写了一篇教程《[多台电脑如何共享翻墙通道](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)》，教你如何解决监听端口绑定地址的问题。

　　如果你光使用 VPN 作为“代理”。由于 VPN 本身是不开启监听端口的。那么你就必须想办法共享 VPN 的翻墙通道。至于如何共享，请看《[多台电脑如何共享翻墙通道](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)》。

　　本教程适用于目前的各种主流操作系统，包括但不限于 Windows、Linux、Mac OS X ...... 　　考虑到目前 Windows 系统的用户占绝大多数，本教程拿 Windows 系统来说事儿。希望 Linux 系统和 Mac OS X 系统的用户别怨俺偏心。

　　**注意事项：  
　　要特别小心真实系统和虚拟系统的防火墙设置**。很多人就是因为防火墙没配好，导致代理无法连通。

　　如果你碰到上述困难，可以参考如下博文——用 netcat 辅助你进行诊断。

《[扫盲 netcat（网猫）的 N 种用法——从“网络诊断”到“系统入侵”](https://program-think.blogspot.com/2019/09/Netcat-Tricks.html)》

  
　　先跟大伙儿说一下：今天这个教程跟物理网卡【**没有**】半毛钱关系。跟你电脑上装了多少块物理网卡，也【**没有**】半毛钱关系。在本文后续的介绍中，【**不会**】再涉及到物理网卡。待会儿在配置代理的时候，也【**不会**】再涉及物理网卡上的 IP 地址。切记！  
　　另外，今天这个教程，跟你用的上网方式也【**没有**】关系。不论你是在公司上网还是在家用宽带，本教程都适用。  
　　【**这部分是重点，注意看喽！**】 　　一旦你安装完虚拟机软件，那么你的操作系统中就会多出新的虚拟网卡和虚拟子网。下面俺根据 VMware 和 VirtualBox 分别说明。 　　每次安装 VMware，新增加的虚拟子网，网络地址都可能会不同，所以俺多费点口水。 　　首先到 Windows 控制面板的网络连接看一下，如果看到下图，就这说明 VMware 已经帮你加入了2个虚拟网卡，这俩网卡分别位于 NAT 虚拟子网和 Host-Only 虚拟子网。

![不见图 请翻墙](https://lh3.googleusercontent.com/I0BZO21bRYuinYFgRO87fB-ZY4Bac3L7orMMxn7m9m7y7ZfOvn4AazIltGFDj41JWAbrFZp5ah3TdbrwI_IPTEhWVEyg81iQp3BdKLhAGIv9KcZdy5TuuzlM6KM)

  
　　然后，你到 VMware 主菜单上点”Edit“菜单，然后再点”Virtual Network Editor“菜单，会出现虚拟子网的对话框，通过该对话框可以看到 VMware 创建的所有虚拟子网。你会看到好多个虚拟子网，咱只要关心其中两个——分别是 Type 为【Host-Only】和 Type 为【NAT】的。然后，把这两个子网的”Subnet Address“分别记下来（**千万别把这俩记混了**），待会儿要用到。截图如下  

![不见图 请翻墙](https://lh6.googleusercontent.com/z-D7eOmA1xYjGQcdPZ9cSV7RSl8nGWbkls8-_fUc1fHghH7YqcI1jvZpzO77HnXw5btC9r6wByLjf_dvL96Kzlibe6XJHs6-JhcFQ39WhZBdhcrGCgk_07beKK0)

  
（请注意，上述截图中列出的都是虚拟子网的【**网络地址**】，表示的是整个子网，所以最后一位是 `0` ） 　　每次安装 VirtualBox 的时候，它创建的虚拟子网，网络地址总是一样的，所以 VirtualBox 的操作比较简单。

　　对于 NAT 模式，默认的虚拟子网总是 `10.0.2.0`；对于 Host-Only 模式，默认的虚拟子网总是 `192.168.56.0`（请注意，这两个是虚拟子网的【**网络地址**】，表示的是整个子网，所以最后一位是 `0` ）

  
　　**牢记这俩子网的网络地址（千万别把这俩记混了），待会儿要用到。**  
  
　　如何在虚拟机软件中安装 Guest OS，《[扫盲操作系统虚拟机](https://program-think.blogspot.com/2012/10/system-vm-0.html)》系列教程已经有详细的操作图解，此处不再啰嗦。  
　　（**这部分是重点，看仔细喽！**）  
　　首先，你要在虚拟机软件中设置该“虚拟系统A”的网卡模式，要设置为【**Host-Only**】。 　　其次，要进入“虚拟系统A”，到“控制面板”的“网络连接”里，找到那块网卡，右键菜单点“属性”，再点“TCP/IP”的属性，会出现如下截图

![不见图 请翻墙](https://lh3.googleusercontent.com/bS3_NN5upSDaEuUgOTyDC38X1Q8N5Njyorp0CSatovD1CTq5y6lPkn0fOBQXUZqH6dwPAUYeeHj9pVqUVkmf6sIig18AfCRmVldSeMKoW2nVWwNdi7s0WO3EMcA)

  
**IP 地址**  
（**这步一定要小心，别填错了**） IP 地址一共四段：

头三段，分别填写【**Host-Only**】子网的网络地址的头三个数字。请回顾刚才的章节——★真实系统（Host OS）的虚拟网卡。

  
第四段，你可以填 `2` 到 `254` 之间的任何一个数。  
**子网掩码**  
填写 `255.255.255.0`  
**默认网关** 不用填

**DNS**

不用填 　　这块【Host-Only】网卡配好之后，为了验证你是否配置成功，可以执行如下步骤验证：

进入“虚拟系统”，用 `ping` 命令测试一下真实系统的那块【Host-Only】网卡的 IP 地址。如果能 ping 得到就说明你配对了。

　　在单虚拟机方案中，代理直接安装在 Host OS 里面。关于代理软件的安装，就不用再啰嗦了吧？  
　　（**这部分也是重点，看仔细喽！**） 　　为网络软件配置代理的时候，通常要填写代理的 IP 地址和端口号。端口号通常不会搞错。因为每一款代理软件开启的端口号是固定的。但是 IP 地址常常会填错。很多人就是栽在这一步。

　　填写代理的 IP 地址，千万【**不能**】填 `127.0.0.1`，因为这个地址表示【本机】，也就是 Guest OS 自己。

  
　　**正确的写法**是：填写真实系统的那个【**Host-Only**】网卡的 IP。 这个 IP 地址一共四段：

头三段，分别填写【**Host-Only**】子网的网络地址的头三个数字。请回顾刚才的章节——★真实系统（Host OS）的虚拟网卡；

  
第四段，填 `1` 　　俺以 IE 浏览器为例，截图如下

![不见图 请翻墙](https://lh3.googleusercontent.com/ywn99XmncvnxcYN2hOcLND3IBzGMlA1sxqm9ovOmiv7tg3yqtsc3c5S1VwkddNOuCivOxCo0Agc04p4UBB6TZybIoU2tXdSOi1S_Yn7XrmCNTAfdcBjlACOHMDI)

  
  
　　如何在虚拟机软件中安装 Guest OS，《[扫盲操作系统虚拟机](https://program-think.blogspot.com/2012/10/system-vm-0.html)》系列教程已经有详细的操作图解，此处不再啰嗦。  
　　要使用双虚拟机方案，你需要准备【**两套**】虚拟系统（Guest OS）。  
　　首先，你要在虚拟机软件中设置该“虚拟系统A”的网卡模式，要设置为【**Host-Only**】。 　　其次，要进入“虚拟系统A”，到“控制面板”的“网络连接”里，找到那块网卡，点属性，会出现如下截图

![不见图 请翻墙](https://lh3.googleusercontent.com/bS3_NN5upSDaEuUgOTyDC38X1Q8N5Njyorp0CSatovD1CTq5y6lPkn0fOBQXUZqH6dwPAUYeeHj9pVqUVkmf6sIig18AfCRmVldSeMKoW2nVWwNdi7s0WO3EMcA)

  
**IP 地址**  
（**这步一定要小心，别填错了**） IP 地址一共四段：

头三段，分别填写【**Host-Only**】子网的网络地址的头三个数字。请回顾刚才的章节——★真实系统（Host OS）的虚拟网卡。

  
第四段，你可以填 `2` 到 `254` 之间的任何一个数。  
**子网掩码**  
填写 `255.255.255.0`  
**默认网关** 不用填

**DNS**

不用填 　　这块【Host-Only】网卡配好之后，为了验证你是否配置成功，可以执行如下步骤验证：

进入“虚拟系统A”，用 `ping` 命令测试一下真实系统的那块【Host-Only】网卡的 IP 地址。如果能 ping 得到就说明你配对了。

  
　　“虚拟系统B”要配置两块网卡，【**这部分非常非常容易搞错，一定要看仔细喽！**】

**第1步**

  
刚装好的“虚拟系统B”，默认已经有一块网卡了。你先把这块网卡的网卡模式，设置为【**NAT**】。

**第2步**

进入“虚拟系统B”，到“控制面板”的“网络连接”里，找到那块网卡，右键菜单点“属性”，再点“TCP/IP”的属性，会出现如下截图

![不见图 请翻墙](https://lh3.googleusercontent.com/hc60D2QGAJWQkllix3-vIwuIb7pbhsSS1rMLGhTtTAJbyatY-Kh8DzFx_dE2-MxIuraN-6b-SxtEO_JMB69wcrNR7GmV--cibnHFeyZ9v2nFBT1sMvDb3Or85JI)

  
**IP 地址**  
【**这步一定要小心，别填错了**】 IP 地址一共四段：

头三段，分别填写【**NAT**】子网的网络地址的头三个数字。请回顾刚才的章节——★真实系统（Host OS）的虚拟网卡。

  
第四段，你可以填 `3` 到 `254` 之间的任何一个数。  
**默认网关**  
（**这步也要小心，别填错了**）  
默认网关的地址也是4段，头三段就照抄刚才 IP 地址的头3个数字。第4个数字填写 `2`（不论是 VMware 还是 VirtualBox 都填 `2`）  
**DNS**  
此处填写你常用的 DNS 服务器，俺个人建议填 Google 的那俩（`8.8.8.8` 和 `8.8.4.4`）  
**子网掩码**  
填写 `255.255.255.0` 　　这块 NAT 网卡配好之后，为了验证你是否配置成功。可以在“虚拟系统B”里面开一个浏览器（不设代理），访问一下互联网。如果能访问，说明这块 NAT 网卡 OK 了。

**第3步**

  
打开虚拟系统的设置对话框，再添加一块网卡了。（如何加第二块网卡，请看《[扫盲操作系统虚拟机](https://program-think.blogspot.com/2012/12/system-vm-5.html)》教程）然后把这块网卡的网卡模式，设置为【**Host-Only**】。

**第4步**

  
　　进入“虚拟系统B”，到“控制面板”的“网络连接”，找到新添加的【**第二块**】网卡，右键菜单点“属性”，再点“TCP/IP”的属性，会出现如下截图  

![不见图 请翻墙](https://lh3.googleusercontent.com/bS3_NN5upSDaEuUgOTyDC38X1Q8N5Njyorp0CSatovD1CTq5y6lPkn0fOBQXUZqH6dwPAUYeeHj9pVqUVkmf6sIig18AfCRmVldSeMKoW2nVWwNdi7s0WO3EMcA)

  
**IP 地址**  
【**这步一定要小心，别填错了**】 IP 地址一共四段：

头三段，分别填写【**Host-Only**】子网的网络地址的头三个数字。请回顾刚才的章节——★真实系统（Host OS）的虚拟网卡。

  
第四段，你可以填 `2` 到 `254` 之间的任何一个数。  
再提醒一下：虚拟系统A和虚拟系统B各自有一块【Host-Only】网卡，这两块网卡的 IP 地址头三位是一样的，**第四位不能相同——否则 IP 地址会冲突**。  
**子网掩码**  
填写 `255.255.255.0`  
**默认网关** 不用填

**DNS**

不用填  
　　在双虚拟机方案中，**代理是安装在“虚拟系统B”（网关）里面的**，别搞混喽！关于代理软件的安装，就不用再啰嗦了吧？  
　　在双虚拟机方案中，那些有危险的**上网软件是安装在“虚拟系统A”里面的**，别搞错喽！ 　　下面详细说说上网软件的代理配置。

　　为网络软件配置代理的时候，通常要填写代理的 IP 地址和端口号。端口号通常不会搞错。因为每一款代理软件开启的端口号是固定的。但是 IP 地址常常会填错。所以**请大伙儿把下面看仔细喽！**

  
　　填写代理的 IP 地址，**千万【不能】**填 `127.0.0.1`，因为这个地址表示本机，也就是“虚拟系统A”自己。  
　　**正确的写法**是：填写另一个虚拟系统（虚拟系统B）的那个【**Host-Only**】网卡的 IP。 　　因为“虚拟系统B”（网关）有两块网卡，很多人填错了，栽倒在这一步。俺以 IE 浏览器为例，截图如下

![不见图 请翻墙](https://lh3.googleusercontent.com/E4_zkEEFoQwmHuHdp9JOps50_4GNu2yfL9mxUm8uQUE3nsbzVd6p3xNSCdGlQrgLhP1VMjVeg8hsPLQ8x8wEt-oIyJDBpA5KVZM3-6tVPuFsn6dyCTENbWAq0Y8)

  
  
　　在双虚拟机方案中，虚拟机在启动时有可能会出现错误提示：“网络上有重名”。如果你碰到这个错误，只需把虚拟机网卡的 NetBIOS 功能禁用，即可解决。如何禁用 NetBIOS，请看“[微软官网这里](https://technet.microsoft.com/zh-cn/library/ms143696%28v=sql.90%29.aspx)”。 　　（经热心读者 meek 提醒，俺补充了这一章节）

　　在《扫盲操作系统虚拟机》系列的[第5篇](https://program-think.blogspot.com/2012/12/system-vm-5.html)，俺介绍了 Guest OS 的各种网卡模式，其中也包括“Internal 模式”。这种模式类似于“Host Only 模式”，差别在于——Host OS 上的进程无法看到“Internal 模式”的虚拟网卡。

　　因此，“双虚拟机方案”也可以采用“NAT + Internal”的玩法。 　　好处是——隔离性更好； 　　缺点是——Internal 这种网卡模式 Virtual Box 支持而 VMware 【不】支持 （对 VMware 用户，可以通过添加“自定义网卡”来达到类似效果）。 　　如果你想采用“NAT + Internal”的方式配置虚拟网卡，那么整个配置过程跟前一章节介绍的“NAT + HostOnly”很相似，差别仅仅在于把两个虚拟网卡的“HostOnly 模式”替换为“Internal 模式”。所以俺就不重复罗嗦了。 　　无论是“双虚拟机方案”还是“单虚拟机方案”，配置完毕，联通代理之后，为了保险起见，你需要再验证一下虚拟机的隔离性。 1. 先把代理关闭，到虚拟机A 中运行危险软件，看它是否能联网成功。（如果联网成功，说明你的配置有误）

2\. 进入虚拟机A，开启一个命令行窗口，用 `ping` 命令测试一下你常用的 DNS 服务器的 IP（如果能 ping 到，说明你的配置【有误】）

  
　　由于涉及两套方案，而且涉及两种虚拟机软件，本文有点长，步骤有点多。如果你根据本教程配置完毕，还是不行，请到[本文留言](https://program-think.blogspot.com/2013/01/howto-cover-your-tracks-7.html)，俺会尽量解答。

**[回到本系列的目录](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html#index)**

