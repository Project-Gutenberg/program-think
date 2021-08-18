---
layout: default
title: '如何保护隐私[3]&#65306;关于浏览器的基本防范&#65288;中&#65289;'
date: None
author:
    display_name: 
---

　　今天这篇，主要介绍浏览器 Cookie 方面的防范。  
　　本文所说的“cookie”，指的是浏览器相关的 cookie（有时候也叫“HTTP cookie”）。 　　浏览器 cookie 的主要功能是：帮助网站保存一些小片段的信息。比如，你曾经在自己的浏览器上登录过某个论坛，下次你再打开论坛的登录页面，你会发现用户名已经帮你填好了，你只需要输入口令即可。那么，这个登录页面是如何知道你上次登录用的账户名捏？奥妙就在于：该网站在你的浏览器端保存了一个 cookie，里面包含了你上次登录使用的帐号名称。 　　本章节面向【懂技术】的读者。如果你不太懂技术，可以略过本节，直接进入下一章节，以免浪费时间。  
　　**步骤1** 　　当你在浏览器中点某个书签、或者在浏览器地址栏输入某个网址，浏览器会向对应的网站发起一个 HTTP 请求（术语是 HTTP Request）。

　　**步骤2**

　　然后，网站的服务器收到这个 HTTP 请求之后，会把相应的内容（比如网页、图片、等）发回给浏览器（这称为 HTTP 响应，术语是 HTTP Reponse）。 　　如果网站想设置 cookie，就在发回的 HTTP Response 中，包含一个设置 cookie 的指令。举例如下：

> Set-Cookie: user=xxxx; Path=/; Domain=www.example.com

　　在上述例子中，设置了一个 cookie。这个 cookie 的【名】是 `user`；cookie 的【值】是 `xxxx`；cookie 绑定的【域名】是 `www.example.com`  
　　**步骤3** 　　浏览器在收到这个指令后，就会在你的电脑中存储该 cookie 的信息。  
　　假设过了几天之后，你再次访问上述的 `www.example.com` 网站（在上次的访问中，已经被设置过 cookie 了）。这时候，浏览器发现该网址已经有对应的 cookie，就会把 cookie 的信息放在 HTTP Request 中，然后发送到网站服务器。具体的指令如下：  

> Cookie: user=xxxx

　　网站服务器拿到这个 HTTP Request 之后，就可以通过上述信息，知道 cookie 的【名】与【值】。  
　　cookie 在洋文中的意思就是：小甜饼、曲奇饼。这个单词其实已经暗示了 cookie 技术所能存储的信息量是比较小滴。 　　从刚才的技术实现机制可以看出，cookie 只能用来存储纯文本信息，而且存储的内容不能太长——因为 Cookie 的读写指令受限于 HTTP Header 的长度。 　　但是，cookie 的信息量虽小，能耐却很大哦。请看下面的例子。

　　**举例**

　　比如某个网站上有很多网页，每个网页上有很多广告。该网站想要收集：每一个访客点击了哪些广告。

　　由于这些信息量比较大，直接存储在 cookie 里可能放不下。所以，网站通常是在 cookie 中保存一个【**唯一的用户**】标识。然后把用户的点击信息（包括在哪个时间点击哪个广告）都存储在服务器上。

　　下次你再访问该网站，网站先拿到 cookie 中的用户标识，因为这个标识具有唯一性，那么就可以根据该标识，从网站服务器上查出该用户的详细信息。 　　从上述的实现机制可以看出，cookie 是跟 HTTP Request 对应的网址（域名和路径）相关的。 　　所以，不同域名的网站设置的 cookie 是互相独立的（隔离的）。这一点由浏览器来保证，以确保安全性。

　　补充一下：cookie 绑定的域名可以是【**小数点开头**】的。举例如下：

  

> Set-Cookie: user=xxxx; Path=/; Domain=.example.com

　　这个指令设置的 cookie，可以被 `example.com` 的【**所有**】下级域名读取（比如：`www.example.com` 或 `ftp.example.com`）。  
　　首先来说说“第一方 Cookie”与“第三方 Cookie”的区别，因为这跟隐私的关系比较密切。 　　要说清楚这两者的差异，俺来举个例子。

　　**举例**

　　打个比方，你上新浪去看新闻，并且新浪的网页上嵌入了阿里巴巴的广告（假设新浪的页面和嵌入的广告都会设置 cookie） 　　那么，当你的浏览器加载完整个页面之后，浏览器中就会同时存在新浪网站的 cookie 和 阿里巴巴网站的 cookie 　　这时候，新浪网站的 cookie 称为“第一方 Cookie”（因为你访问的就是新浪嘛） 　　相对的，阿里巴巴的 cookie 称为“第三方 Cookie”（因为你访问的是新浪，阿里巴巴只是不相干的第三方） 　　根据存储方式的不同，分为两类：基于内存的 Cookie 和 基于文件的Cookie。基于内存的 cookie，当浏览器关闭之后，就消失了；而基于文件的 cookie，即使浏览器关闭，依然存在于硬盘上。和隐私问题相关的 cookie，主要是第二类（基于文件的Cookie）。 　　今年的315晚会，央视猛烈抨击了 cookie 的隐私问题，搞得好像 cookie 是洪水猛兽一般。CCAV 对 cookie 的妖魔化宣传，典型是用来吓唬不懂技术的外行。 　　其实捏，cookie 是有利有弊的。cookie 之所以应用这么广泛，因为它本身确实是很有用的。请看下面的几个例子。 　　目前很多基于 Web 的邮箱，都有自动登录功能。也就是说，你第一次打开邮箱页面的时候，需要输入用户名和口令；过几天之后再来打开邮箱网页，就不需要再次输入用户名和口令了（比如 Gmail 和 Hotmail 就是这样的）。 　　为啥邮箱可以做到自动登录，就是因为邮箱的网站在你的浏览器中保存了 cookie，通过 cookie 中记录的信息来表明你是已登录用户。 　　比如某个论坛允许匿名用户设置页面的字体样式和字体大小。 　　那么，该论坛就可以把匿名用户设置的字体信息保存在 cookie 中，下次你用同一个浏览器访问该论坛，自动就帮你把字体设置好了。 　　一般来说，有正经用途的 cookie，大都是“第一方 Cookie”；至于“第三方 Cookie”，大部分是用来收集广告信息和用户行为的。 　　cookie 就像一把双刃剑，有很多用途，但也有弊端。一个主要的弊端就是隐私问题。 　　假如你同时使用 Google 的 Gmail 和 Google 的搜索（很多 Google 用户都这么干）。当你登录过 Gmail 之后，cookie 中会保存你的用户信息（标识你是谁）；即使你在 Gmail 中点了注销（logout），cookie 中还是会有你的用户信息。 　　之后，你再用 Google 的搜索功能，那么 Google 就可以通过 cookie 中的信息，知道这些搜索请求是哪个 Gmail 用户发起的。 　　可能有些同学会问：Gmail 和 Google 搜索，用的是不同的域名，如何共享 cookie 捏？ 　　俺前面有介绍过，某些 cookie 绑定的域名是以小数点开头的，也就是说，这类 cookie 可以被所有下级域名读取。

　　因为 Gmail 的域名是 `mail.google.com`，而 Google 搜索的域名是 `www.google.com`。所以这两者都可以读取绑定在 `.google.com` 的 cookie！

　　注：俺拿 Google 来举例是因为俺博客的读者，大部分都是 Google 用户。其实不光 Google 存在此问题，百度、腾讯、阿里巴巴、奇虎360、等等，都存在类似问题（这几家都有搜索功能，也都有自己的一套用户帐号体系）。 　　很多网站会利用 cookie 来追踪你访问该网站的行为（包括你多久来一次，每次来经常看哪些页面，每个页面的停留时间） 　　这样一来，网站方面就可以根据这些数据，分析你的个人的种种偏好（这就涉及到个人隐私）。 　　请注意：利用 cookie 收集个人隐私的把戏有很多，俺限于篇幅，仅列出上述两例。  
　　在[本系列的前一篇](https://program-think.blogspot.com/2013/06/privacy-protection-2.html)，俺已经分析了：Firefox 是主流浏览器中，隐私方面比较靠谱的（完全开源、没有商业背景）。相对于 Firefox，Chrome 只是【部分开源】，而且 Google 的商业模式太依赖广告，不会为隐私保护而得罪广告主；至于 IE，根本不开源，自身的安全性也不够。 　　所以，本小节下面的内容，主要拿 Firefox 来说事儿。如果你是 Chrome 的粉丝，不想换 Firefox，也没关系。这两款浏览器的某些功能大同小异，你可以参考本章节的介绍，然后在 Chrome 上依样画葫芦。 　　前面说了，大部分“第三方 Cookie”都【不是】干正经事儿的。所以，最简单也是最宽松的设置，就是光禁用“第三方 cookie”。 　　配置方法和截图如下： 　　在 Firefox 主菜单点“工具”，再点“选项”。在弹出的选项对话框中，选“隐私”标签页。 　　在界面的第一个下拉框中选择“使用自定义历史记录设置”

　　选完下拉框，你会看到一个复选框叫“接受第三方 Cookie”，请【**去掉**】这个复选框的打勾。

  

![不见图 请翻墙](https://lh6.googleusercontent.com/GJzSlsOnwLZJfy1M3dkWU-0-Hvw7sW7XDwf_gQZ9SybX-77bHOc3xM0ziyInR528e7P8bDXexSds_euw-AWZUUiGoPS-xNF2FNSor9U0ZY5yejRpLN8IYbl4u245)

  
　　这种方式比前一种更严格。你只保留某些你信任的网站的 cookie，其它网站统统禁用。 　　配置方法和截图如下： 　　在 Firefox 主菜单点“工具”，再点“选项”。在弹出的选项对话框中，选“隐私”标签页。 　　在界面的第一个下拉框中选择“使用自定义历史记录设置”

　　选完下拉框，你会看到一个复选框叫“接受来自网站的 Cookie”，请【**去掉**】这个复选框的打勾。

　　然后到该复选框右侧，点“例外”按钮，把你信任的网站域名输入进去。

![不见图 请翻墙](https://lh3.googleusercontent.com/MZ1NihopvgmG_FrHnavEGYjX1BKrm3E-h7GEa78mYLfTFHVwx7VY8jM_GFtw2zN3gTeCQH1Cq1Cq3K9vqY7-OExOgd0_eF_0_lzfXJlBWvdsKfwofgZz7quEa7s)

  
  
　　关于“隐私浏览模式”，在[本系列的前一篇](https://program-think.blogspot.com/2013/06/privacy-protection-2.html)已经介绍过了，此处不再啰嗦。 　　相比前两个招数，这招最严格。在隐私浏览模式下，浏览器关闭之后，期间所有的 cookie 都消失。 　　但是，这样设置也可能带来一些不方便之处（安全性和方便性通常是截然对立）。你可能要先尝试一段时间，看看自己能否忍受这种模式。 　　配置方法和截图如下： 　　在 Firefox 主菜单点“工具”，再点“选项”。在弹出的选项对话框中，选“隐私”标签页。 　　在界面的第一个下拉框中选择“使用自定义历史记录设置”

　　选完下拉框，你会看到一个复选框叫“始终使用隐私浏览模式”，请【**勾上**】这个复选框。

打勾之后，Firefox 会提示你重启浏览器。

![不见图 请翻墙](https://lh4.googleusercontent.com/KJNGaP3kThZTwB2_nqDR38Yz1F0phVDeL5pEg6oQNuirk3hWqC_0wLYoZu4zhtbD3BKpN31WxmszClX6M9M7tvgK7vD09SwUKTOS69EHTyt8kypdaOmpekjatWQ)

  
　　刚才介绍的几招，都是针对单个浏览器 。大部分情况下是够用了。但是某些特殊情况，还是会搞不定。

　　比如：你经常用 Gmail，而且依赖于 Gmail 的自动登录。这时候，你就【不应该】禁用 `.google.com` 域名下的 cookie（禁用了就无法自动登录 Gmail）。

　　但是，你在用 Google 搜索的时候，又不希望让 Google 知道你是谁。咋办捏？请听下回分解——如何隔离浏览器。

[回到本系列的目录](https://program-think.blogspot.com/2013/06/privacy-protection-0.html#index)

