---
layout: default
title: '博客评论功能升级&#65288;增加&#8220;留言过滤&#8221;&#12289;&#8220;200条之后自动加载&#8221;等&#65289;'
date: None
author:
    display_name: 
---

　　话说两年前（2012年9月），俺对 BlogSpot 博客平台的“评论/留言功能”进行了一次定制。当时增加了“嵌套评论”（两层），增加了“评论中插入图片、超链接、粗体”（采用 BBCode 语法）。

　　最近两年来，博客的访问量大增，因此评论数也大增。尤其是最近一个季度，几乎每篇博文的评论数都超过200条。这就引出几个【易用性】的问题：

1\. BlogSpot 平台默认只加载开头200条评论 2. 如果你想看全部评论，要自己去页面底部点击“加载更多” 3. 如果评论数太多（比如超过300条），你需要连续点击好几次“加载更多”，点得手指头都抽筋了（已经有好几个人来抱怨了） 3. 虽然俺在页面上用醒目的红色粗体进行了提示，但是很多粗心的读者并不知道要去点击“加载更多” 4. 如果这些粗心的读者去发评论，（并是在200条之后）他们就以为评论发不出来（已经有好几个人来抱怨了） 5. 已经有好几个热心读者提出建议，要求加入类似论坛的过滤功能（比如：“只看此人”、“不看此人”） 　　虽然俺是个老程序猿，不过捏，Web 界面并不是俺擅长滴。再加上本人也比较懒，所以对上述抱怨也没有及时处理（在此深表道歉）。 　　但是最近几个月，俺自己也受不了了——每次回复评论，都要点击“加载更多”，点得心烦。所以这几天痛下决心，终于把上述几个问题都搞定了。然后顺便也稍微美化一下评论区的界面。  
  
　　**功能描述** 　　如题。

　　**前提条件**

　　你的浏览器必须开启“JavaScript 脚本功能”（所有主流的浏览器，默认都开启该功能）。 　　如果你把浏览器的 JS 脚本功能给禁用了，打开俺博客界面时，会看到醒目的提示。

　　**补充说明**

　　如果某篇博文的评论数比较多（比如大于300），你可能需要稍等片刻。为了界面友好，俺在评论区的开头位置会显示一个动态的文字提示，以表面正在加载。  
　　**功能描述** 　　目前支持两种过滤： 1. 只看某人的【相关】的评论 （包括：此人的评论、此人回复的评论、回复此人的评论。其它统统都隐藏） 2. 隐藏某人的【相关】评论 （包括：此人的评论、回复此人的评论） 　　在每一条留言的底部，会显示 2-3 个超链接。为了避免超链接太多，影响整个界面的视觉效果，俺目前采用的是“mouse hover”的风格——只有当鼠标移动到这条留言上，才会显示相应的超链接。

　　**补充说明**

　　如果是【已经】登录过 Google 帐号的用户，可以进行精确的过滤。 　　如果是【没有】登录过 Google 帐号的用户，但是设置了“网名”，俺根据网名进行过滤。这种情况下，【无法区分】“同名用户”。典型的例子就是：俺博客至少有两位长期读者，都用了“忠党爱国”这个网名（一个自称是“网评员”，另一个专门与之抬杠）。 　　对于“匿名用户”，只提供“功能2”，不提供“功能1”（貌似没啥意义）。

　　**前提条件**

　　你的浏览器必须开启“JavaScript 脚本功能”（所有主流的浏览器，默认都开启该功能）。 　　如果你把浏览器的 JS 脚本功能给禁用了，打开俺博客界面时，会看到醒目的提示。  
　　**功能描述** 　　最近2年来，发现不少读者喜欢在评论中粘贴网址。为了方便大伙儿直接点击，俺支持一种新的“自定义语法”——对于评论中的网址，如果两边都是空格或换行，该评论发布后，这个网址会自动变成可点击的超链接。

　　**前提条件**

　　俺博客评论区的所有“自定义语法”功能都是通过 JS 脚本实现滴——这个自然也不例外。  
　　**功能描述** 　　这是用来显示某些通知信息的。比如当博客的评论加载完之后，会提示一下。 　　为了避免影响阅读，这个提示框只出现在页面最底部，而且会在几秒钟之后自动消失。

　　**补充说明**

  
　　对于那些禁用了 JS 脚本的浏览器，这个提示框会一直存在并显示：你的浏览器不支持 JavaScript 脚本, 导致某些功能无法正常显示 :( 　　为啥“提示框会一直存在”？因为提示框的自动消失靠的是 JS 脚本来实现的。  
　　上述介绍的这些新功能，都是这几天晚上匆忙赶出来的，而且俺的 CSS 水平基本上属于三脚猫功夫。所以，可能会有一些 Bug。

　　**如果你发现了啥问题，敬请告知，俺会非常感谢。**

　　搞过 Web 开发的同学应该明白——要兼容不同浏览器（尤其是老版本 IE），是非常头疼的事情。 　　目前为止，俺只测试了如下几款浏览器： Firefox 32 for Linux Chrome 37 for Windows IE 8 　　初步感觉：新版的 Firefox 和 Chrome，应该没啥问题。至于 IE8，“自动加载评论”和“评论过滤”这两个功能貌似都有问题（估计 IE6 更惨）。解决的希望比较渺茫（IE 对 W3C 标准的实现，太烂了）。有空的话，俺再测试一下新版本的 IE，看看效果如何。希望俺能搞定 IE8 之后的版本。

　　**如果你用的浏览器碰到兼容性问题，请帮忙反馈一下，先行谢过。**

　　如果你对本博客的界面功能有啥想法，欢迎在博客留言中告知俺。 　　俺趁着这几天写 JS/CSS 的热情还没消退，再一鼓作气多做些界面完善。 　　如果你自己也是博主，需要了解相关的技术，建议你先自己去看俺博客的 HTML 源代码（“JS 脚本”和“CSS 样式”都包含在其中了）。对于想搞“Web 界面开发”或“Web 界面美化”的同学，看别人页面的源代码是基本功。 　　如果你看了俺博客的 HTML 源代码还是搞不定，可以到本文留言，俺会提供友情支持 :) 　　假如有比较多的人来询问相关的技术实现，俺再单独发一篇帖子作介绍。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
[博客评论功能升级（智能贴图、图片代理）——兼谈“Web 图片的隐私问题及防范”](http://program-think.blogspot.com/2015/04/custom-blogger-comment.html)  
[博客评论功能升级（“未读”状态、按时间过滤）——兼谈“为啥俺不用其它博客平台”](http://program-think.blogspot.com/2014/12/custom-blogger-comment.html)  
[博客界面升级（增加“界面定制”、“文章目录”、“自动刷评论”、“全屏显示”等）](http://program-think.blogspot.com/2014/10/custom-blogger-ui.html)  
[博客评论功能升级（引入 BBCode 语法），顺便分享一下实现方法](http://program-think.blogspot.com/2012/09/custom-blogger-comment.html)
