---
layout: default
title: '扫盲 Firefox 定制&#8212;&#8212;从&#8220;user.js&#8221;到&#8220;omni.ja&#8221;'
date: None
author:
    display_name: 
---

　　最近一年，写过好几篇涉及“Web 安全”的博文。这些博文或多或少都会提及“Firefox 的定制”。考虑到某些读者对这方面不太了解，单独写一篇扫盲。 　　如果你从来不用 Firefox 浏览器，本教程就不用看了（以免浪费时间）。 　　本文主要面向不太熟悉 Firefox 的菜鸟；对于 Firefox 的老鸟，顶多只需要看“高级话题”相关的章节。  
　　Firefox 支持【多实例】（多个 profile）。你可以把“profile”这个概念通俗理解为：“独立的浏览器环境”。 　　也就是说，实例之间是【互相隔离】滴，每个实例都有自己【独立的】“书签、浏览历史、下载历史、cookies ......” 　　就算你从来没有创建过实例，只要你通过 Firefox 上网，你的 Firefox 至少会有一个实例（也就是你正在用的这个）。 　　每个实例（profile）都对应一个目录，属于该实例的那些东西（书签、浏览历史、下载历史、cookies ...）全都存储在该目录下。 　　要想查看你正在使用的 Firefox 实例对应的目录，很简单：

1\. 在浏览器地址栏输入 `about:support` 然后敲回车

  
2\. 这时候会显示一个支持页面，其中有一项 `Profile Directory`（俺用的是英文版，中文版的叫法略有不同），对应的就是【当前实例的目录】。  
　　“配置选项”也叫“首选项”，洋文称之为“Preferences”。 　　通俗地说就是：Firefox 提供了一大堆可供用户定制的参数。通过修改这些参数，可以对 Firefox 进行【全方位】定制。 　　每个 Preference 包含如下几个要素：

　　**名称**

　　每个 Preference 的名称必定是【唯一】滴。 　　“名称”由英文单词构成，单词之间以“小数点”或“下划线”分隔。

　　**数据类型**

　　Preferences 的“数据类型”必须是“布尔型、整数型、字符串型”这三者之一。 　　“布尔型”的值只能是 true 或 false。 　　“整数型”的值可以是负数。

　　**默认值**

　　每个 Preference 都有个“默认值”。 　　“默认值”包含在 Firefox 的安装包里面。 　　绝大多数用户并【不需要】去修改“默认值”。

　　（注：极少数有此需求的读者，可以去本文的高级话题——autoconfig这个章节）

　　**当前值**

　　每个 Preference 都对应某个“当前值”。 　　当你修改 Preference 的时候，修改的就是它的“当前值”。 　　一开始的时候，每个 Preference 的“当前值”就等于它的“默认值”；如果该 Preference 被定制了（修改了），其“当前值”与“默认值”就有可能不同。 　　首先，Firefox 的用户当然可以修改配置选项（具体如何做，后续章节会细聊） 　　除了用户，【浏览器扩展】也可以添加或修改“配置选项”。某些扩展会提供定制界面，让用户设定某些参数。这些参数也保存在浏览器的 Preference 里面。 　　有必要强调一下：网站上的 JS 是【无法修改】Preference 滴！ 　　道理很简单：因为 Firefox 的 Preference 中保存了很多与安全性相关的配置参数。如果允许网站的 JS 修改这些参数，将会成为巨大的安全隐患。 　　俺总结下来，大致有如下几种需求：

　　**1\. 安全加固**

　　你可以通过定制很多的 Preferences 以大大强化 Firefox 的安全性（包括隐私防护能力）。 　　每次 Firefox 的新版本增加了某个比较重要的安全相关的定制选项，俺会在每季度的《近期安全动态和点评》提醒大伙儿。

　　**2\. 性能优化**

　　通过定制 Preference 可以优化性能（包括：“网络传输、内存使用、界面渲染”等方面）

　　**3\. 易用性**

　　通过定制 Preference，你还可以改进 Firefox 界面的易用性。  
　　修改 Firefox 的 Preference，最简单的方式就是“about:config”界面了。

　　你在浏览器地址栏输入 `about:config` 然后敲回车，就进入该界面。

　　（提醒一下：打开该界面时，你可能会看到一个警告提示，别慌张） 　　“about:config”界面主要是个的表格，共4列，分别是： 　　第1列：Preference 的“名称” 　　第2列：Preference 的“状态”（如果显示“default”表示该 Preference 还没被修改过，显示“modified”表示已经被改过） 　　第3列：Preference 的“数据类型” 　　第4列：Preference 的“当前值” 　　该界面默认会列出 Firefox【所有的】Preference（成百上千个）。某些菜鸟一看到这个架势，可能会有点晕。 　　别慌，界面上方有一个搜索框，可以帮你进行【筛选/过滤】。

　　该搜索框针对 Preference 的名称进行【模糊匹配】。比如说：你在搜索框中输入 `network`，那么界面上就只列出名称中包含 `network` 的那些 Preferences。

　　对于“布尔型”的 Preference，你双击 Preference 所在的这行，就可以修改它的“当前值”（在 true 与 false 之间切换） 　　对于其它数据类型，双击 Preference 所在的行，会弹出一个对话框，让你输入【新的】数值。 　　所谓的“重置”（reset）就是指“恢复默认值”。 　　（对于已经被改过的 Preference）选中它所在的那行；点右键；在快捷菜单上有一项“Reset”（重置）；使用这个菜单项就可以把该选项重新恢复成默认值。 　　在“about:config”界面的表格上点右键；在快捷菜单上有一项“New”（新增）；可以让你添加一个新的 Preference。 　　添加时会让你指定新 Preference 的“名称”和“数值”。  
　　你在“about:config”界面的搜索框中输入 `general.warnOnAboutConfig`，此时只会过滤出一个 Preference，这个 Preference 是“布尔型”。当它的值是 `true`，每次你打开“about:config”界面都会显示警告提示；反之，则不显示。 　　你可以修改这个 Preference 的值。修改之后再【重新打开】“about:config”界面，体会一下效果。  
  
　　每个 Firefox 实例中都有名为 `prefs.js` 的配置文件。这个文件保存了当前实例中【所有】Preferences 的设置。 　　该文件位于每个【实例目录】下。  
　　该文件的扩展名是 `.js`，说明其内容是 javascript 语法。  
　　在 javascript 语法中，任何一行中如果出现【双斜杠】`//` ，那么“从双斜杠一直到行尾”都算【注释】；另外，包含在 `/*` 和 `*/` 之间的内容也是【注释】。（注：第二种注释可以跨越多行） 　　除了注释之外，该文件的每一行有效代码对应一个 Preferences。文件中的每个有效代码行全都是如下这个样子：

user\_pref("配置项名称", 配置项数值);

  
　　由于每一个 Preferences 的名称都是字符串，因此上述代码中的 `配置项名称` 总是包含在【半角引号】中。 　　如果某个 Preferences 的数据类型属于“字符串型”，那么上述代码中的“配置项数值”也要包含在【半角引号】中；否则，就不需要使用引号。  
　　**【不要】直接修改 `prefs.js` 文件！！！** 　　如果你想通过【配置文件】的方式定制 Firefox 的 Preferences，请使用【user.js】（参见下一个章节）。  
  
　　Firefox 使用名为 `user.js` 的文件对 Preferences 进行个性化定制。  
　　该文件位于【实例目录】下。请注意：**默认情况下【没有】这个文件！** 　　如果你想用这种方式定制 Firefox，需要在【当前实例】的目录下【手动创建】该文件，然后往这个文件中添加代码。  
　　该文件的格式与 `prefs.js` 相同。具体介绍参见“前一个章节”。 　　前面介绍“about:config”界面时，已经让你做了一个小小的练习。 　　现在，咱们在“user.js”中继续进行这个练习——

　　当你创建好一个空的 `user.js` 文件，在文件中添加如下代码，并存盘。

  

user\_pref("general.warnOnAboutConfig", false);

　　（注：上述代码中的“括号、引号、逗号、分号”必须都是【半角符号】） 　　上述文件存盘之后，你把 Firefox 重新启动，然后再打开“about:config”界面，这时候就不会再有那个讨厌的警告信息了。 　　如果你已经在“user.js”中修改过某个 Preference，之后又想恢复其默认值。请参照如下步骤： 1. 先在“user.js”中把这个 Preference 的配置“删除”或“注释掉”； 2. 重启浏览器； 3. 再到“about:config”界面进行重置操作。 　　当你要通过这种方式修改某个选项，先搞清楚这个选项的含义和用途，并了解可能的【副作用】。  
  
　　当 Firefox 启动的时候，会读取 `user.js` 和 `prefs.js`，拿到这两个文件中的 Preferences 配置，并保存在内存中。  
　　如果发现这两个文件的配置有冲突，以 `user.js` 为准（也就是说：“`user.js` 的配置”会覆盖“`prefs.js` 的配置”）。 　　如果同一个配置项在某个文件中出现多次，后面的代码行会覆盖前面的代码行。 　　当你打开“about:config”界面，Firefox 会把内存中的 Preferences 信息显示给你看。

　　如果你在这个界面上进行了修改，修改的结果会保存在内存中，同时也会保存到 `prefs.js` 文件中。

  
　　另外，Firefox【不会】去修改你用于定制的 `user.js` 文件。 　　“高级话题”是专门针对“Firefox 老鸟”，尤其是那些具有“geek 精神”（善于折腾）的用户。

　　（熟悉本博客的读者应该知道：俺一向鼓励【折腾】，并写过一篇博文《[聊聊【折腾】的重要性](https://program-think.blogspot.com/2017/04/The-Importance-of-Zheteng.html)》）

　　至于菜鸟嘛，先搞定前面章节介绍的内容，学会怎么用“user.js”；然后再考虑本文的“高级话题”。 　　考虑到本章节的特点，“高级话题”的介绍只是【点到为止】——对于【善折腾】的读者，俺只需给出一个方向，他们自然能沿着这个方向走得足够远。 　　通过“user.js”，虽然可以让你定制每一个 Preference；但至少有如下局限性：

　　**局限性1——【无法】修改某个 Preference 的【默认值】**

  
　　请注意：在 `user.js` 中修改的是【当前值】。不管“当前值”如何变，“默认值”【没】变。 　　在某些特殊场合，你可能想要定制 Preference 的【默认值】。

　　**局限性2——【无法】锁定某个 Preference**

　　所谓的“锁定”就是“禁止修改”的意思。 　　比如说：某个第三方扩展会修改某个 Preference 的值；但你又不希望这个 Preference 被修改。这时候就可以把这个 Preference【锁定】。 　　Firefox 的扩展能力及其强大，当然能满足上述这些怪异的需求。

　　Mozilla 提供了名为【autoconfig】的机制，可以更进一步地定制 Preference。具体参见 Mozilla 官网的“[这篇教程](https://support.mozilla.org/en-US/kb/customizing-firefox-using-autoconfig)”（洋文）。

  
　　在 `user.js` 中，咱们只能使用 `user_pref` 这个函数；而在【autoconfig】这种定制方式中，还提供了更多的函数，至少包括如下（代码中绿色的部分是注释）：  

defaultPref("配置项名称", 配置项数值); // 该函数用于：定制配置项的【默认值】
lockPref("配置项名称", 配置项数值); // 该函数用于：设置配置项的默认值并【锁定】
unlockPref("配置项名称"); // 该函数用于：【解锁】配置项
clearPref("配置项名称"); // 该函数用于：把配置项的【当前值】恢复为【默认值】

  
　　“autoconfig”虽然比“user.js”更牛逼，但其能力只局限于 Preference 相关的定制。 　　有些你想定制的东西（比如：默认的键盘快捷键）【并不】保存在 Preference 中——也就是说，即便你去捣鼓“autoconfig”也【搞不定】！这时候就要引入【终极大杀器】——直接修改【omni.ja】。 　　顺便插一句： 　　自从 Firefox Quantum（Firefox 57）之后，旧的“XPCOM 扩展机制”已经淘汰，换成新的“WebExtensions 扩展机制”。但是，“新扩展机制”的功能比原来要弱（据说是为了安全性的考虑）。比如：对“键盘快捷键”的定制能力就变弱了。 　　在这种情况下，“定制 omni.ja”的优势就更加明显——因为它能做到“用扩展无法完成的事情”。 　　Firefox 是一个很复杂的开源项目，代码量超大。它的核心代码（比如：渲染引擎、JS 引擎）是基于 C++ 语言开发（并在逐步迁移到 Rust 语言）。而软件界面（UI）相关的部分，大体上还是 Web 那套东西（不外乎就是：XML、JS、JSON、CSS ...）。

　　这些与 UI 相关的东西，大部分都打包在（安装包自带的）`omni.ja` 文件中。如果你摸透了 `omni.ja` 的结构，就可以对 Firefox 的界面进行任意定制。

  
　　说到这里，某些熟悉 Firefox 的用户会反问：为啥不用 `userChrome.css` 定制 Firefox？  
　　这个东东俺当然知道（而且还写过专门的教程，链接在“[这里](https://program-think.blogspot.com/2016/10/custom-firefox-theme-without-extension.html)”）。但它的能力很【有限】——只能修改 CSS 样式，【无法】定制界面的功能。 　　举个【简单】例子： 　　比如说 Firefox 的默认快捷键中，【Ctrl + q】会退出整个进程；

　　如果你不喜欢这个快捷键，可以换成一个更顺手的（通过修改 `omni.ja` 里面的 `chrome/en-US/locale/browser/browser.dtd`）

　　举个【复杂】例子： 　　或许很多 Firefox 用户不知道——你可以用【Alt + 数字键】或【Ctrl + 数字键】来切换 Firefox 的标签页。 　　（注：俺在 Linux 用的是 Alt，而 Windows 环境用的是 Ctrl） 　　当你在 Firefox 界面上按了这个组合键，会触发某个 JS 代码，然后由这个 JS 代码来改变当前标签页的状态。

　　而这段 JS 代码就包含在 `omni.ja` 这个压缩包的某个文件中（`chrome/browser/content/browser/browser.xul`）。如果你能修改这段 JS 代码，就可以实现自己想要的某些效果。

　　**友情提醒：**

  
　　安装好的 Firefox 有【两个】 `omni.ja` ——大的那个有30多兆，小的那个有十多兆。 　　当你要折腾的时候，别搞错了！！！ 　　比如说：当俺在折腾键盘快捷键时，修改的是【大的】那个。  
　　**如何“解压缩”？**  
　　虽然 `omni.ja` 的扩展名是 `.ja`，但其实是个 zip 压缩包；但它又【不是】标准的 zip 压缩包——因为它的文件头有点特殊。  
　　俺在 Linux 下用 `unzip` 命令进行解压缩，完全 OK（使用 Mac OS 的同学也可以用这个命令）；  
　　对于使用 Windows 的同学，（Mozilla 官网的文档建议）先把扩展名改为 `.zip` 再用资源管理器自带的解压功能（注：其它解压 zip 的工具不一定能行）。

　　**如何“压缩（重新打包）”？**

  
　　当你【修改完】`omni.ja` 内部的文件之后，要【重新打包】该文件。 　　对于 POSIX 环境（Linux & UNIX），Mozilla 官网的文档建议使用如下命令：

zip -qr9XD omni.ja \*

  
　　简单说几个注意事项：

　　**第1条**

  
　　`omni.ja` 内部的文件很多。只修改那些【你有把握】的文件。  
　　如果你把 `omni.ja` 内部的某些文件改坏了，可能会导致 Firefox 无法启动，而且也没有任何报错信息。

　　**第2条**

  
　　每次修改完 `omni.ja`，为了让你的修改生效，要记得：先退出 Firefox【进程】；然后清空整个缓存目录；最后再启动 Firefox。

　　**第3条**

　　由于每次修改完都要做“打包、清缓存、重启 Firefox”这几件事情。俺建议：搞个命令行脚本帮你自动干这些事儿，以提升效率。

　　**第4条**

  
　　`omni.ja` 会随着 Firefox 的版本而变化。也就是说，每次有新版本，你还需要在新版本上再修改一次。 　　如果结合第3条与第4条，你更应该写一个脚本，帮你【自动化】完成整个定制流程。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[无需任何插件或扩展，定制 Firefox 外观](https://program-think.blogspot.com/2016/10/custom-firefox-theme-without-extension.html)》  
《[基于安全考虑，如何选择及切换 Firefox 版本？](https://program-think.blogspot.com/2018/10/How-to-Choose-Firefox-Version.html)》  
《[弃用 Chrome 改用 Firefox 的几点理由——关于 Chrome 69 隐私丑闻的随想](https://program-think.blogspot.com/2018/09/Why-You-Should-Switch-from-Chrome-to-Firefox.html)》  
《[如何用 GreaseMonkey 扩展 Google Reader](https://program-think.blogspot.com/2011/11/greasemonkey-scripts-for-google-reader.html)》  
《[聊聊【折腾】的重要性](https://program-think.blogspot.com/2017/04/The-Importance-of-Zheteng.html)》

