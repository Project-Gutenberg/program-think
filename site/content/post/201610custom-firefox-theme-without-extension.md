---
layout: default
title: '无需任何插件或扩展&#65292;定制 Firefox 外观'
date: None
author:
    display_name: 
---

　　**关于“评论区改版”的补充说明**  
　　十一假期[重写了博客评论区的代码，并增加了评论的“热度排名”](https://program-think.blogspot.com/2016/10/custom-blogger-comment.html)。这之后的两周，修复了好几个热心读者反馈的 bug，也采纳了热心读者提出的好些个建议（有些建议已经做出来了，有些还在计划中）。最近一周，前一篇博文的评论数从500+增长到700+。俺感觉评论界面的载入速度偏慢，所以上周俺一直都在优化代码，以提高界面载入速度。 　　可能某些读者发觉俺连续两周没有发博文，担心俺出事了。其实最近2周，俺一直在评论区出没。经常逛评论区的同学，应该晓得俺没事儿。 　　（判断俺是否出事了，【不要】光看“发博”间隔，要看俺的网络活动——有时候虽然没有发博文，但是俺可以通过回复评论体现出网络活动，以表明俺还活着）  
　　刚才说了，最近半个月都在倒腾页面代码（HTML/JS/CSS），业余时间几乎都花在这上面。搞得晚上做梦都梦见博客界面出 bug。在这种状态下，今天继续来讨论技术话题——关于 Firefox 的界面定制。

　　网上已经有很多 Firefox 的插件或扩展，可以定制 Firefox 的界面。不过今天俺要聊的是——**【无需任何插件/扩展】**，就可以定制 Firefox 的各种界面。

  
  
　　信息安全领域有一个原则——系统中运行的代码越多，出现漏洞的概率就越大。 　　如果不需要额外的插件和扩展，就可以定制 Firefox 的界面，那自然就可以做到“运行的代码最少”。 　　另外，即使是 Firefox 官网提供的插件或扩展，你也不敢保证全都是【可信任】的。万一你使用了某个恶意的插件或扩展，那风险就大了。 　　还有一点：插件和扩展都有自动升级的机制（可以在 Firefox 选项中禁掉自动升级），可以不断升级到最新版本。 　　说到“软件的自动升级”这个玩意儿，它是两面性的。好处是可以通过这个机制，不断完善软件（比如修复新发现的漏洞）；坏处是，万一某个软件的作者起了歹意，就可以在软件的新版本中悄悄地加入某些流氓功能，而用户却蒙在鼓里，毫不知情。 　　今天要聊的这个招数，不需要依赖任何外部的插件和扩展，所以上述弊端都可以规避掉。 　　不管是插件还是扩展，都会引入一定的性能开销。比如说：会占用更多的内存。【有时候】也会占用一些 CPU 资源。 　　如果不需要额外的插件/扩展，性能上是最合算滴。 　　今天介绍的这个招数，仅仅需要涉及两个文本配置文件。【完全绿色】，而且非常轻量级。 　　不需要任何安装步骤，只需要把配置文件复制到相应目录下，即可生效。 　　对于经常重装系统的同学，方便易用也是一个需要考量的点。 　　Firefox 的 profile 有时候也称为“实例”。在一个系统中，你可以为 Firefox 配置多个 profile，每个 profile 有各自【独立的】收藏夹、【独立的】配置选项（比如代理设置）、【独立的】页面缓存...... 　　默认情况下，Firefox 所有的 profile 都存放在同一个目录的【不同子目录下】（每个【子目录】是一个 profile）。 　　那么，如何找到 Firefox 的 profile 目录捏？下面介绍几种不同的方法。  
　　打开 Firefox，在地址输入 `about:support` 并回车，会进入其 support 界面。其中有一项是 `Profile Directory`（俺用的是英文版，中文版的叫法略有不同）。在这一项右边有一个“打开”的按钮，点击这个按钮就会跳到 profile 目录。 　　不同的操作系统，profile 目录的位置也不同。 　　对于 Windows，你在资源管理器的地址栏输入如下，然后按回车，就进入了。

%APPDATA%\\Mozilla\\Firefox\\Profiles

　　对于 Linux 系统，profile 目录的位置如下

~/.mozilla/firefox/

　　对于 Mac OS 系统，profile 目录的位置如下（有两种可能的位置）

~/Library/Application Support/Firefox/Profiles/
~/Library/Mozilla/Firefox/Profiles/

　　CSS 是洋文“Cascading Style Sheets”的缩写词。中文也称为“层叠样式表”或“级联样式表”。它可以用来定制 Web 页面的排版、布局、字体、颜色...... 　　考虑到某些读者是技术菜鸟，俺再稍微说一下： 　　CSS 与 JS 脚本是【完全不同】滴。JS 脚本本质上是一种程序代码。因此，攻击者可以通过某种手段引诱你执行某些恶意的 JS 脚本，从而让你中招。而 CSS 本质上并【不是】程序代码（CSS【不是】可编程的）——它只是某种形式的配置文件，用来配置网页的展示方式，仅此而已。 　　所以，使用外部的（网上找来的）CSS 文件【没有】安全风险。

　　如果你之前对 CSS 一无所知，俺无法通过这短短的一个章节让你入门。这种情况下，建议你去中文维基百科扫盲一下（链接在“[这里](https://zh.wikipedia.org/wiki/%E5%B1%82%E5%8F%A0%E6%A0%B7%E5%BC%8F%E8%A1%A8)”）。

　　别担心！你不需要很懂 CSS，也可以学会今天这篇教程。很多时候，你只需具备【依葫芦画瓢】的能力，即可 :)  
　　Firefox 提供了某种机制，让用户可以通过 CSS 文件来定制 Firefox 的各种界面。 　　要学会定制，首先要找到 CSS 文件存放的位置。

　　前面已经提到了“profile 目录”。先找到 Firefox 当前 profile 所在的目录。对于大部分普通用户，只会有一个 profile，并且这个 profile 对应的目录名是形如 `xxxxx.default` 这样的形式。

  
　　进入 profile 所在的目录后，在这个目录下还有一个子目录叫做 `chrome`，俺所说的 CSS 文件就放在这个 `chrome` 目录下。 　　（可能有些同学会纳闷：为啥 Firefox 的配置文件存放目录，却用了 chrome 这个名字。其实是先有这个目录名，之后再有 Google 的 Chrome 浏览器）

　　**如果你没找到名叫 `chrome` 的目录，就自己创建一个**

　　为了避免技术菜鸟搞错，俺再唠叨一下。

　　如果你没有发现 `chrome` 目录，然后自己创建了一个。你要确保这个 `chrome` 目录与另一个叫做 `extensions` 目录是【并列】关系（兄弟目录关系）。

  
　　放到 `chrome` 目录下的配置文件有两个，名称分别为如下：  

userChrome.css
userContent.css

　　这两个文件分别有啥用途捏？且听俺细细道来：

`userChrome.css` 是专门用来定制 Firefox 【自身的界面】（比如 Firefox 自己的“地址栏、搜索栏、快捷菜单、滚动条......”）

  
`userContent.css` 是专门用来定制 Firefox 浏览的网站的界面（假如你对俺博客的某些界面效果不爽，就可以用它来定制）  
  
　　虽然 `userChrome.css` 本身是一个 CSS 格式的文件，但是它与普通的 CSS 文件有个不同之处。**它的【第一行】必须是如下形式**  

@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

　　除了上述这点，其它的语法与普通的 CSS 完全一样。 　　这是俺首先要介绍的一招。 　　虽然现在的 Firefox 和 Chrome 都会在地址栏前端用一个小图标来提示 HTTPS 的加密类型。但是那个小图标实在太小了，不够显眼。俺希望把整个地址栏着色，以便更醒目地警告某些不够安全的 HTTPS 加密类型。 　　下面这段 CSS 代码，展示了如何根据 HTTPS 加密类型来设置地址栏的颜色。中文是俺加的注释，不影响 CSS 的使用。

　　关于“混合内容”的概念，可以参见 Firefox 官网的“[这里](https://developer.mozilla.org/en-US/docs/Web/Security/Mixed_content)”。

  

#urlbar
{ position: relative !important; z-index: 1 !important;
} /\* 下面这一大坨样式，是为了作一些准备工作。不懂 CSS 的同学请直接无视之 \*/
#identity-box::after
{ content: "" !important; position: absolute !important; height: 100% !important; width: 100% !important; top: 0 !important; left: 0 !important; opacity: .5 !important; z-index: \-1 !important
} #identity-box.verifiedDomain::after /\* 已验证通过的域名 \*/
{ background-color: PaleGreen !important; /\* 你可以把这行的颜色值改为你自己喜欢的 \*/
}
#identity-box.verifiedIdentity::after /\* 已经验证通过的标识 \*/
{ background-color: PaleGreen !important; /\* 你可以把这行的颜色值改为你自己喜欢的 \*/
}
#identity-box.weakCipher::after /\* 弱加密 \*/
{ background-color: Salmon !important; /\* 你可以把这行的颜色值改为你自己喜欢的 \*/
}
#identity-box.mixedActiveContent::after /\* 混合内容，含“主动内容”（这种尤其危险） \*/
{ background-color: DeepPink !important; /\* 你可以把这行的颜色值改为你自己喜欢的 \*/
}
#identity-box.mixedDisplayContent::after /\* 混合内容，含“被动内容” \*/
{ background-color: Pink !important; /\* 你可以把这行的颜色值改为你自己喜欢的 \*/
}
#identity-box.mixedDisplayContentLoadedActiveBlocked::after /\* 混合内容，其中的“主动内容”已经被禁掉 \*/
{ background-color: Pink !important; /\* 你可以把这行的颜色值改为你自己喜欢的 \*/
}

  
　　每个标签页上的关闭按钮（叉叉）太占用空间，可以设置成——只有当鼠标移动到某个标签页上方，才动态显示那个叉叉。 　　具体代码如下：

.tabbrowser-tab:not(\[selected\]) .tab-close-button
{ visibility: hidden !important; margin-left: \-16px !important;
}
.tabbrowser-tab:not(\[selected\]):hover .tab-close-button
{ visibility: visible !important; margin-left: 0px !important;
}

  
　　如果你嫌快捷菜单太冗长，可以用如下方式隐藏（俺只举2个例子，说明两种不同的隐藏方式）

**第1种方式：根据菜单的标识进行隐藏**

　　下面这个例子，把几个常用的快捷菜单项隐掉。 　　（对俺而言，这些功能太常用，都有对应的快捷键，就不要再浪费菜单的空间了）

#context-copy, /\* 复制 \*/
#context-cut, /\* 剪切 \*/
#context-paste, /\* 粘贴 \*/
#context-delete, /\* 删除 \*/
#context-undo, /\* 撤销 \*/
#context-selectall /\* 全选 \*/
/\* 最后一项末尾【不能】出现逗号 \*/
{ display: none !important;
}

  
　　如果你想隐藏别的菜单项，可以到 Firefox 官网的“[这个链接](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XUL/List_of_commands)”查看各种内置菜单项的“命令名称”，然后稍作修改就变成菜单项的“标识”了——这就是俺所说的【依样画葫芦】 :) 　　举例： “全选”这个功能的命令名是

cmd\_selectAll

该命令在快捷菜单中对应的 CSS 标识是

#context-selectall

  
**第2种方式：根据菜单显示的文字进行隐藏** 　　上面那招是根据菜单的“标识”，但是菜单标识有时候不太好找，于是俺介绍另一个方式——根据显示在菜单项上的文字进行隐藏。 　　下面是俺的举例，摘自本人的 Firefox 配置文件。 　　（再次唠叨：由于俺用的是英文版，所以俺的菜单项上当然是英文。使用中文版的同学，请自行修改引号中的文字）

menuitem\[label\="Reload Tab"\],
menuitem\[label\="Reload All Tabs"\],
menuitem\[label\="Mute Tab"\],
menuitem\[label\="Close Tabs to the Right"\],
menuitem\[label\="Close Other Tabs"\],
menuitem\[label\="Close Tab"\],
menuitem\[command\="Browser:BookmarkAllTabs"\] /\* 最后一项末尾【不能】出现逗号 \*/
{ display: none !important;
}

  
  
　　`userContent.css` 用到了某个特殊的 CSS 语法（`@-moz-document`）。通过这个语法来指定：某个样式只应用到某个特定的网址。 　　这个语法有4种形式，分别如下：

/\*
以下是【严格匹配网址】的语法。俺举的栗子：用来匹配中文维基百科的首页
\*/
@-moz-document url(https://zh.wikipedia.org/)
{
/\* 这里放置 CSS 样式定义 \*/
} /\*
以下是【匹配网址前缀】的语法，可以用来匹配以这部分字符串开头的网址。俺举的栗子：可以用来匹配 Google 搜索在不同国别下的网址。
比如： www.google.com.hk www.google.com.tw www.google.co.uk 都可以被下列方式匹配上。
\*/
@-moz-document url-prefix(https://www.google.)
{
/\* 这里放置 CSS 样式定义 \*/
} /\*
以下是【匹配域名】的语法，可以用来匹配该域名下的所有网址。俺举的栗子：本博客的域名
\*/
@-moz-document domain(program-think.blogspot.com)
{
/\* 这里放置 CSS 样式定义 \*/
} /\*
以下是正则表达式（规则表达式）的语法。俺举的栗子：用来匹配所有的 HTTPS 网址的正则表达式。
请注意，正则表达式需要包含在 半角引号 中间。
\*/
@-moz-document regexp("https:.\*")
{
/\* 这里放置 CSS 样式定义 \*/
}

  
　　先声明：

　　俺仅仅是拿这个来作为示范。即使你从来不在俺博客发评论，也可以通过这个示例学到——如何用 `userContent.css` 去改变某个网站的界面样式。

　　其实捏，本月初俺在重写评论界面时，总觉得 Blogspot 平台默认的“评论编辑框”太矮了，看了很不爽。当时俺在自己的 `userContent.css` 中加了一个样式去改善它。修改的过程中就想到——不如写一篇博文（也就是你正在看的这篇）。

　　插一句题外话

　　本博客的所有页面，俺都可以通过博客管理界面进行定制，除了上面提到的那个“评论编辑框”。因为这个编辑评论的 HTML 页面位于另一个域名（`www.blogger.com`），【无法】通过博客的管理界面定制它。

　　你可以通过如下的语法，定制 blogspot 博客平台的编辑框高度。

@-moz-document url-prefix(https://www.blogger.com/comment-iframe.g)
{ #commentsHolder .commentBodyContainer textarea#commentBodyField { height: 380px !important; /\* 俺设的高度是 380 像素，你也可以调整为其它数值 \*/ }
}

  
　　请注意，俺使用的是【前缀匹配】的语法（`@-moz-document 网址前缀`）。为啥俺不用“严格匹配”而用“前缀匹配”捏？因为这个网址的后半部带了一堆参数（网址中问号后面的那部分）。由于这些参数【不是】固定的（经常会发生变化）。因此，你就没法用“严格匹配”了。  
　　当然啦，也可以用正则匹配的语法（`@-moz-document 网址正则式`）来实现同样的效果。但是考虑到大部分读者不懂正则表达式，所以俺就光拿“前缀匹配”来举例。 　　大多数读者都是不懂 CSS 的，但是没关系。你可以去网上找别人写好的现成的 CSS 来用。 　　下面这个网站大概是全球最大的 CSS 集散地。你可以在那上面找到很多现成的 CSS——这就是拿来主义的好处 :) 当然啦，你要具备基本的洋文阅读能力。

[https://userstyles.org/](https://userstyles.org/)

　　另外，你还要善于使用搜索引擎，就可以搜到很多别人写好的现成的 CSS。关于这方面的技巧和教程，参见俺之前的一个系列：

《[如何挖掘网络资源](https://program-think.blogspot.com/2013/03/internet-resource-discovery-0.html)》。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[扫盲 Firefox 定制——从“user.js”到“omni.ja”](https://program-think.blogspot.com/2019/07/Customize-Firefox.html)》  
《[如何用 GreaseMonkey 扩展 Google Reader](https://program-think.blogspot.com/2011/11/greasemonkey-scripts-for-google-reader.html)》  
《[弃用 Chrome 改用 Firefox 的几点理由——关于 Chrome 69 隐私丑闻的随想](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)》  
《[如何防止黑客入侵](https://program-think.blogspot.com/2010/06/howto-prevent-hacker-attack-0.html)》（系列）  
《[如何挖掘网络资源](https://program-think.blogspot.com/2013/03/internet-resource-discovery-0.html)》（系列）

