---
layout: default
title: '如何隐藏你的踪迹&#65292;避免跨省追捕[6]&#65306;用虚拟机隐匿公网 IP&#65288;原理介绍&#65289;'
date: None
author:
    display_name: 
---

　　在多位读者的强烈要求下，本文终于隆重推出了 :) 今天俺来介绍一下：如何利用操作系统虚拟机（以下简称“虚拟机”）来隐匿自己的公网IP。  
  
　　为了给本文打基础，俺在最近两个月特地写了一个《扫盲操作系统虚拟机》的系列博文（链接在“[这里](https://program-think.blogspot.com/2012/10/system-vm-0.html)”）。如果你不是 IT 技术人员，或者你对虚拟机了解不多，**强烈建议**你先把这个虚拟机扫盲系列看完，然后再来看本文。  
　　在本系列第一篇《[网络方面的防范](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-1.html)》，俺专门解释了：“什么是公网 IP”，也特别强调了“公网 IP 暴露”的危险性。如果你比较健忘的话，先去把那篇再复习一下。 　　如果你上网不使用代理，那么你访问的网站就会看到你的公网 IP。示意图如下：

![不见图 请翻墙](https://lh4.googleusercontent.com/Ky0rYvcL-GXMW1VIFzPg_GGKs0IWNtfiuzkYUvLEzdFNCodugIfE-BiN9FW7AYYUrtKbugWlVrQs6aI7Y3eJVNP61MRsaBjthXAxhPDQXajAMWlWa6LguRZ-kBY)

　　此处说的代理是广义的，包括普通代理、VPN、多重代理、等。如果用了代理，你访问的网站看到的公网 IP 实际上是代理服务器的 IP。 示意图如下

![不见图 请翻墙](https://lh3.googleusercontent.com/lkZjGLE-sd3KUXrB-SeMUPX2jSl3QlY7byT6i8SwLVsQBq_yQp8YgaNNRDrG3rt48oaxqjLAtays9MByzYNtzp-iSzJ-UVGakaWovLe1AHQzo8H-ifPHjPVgrd8)

　　但是不要高兴得太早，仅仅依靠普通的代理，是远远不够滴！请看下面的例子。  
　　比如你在浏览器中设置了代理，那么浏览器确实会通过代理来加载网站的页面。**但是**，浏览器如果安装了某些插件（最典型的是 Flash），这些插件是可以做到绕过代理，直接去访问目标网站的。 　　举个例子： 　　比如你想在某个国内的网盘上传政治敏感文件。因为这个网盘是国产的，你担心网盘服务器会记录你的公网 IP。所以捏，你设置了浏览器的 HTTP 代理，通过翻墙代理来访问这个网盘的页面。

　　如今的很多网盘是利用 Flash 插件进行文件上传的。而且 Flash 插件在上传文件的时候，往往是不经过浏览器的 HTTP 代理，**直接连接**网盘服务器。如此一来，你的公网 IP 还是暴露了 :(

示意图如下

![不见图 请翻墙](https://lh3.googleusercontent.com/LPdbpOzwgT_7h9MHALQ-3e9-jfwlCodpNduHegMvOks1YMIbW1BV9P5k6hcT2Qy-p-oylRNxLi5ysTco4mSuVTmzVK9xTo69Mhm548bjwYH7GaS1j2BJugqjZ-4)

  
　　除了浏览器插件（以 Flash 为主）会暴露你的公网 IP，还有其它很多国产的网络软件也会暴露你的公网 IP。比较典型的有 QQ、腾讯浏览器、360浏览器、迅雷、等等。关于危险的国产软件，本系列第2篇[《个人软件的防范》](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-2.html)已经聊过，这里就不再浪费口水了。  
　　上述这些网络软件虽然都提供了代理的功能。**但是**，即使你设置了代理，这些软件依然有可能在后台，悄悄地访问自己公司的服务器，传输某些不可告人的信息。而且这些软件访问自家的服务器，往往是绕过代理设置，**直接连接**——这就会导致你的公网IP暴露。 示意图如下

![不见图 请翻墙](https://lh3.googleusercontent.com/7MASBpz1J59zvlSRizUzzm05eHvd7WyTtRonnqLkq_LTJhwNBYnq4c2PNnSQsVOSOiQPSEv05AVa17LRkRqFk-4JKFtpR22iorSc5esjENtmzP7TiM8p8XBhEKo)

　　那么，如何避免上述这几种危险的情况捏？首先来看一下“单虚拟机”的方案。

　　咱们可以把那些有危险的软件安装在虚拟系统（虚拟机A）内，然后把该虚拟唯一的虚拟网卡设置为【**Host-Only**】模式（关于网卡模式的设置，请看“[这里](https://program-think.blogspot.com/2012/12/system-vm-5.html)”）。由于唯一的虚拟网卡是【**Host-Only**】模式，所以 虚拟机（Guest OS）内的任何软件都**不可能【直接访问】外部网络**。

　　那么，如何让这些危险的软件联网呢？你可以在 Host OS 里面安装一个代理软件。虽然这个 Guest OS 无法访问外网，但还是可以访问 Host OS 的，所以也就可以连接到 Host OS 里面的代理软件。然后你设置这些危险软件的 HTTP 代理或 SOCKS 代理，让它们通过代理连接到互联网。 示意图如下

![不见图 请翻墙](https://lh4.googleusercontent.com/mMOFO42Roq6rr1JcQ0Wo4UB96y-PlQYkbNQm3sqSYXfS2GB9Z_L7deTpRhwR5nknnuD3_r06TR0xNviXYcUCPaf2TJ12j28VOUyt_CKVYzr-vP-_asld7Ia113o)

　　说完“单虚拟机方案”，再来说说“双虚拟机方案”。 　　对很多网友而言，单虚拟机已经足够了。那么为啥俺还要介绍双虚拟机捏？主要有如下几方面考虑 1、某些翻墙代理软件不是开源的，有些网友对这类软件不放心 2、某些网友的 Host OS 不是 Windows，但是很多翻墙代理是 Windows 软件

　　所以，咱们可以在“单虚拟机”的基础上再扩展一下，把代理软件也放到虚拟机中（下图的虚拟机B）。虚拟机B 的网卡很有讲究滴——**必须是双网卡**。一个网卡设置为 Host-Only 模式，以便跟虚拟机 A对接；另一个网卡设置为 NAT 模式，以便访问外网。

示意图如下

![不见图 请翻墙](https://lh5.googleusercontent.com/EG-eA0wURF5rWkQGkl0Yq7lQjwaVkDoB1t_dSwTQf5GlDKdLcDrfBqzU1D2IrQ1dTAUcPqGLeL1369RDNijQ2jcEL6H40_dzehktsSfquNe6DmvO44U4PZF-kC0)

  
　　在本系列的前一篇，俺介绍了“[用多重代理保持匿名](https://program-think.blogspot.com/2012/03/howto-cover-your-tracks-5.html)”。今天介绍的这2个招数都可以跟多重代理搭配 　　打个比方，假设你用“Tor + 自由门”来构造多重代理。对于单虚拟机的方案，你把“Tor、自由门”都安装到 Host OS 即可；对于双虚拟机的方案，你把“Tor、自由门”都安装到 虚拟机B 即可。  
　　关于“虚拟机结合代理来隐匿公网IP”，基本原理就介绍到这里。[本系列的下一篇](https://program-think.blogspot.com/2013/01/howto-cover-your-tracks-7.html)，俺写一个傻瓜化的配置教程，附上详细的截图，告诉你如何操作。

**[回到本系列的目录](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html#index)**

