---
layout: default
title: '博客评论功能升级&#65288;引入 BBCode 语法&#65289;&#65292;顺便分享一下实现方法'
date: None
author:
    display_name: 
---

  
　　最近一年来，翻墙到俺博客留言的读者日渐增多。留言多了之后， Blogger / BlogSpot 平台的评论功能就越发显得老土了。这个周末，俺痛下决心，把默认的评论功能彻底改造一下。这番改造，主要增加了如下几个功能：  
**1\. 增加嵌套评论的功能** 通过嵌套评论，直接回复前几楼的留言就方便了。 由于 Blogger / BlogSpot 平台在功能上仅支持两层嵌套。所以，目前俺还搞不出多层嵌套。

**2\. 增加楼层数的显示**

类似 BBS 论坛的效果（目前不支持 IE 8 之前的版本）。

**3\. 增加评论者的头像**

如果登录过 Gmail 或 OpenID，会显示用户的头像。对于匿名用户，显示默认头像。

**4\. 评论支持 BBCode 语法**

可以在评论中使用常见的几种 BBCode 语法，目前支持如下4种：

超链接

\[url\]网址\[/url\]

带标题的超链接　

\[url=网址\]标题\[/url\]

图片

\[img\]图片的网址\[/img\]

粗体文字

\[b\]加粗的文字\[/b\]

关于 BBCode 的更多介绍，请看"[这里](https://zh.wikipedia.org/wiki/BBCode)"。

**5\. 调整了背景颜色和边框**

主要是为了看起来爽一点。

　　针对上述新功能，欢迎大伙儿多提意见和建议，便于俺改进（点"[这里](http://program-think.blogspot.com/2012/09/custom-blogger-comment.html#comments)"发表你的高见）。

　　下面是改造后的评论功能截图，如果你的浏览器看到的效果有差异，敬请告知你的浏览器版本。

![不见图 请翻墙](https://lh5.googleusercontent.com/jAtB5-K0PTdgslIj6TsdaGTKYSHAuHmNvvQfW0v_X4VHs6wXfZULjnV6ccLyk5k3yc6XfUHtXLoYEW5_Zxwh7AkZVGTxqZ8RTMWAs6l1vAU7BStzPQ)

　　接下来，俺分享一下具体的实现方式，希望对其他 Blogger / BlogSpot 上的博主有帮助。如果你没有在 Blogger / BlogSpot 上开博客，那后面的内容就无需再看了。 ================华丽的分割线================ 简介： 嵌套评论功能由于涉及到后端，需要 Blogger / BlogSpot 平台的支持才有可能实现。幸运的是，Blogger / BlogSpot 平台在今年开始提供"嵌套评论"的功能。 由于平台提供支持，只需要简单修改一下模板即可实现。 步骤： 首先，进入 Blogger 的后台管理界面，点左边菜单上的 "模板" 按钮。 出现模板管理界面后，再点 "修改HTML" 按钮。 出现一个对话框，点 "继续" 按钮。 然后勾选 "扩展窗口小部件模板 "。 此时，你就可以看到模板的编辑界面了。

**为了保险起见，在编辑之前先备份一下模板。**

在模板中找到如下代码：

> <b:if cond='data:blog.pageType == &quot;item&quot;'>   <b:include data='post' name='comments'/> </b:if>

修改为如下：

> <b:if cond='data:blog.pageType == &quot;item&quot;'>   <b:if cond='data:post.showThreadedComments'>     <b:include data='post' name='threaded\_comments'/>   <b:else/>     <b:include data='post' name='comments'/>   </b:if> </b:if>

最后点 "保存" 按钮。 如果不出意外，你的博客就有嵌套评论功能了。 添加评论的楼层数，有很多种方法。比较简单的有如下两种。 简介： 直接在模板中嵌入 JS 代码。利用模板中的 loop 循环，递增楼层号并显示。 优点： 支持各种浏览器 缺点， 适合用于传统的评论界面。对于新的嵌套评论界面，需要对模板进行大改，比较难搞。 步骤： 根据刚才介绍过的步骤，进入模板编辑界面。

**为了保险起见，在编辑之前先备份一下模板。**

在模板中找到如下代码：

> <b:loop values='data:post.comments' var='comment'>  

修改为如下：

> <script type='text/javascript'>nCommentIndex = 1;</script> <b:loop values='data:post.comments' var='comment'>   <span class='comment-index'>     <script type='text/javascript'>document.write('第'+nCommentIndex+'楼'); nCommentIndex+=1;</script>   </span>

最后点 "保存" 按钮。 如果你想调整楼层号的显示样式，可以在模板的 CSS 代码尾部追加如下代码： （请根据自己的喜好修改下划线部分）

> .comment-index {  
>   float: 浮动靠左还是靠右;  
>   font: 用啥字体;  
>   font-size: 字体大小;  
>   color: 用啥颜色; }

全部修改完之后，点 "保存" 按钮。 简介： 利用 CSS 的计数器功能，实现楼层号的递增及显示。 优点： 支持嵌套评论的界面 缺点： 浏览器兼容性不够好（比如 IE6 不支持 CSS 的 content 属性） 步骤： 根据刚才介绍过的步骤，进入模板编辑界面。

**为了保险起见，在编辑之前先备份一下模板。**

在模板代码中，找到 CSS 的那段代码，然后在 CSS 代码的尾部追加如下代码： （以下这2段代码就是俺博客用的，欢迎剽窃） 这一段用来显示楼层号

> .comment-thread ol {   counter-reset: comment\_counter; } .comment-thread li:before {   content: counter(comment\_counter,decimal) "楼";   counter-increment: comment\_counter;   float: right;   position: relative;   z-index: 1;   text-align: center;   font-size: 120%;   color: $mainLinkColor;   border: none;   margin-top: 10px;   margin-right: 10px;
> 
> }

这一段用来显示嵌套在某楼层之下的单元号

> .comment-thread ol ol {   counter-reset: child\_comment\_counter; } .comment-thread li li:before {   content: counter(comment\_counter,decimal) "楼 " counter(child\_comment\_counter,decimal) "单元";   counter-increment: child\_comment\_counter;   font-size: 100%;
> 
> }

修改完之后，点 "保存" 按钮。 根据刚才介绍过的步骤，进入模板编辑界面。

**为了保险起见，在编辑之前先备份一下模板。**

在模板中找到如下代码：

> <dl id='comments-block'>  

修改为如下：

> <dl expr:class='data:post.avatarIndentClass' id='comments-block'>  

还没完，就在这行代码下方2-3行的地方有如下代码：

> <a expr:name='data:comment.anchorName'/>  

修改为如下：

> <a expr:name='data:comment.anchorName'/> <b:if cond='data:blog.enabledCommentProfileImages'>   <div expr:class='data:comment.avatarContainerClass'>     <data:comment.authorAvatarImage/>   </div> </b:if>

如果你想调整头像的显示尺寸，可以在模板的 CSS 代码尾部追加如下代码： （请根据自己的喜好修改下划线部分）

> .comments .avatar-image-container img {  
>   width: 图像宽度;  
>   height: 图像高度;  
>   border: 图像边界; }

修改完之后，点 "保存" 按钮。  
　　今天就先介绍到这里。以后如果有空，俺还会继续改进本博客的评论功能。相关的代码也会继续补充到本文中。欢迎其它博主[到本文留言](http://program-think.blogspot.com/2012/09/custom-blogger-comment.html#comments)，交流经验。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
[博客评论功能升级（智能贴图、图片代理）——兼谈“Web 图片的隐私问题及防范”](https://program-think.blogspot.com/2015/04/custom-blogger-comment.html)  
[博客评论功能升级（“未读”状态、按时间过滤）——兼谈“为啥俺不用其它博客平台”](https://program-think.blogspot.com/2014/12/custom-blogger-comment.html)  
[博客评论功能升级（增加“留言过滤”、“200条之后自动加载”等）](https://program-think.blogspot.com/2014/09/custom-blogger-comment.html)

