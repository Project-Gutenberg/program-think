---
layout: default
title: '澄清&#8220;自由软件&#12289;开源软件&#8221;相关概念及许可证的误解'
date: None
author:
    display_name: 
---

　　长期以来，一直有很多读者不太明白“自由软件”与“开源软件”的差异。除此之外，还经常会有其它的一些误解。

　　昨天正好在[俺的网盘](https://github.com/programthink/books)上分享了《若为自由故——自由软件之父理查德·斯托曼传》一书的中文版，所以顺便来聊聊相关的话题。

  
　　这可能是最常见的误解，所以俺把这条放在本文第一条。 　　“提供源代码”只是“开源软件”的【必要条件】，但【不是】充分条件。换句话说：不提供源码的一定不是开源软件，提供源码的不一定是开源软件（有点像绕口令）

　　所谓的“开源软件”，是有严格定义滴！目前业界的共识是采用“[开放源代码促进会](https://zh.wikipedia.org/wiki/%E5%BC%80%E6%94%BE%E6%BA%90%E4%BB%A3%E7%A0%81%E4%BF%83%E8%BF%9B%E4%BC%9A)”（洋文叫“Open Source Initiative”，缩写是 OSI）给出的定义。

  
　　其定义很长，包含很多项，俺就不全文列出啦。想看的同学，请猛击 OSI【官网】的“[这个链接](https://opensource.org/osd)”。不懂洋文的同学，请看中文维基百科的“[这个页面](https://zh.wikipedia.org/wiki/%E5%BC%80%E6%BA%90%E8%BD%AF%E4%BB%B6)”。 　　为了让大伙儿加深印象，举 UNIX 的例子。

　　说到 UNIX，在计算机史上那可是大名鼎鼎滴。其背景，俺就不多说啦。当年（上世纪70年代）UNIX 隶属于商业公司 [AT&T](https://en.wikipedia.org/wiki/AT%26T)。那年头，AT&T 销售 UNIX 的时候都会附送【全部源代码】。但即使这样，（以如今的标准来看）UNIX 也【不能】算是开源软件。因为用户拿到源代码之后，受限于保密条款，【无法】随意分发源代码。

　　“开源软件”与“自由软件”这两个概念有很大的重叠，导致很多人混淆这两者（误以为这俩概念可以互换）。 　　但其实这两者在理念上有【很大】差异。考虑到本文是面向普通读者，俺尽可能用通俗的大白话来说一下两者的共性和差异。 　　共性大致有如下几条： 1. 两者都要求——源代码要【公开】 2. 两者都要求——公开的源代码必须具备【完整性】（换句话说，用公开的源码必须能重新生成该软件） 3. 两者都要求——公开的源代码要允许【随意分发】 4. 两者都要求——公开的源代码要允许【随意修改】 5. 两者都要求——【不能】限制商业使用 ...... （还有其它一些共同点，考虑到篇幅，就不再列举啦） 　　“开源软件”的立足点更加侧重于——源代码的【开放性】。 　　“自由软件”的立足点更加侧重于——软件用户的【自由度】。 　　考虑到很多人不太清楚“用户的自由”，俺来介绍一下——

　　FSF 的创始人 [理查德·斯托曼](https://zh.wikipedia.org/wiki/%E7%90%86%E6%9F%A5%E5%BE%B7%C2%B7%E6%96%AF%E6%89%98%E6%9B%BC)（Richard Matthew Stallman，人称 RMS）给出了【用户的四大自由】：

  

> 自由度0： 无论用户出于何种目的，必须可以按照用户意愿，自由地运行该软件。 自由度1： 用户可以自由地学习并修改该软件，以此来帮助用户完成用户自己的计算。 （作为前提，用户必须可以访问到该软件的源代码） 自由度2： 用户可以自由地分发该软件的拷贝，这样就可以助人。 自由度3： 用户可以自由地分发该软件修改后的拷贝。借此，用户可以把改进后的软件分享给整个社区令他人也从中受益。
> 
> （作为前提，用户必须可以访问到该软件的源代码）

  
　　更详细的介绍可以参见 FSF（[自由软件基金会](https://zh.wikipedia.org/wiki/%E8%87%AA%E7%94%B1%E8%BD%AF%E4%BB%B6%E5%9F%BA%E9%87%91%E4%BC%9A)）【官网】的文章（如下）：  
《[What is free software?](https://www.gnu.org/philosophy/free-sw.html)》（原文）  
《[什么是自由软件？](https://www.gnu.org/philosophy/free-sw.zh-cn.html)》（上述的中文翻译） 　　引申阅读：

　　[俺的网盘](https://github.com/programthink/books)上分享了【自由软件运动创始人】理查德·斯托曼（RMS）的“选集”和“传记”，分别如下：

  
《[自由软件，自由社会——理查德·斯托曼选集](https://docs.google.com/document/d/1kTL8VE6AoUZCJY2OJ3qv39nJpFn7zj6EacAHXyNXfEY/)》  
《[若为自由故——自由软件之父理查德·斯托曼传](https://docs.google.com/document/d/1J6AfA8Z4uUiMS7-Or9WchCuiDEc-G6Ar5D3600jxYSQ/)》 　　（注：本文后续部分提到的“许可证、许可协议、license”三者指同一个东东） 　　刚才俺聊到了“自由软件”与“开源软件”在理念上的差异。这些差异自然也会反应到 license 的条款上。比如有些 license 立足于“开源”，还有些 license 立足于“自由”。

　　为了方便大伙儿，给出一个维基百科链接（在“[这里](https://zh.wikipedia.org/wiki/%E8%87%AA%E7%94%B1%E5%8F%8A%E9%96%8B%E6%94%BE%E5%8E%9F%E5%A7%8B%E7%A2%BC%E8%BB%9F%E9%AB%94%E8%A8%B1%E5%8F%AF%E8%AD%89%E6%AF%94%E8%BC%83)”）。该页面对比了各种不同的软件许可协议。在【第二个】表格中，有一栏是“FSF 认可”——**凡是被 FSF 认可的，都可以算是【自由软件】许可证**；另外还有一栏是“OSI 认证”——**凡是被 OSI 认证的，都可以算是【开源软件】许可证**。

　　长期以来，很多商业公司对“自由软件”进行【污名化/妖魔化】。比如微软前任 CEO 巴尔默曾经污蔑说——Linux 以及相关的（GPL）许可证是“癌症”（以下是他原话）：

> Linux is a cancer that attaches itself in an intellectual property sense to everything it touches.  
> That's the way that the license works.

　　长期的妖魔化，让很多人【误以为】“自由软件与商业公司水火不容”。但其实不然！ 　　商业公司也能基于“自由软件许可协议”去开发“自由软件”并提供给用户。该过程可以是“免费的”，也可以是“付费的”。 　　所谓的“付费”，也就是说——商业公司也可以通过“销售自由软件”来获得利润（关于这点，下一条会详细介绍）。  
　　（注：为了打字省力，本文以下部分以 [FOSS](https://en.wikipedia.org/wiki/Free_and_open-source_software) 作为“自由软件 or 开源软件”的总称） 　　关于这个误解，俺把“自由软件”和“开源软件”分开来阐述。 　　在前一条，俺提到：（从理论上讲）商业公司也可以销售自由软件（拿自由软件卖钱）。

　　说到这，可能很多人还不信。下面俺给出 FSF（[自由软件基金会](https://zh.wikipedia.org/wiki/%E8%87%AA%E7%94%B1%E8%BD%AF%E4%BB%B6%E5%9F%BA%E9%87%91%E4%BC%9A)）【官网】的文章。

  
《[Selling Free Software](https://www.gnu.org/philosophy/selling.html)》（原文）  
《[销售自由软件](https://www.gnu.org/philosophy/selling.zh-cn.html)》（上述的中文翻译） 　　如果你理解了“为啥商业公司也允许销售自由软件”，也就比较能理解“为啥商业公司允许销售开源软件”了。

　　OSI（[开放源代码促进会](https://zh.wikipedia.org/wiki/%E5%BC%80%E6%94%BE%E6%BA%90%E4%BB%A3%E7%A0%81%E4%BF%83%E8%BF%9B%E4%BC%9A)）对“开源软件”的定义（前面已经提到），并【没有】对“销售或付费”做任何限制。

　　也就是说，如果你开发了一套“开源软件”，并拿去卖，并且有人愿意买。这个（销售/购买）行为并【不】违背 OSI 的精神和条款。  
　　不要以为俺在本章节提到的只是【理论上的可能性】。在现实生活中已经有商业公司（在遵守 FOSS 许可的前提下）利用自由软件盈利，甚至还上市了——这就是大名鼎鼎的【[红帽公司](https://zh.wikipedia.org/wiki/%E7%B4%85%E5%B8%BD%E5%85%AC%E5%8F%B8)】（洋文是：Red Hat）。该公司发布的“Red Hat Enterprise Linux”（简称 RHEL），在 Linux 社区很有影响。 　　关于“红帽公司”的规模，以下摘自维基百科的介绍：

> Red Hat于1999年8月11日在纳斯达克上市，2005年12月19日纳入纳斯达克100指数，2006年12月12日转到纽约证券交易所挂牌。  
> 2018年10月28日，IBM 将以每股190美元的现金收购 Red Hat 所有已发行股份，总价值约为340亿美元。

　　互联网时代之前和初期，情况确实如此。 　　但如今 FOSS（Free and Open-Source Software）已经改变了全球软件行业的生态环境。 　　举个例子：由于 Linux 内核已经被大量/广泛地适用于各个领域，很多【大型】商业会让自己的程序员参与 Linux 社区的开发；同时，这些程序员拿的是商业公司的工资。 　　虽然 FOSS（Free and Open-Source Software）允许用户获得源代码，允许用户自由地分发软件（包括源代码），但某些 FOSS 的 license 依然会有版权相关的条款（比如：有的会强调“署名权”，有的会强调“修改权”）。 　　引申阅读：

《[对版权的误解 @ FSF 官网](https://www.gnu.org/philosophy/misinterpreting-copyright.zh-cn.html)》

　　坦率地说，犯这种错误的人，既没有理解 FOSS（Free and Open-Source Software），也没有理解共产主义。 　　FOSS 与“共产主义”在本质上简直是【截然相反】滴。 　　前面俺已经说了：“开源软件”不光强调公开源码，而且强调【开放性】；相比之下，共产运动必将导致社会的【封闭性】。 　　为啥共产运动必将导致“封闭性”？

　　有耐心的同学可以去看[卡尔·波普尔](https://zh.wikipedia.org/wiki/%E5%8D%A1%E5%B0%94%C2%B7%E6%B3%A2%E6%99%AE%E5%B0%94)的代表作《[开放社会及其敌人](https://docs.google.com/document/d/1W3zcBUg55Mk5Vhzz3ajelXGh1YoOAxX8zzQvd9LniIs/)》（提醒一下：这是大部头的政治理论著作）

　　前面俺还说了：“自由软件”尽可能确保用户的【自由】；相比之下，共产运动必将导致对自由的【剥夺】（奴役）。 　　为啥共产运动必将导致“对自由的剥夺和奴役”？

　　对此感兴趣的同学可以去看一下[弗里德里希·哈耶克](https://zh.wikipedia.org/wiki/%E5%BC%97%E9%87%8C%E5%BE%B7%E9%87%8C%E5%B8%8C%C2%B7%E5%93%88%E8%80%B6%E5%85%8B)的代表作《[通往奴役之路](https://docs.google.com/document/d/1mmLgc9udwofBGrGD2DHqVq3pZZcaDDqTiw_8EN20wFs/)》。

  
　　批判“共产主义”和“马列主义”的博文，俺已经写过很多。具体参见博客上的 [政治.共产运动](https://program-think.blogspot.com/search/label/%E6%94%BF%E6%B2%BB.%E5%85%B1%E4%BA%A7%E8%BF%90%E5%8A%A8) 标签。 　　在20年前，很多人持有这种观点。如今越来越多的人开始意识到——FOSS 也可以打造出非常优秀的软件。 　　比如说大伙儿平时都在用的浏览器。IE 是完全闭源的商业软件，如今远远比不上 Chrome 和 Firefox。Firefox 是正宗的开源软件；Chrome 虽然不是开源软件，但它是在开源软件 Chromium 的基础上二次开发而成。 　　再比如 Web 服务器软件，长期占据三甲的，有两个（Apache、Nginx）是 FOSS，一个是闭源的（IIS）。而且 Apache + Nginx 的市场份额会明显高于 IIS。 　　（类似的例子还能举出很多） 　　另外，还有很多优秀的闭源商业软件在其内部使用了开源的库（library）。这些商业软件的成功，其内部使用的开源库功不可没。 　　引申阅读：

俺整理的“[C/C++/Python 开源库清单](https://github.com/programthink/opensource)”

  
　　（注：GPL 的全称是“GNU General Public License”，维基百科链接在“[这里](https://en.wikipedia.org/wiki/GNU_General_Public_License)”） 　　这个错误连某些 FOSS 社区的人都会犯。 　　“使用 GPL 协议”的软件，必定是“自由软件”；但反过来就【不】成立。换句话说，除了 GPL 协议，还有很多其它协议，也可以确保其所属的软件是“自由软件”。

　　刚才提到了维基百科上有一个 license 对比清单，再次丢出来给列位看官参考（链接在“[这里](https://zh.wikipedia.org/wiki/%E8%87%AA%E7%94%B1%E5%8F%8A%E9%96%8B%E6%94%BE%E5%8E%9F%E5%A7%8B%E7%A2%BC%E8%BB%9F%E9%AB%94%E8%A8%B1%E5%8F%AF%E8%AD%89%E6%AF%94%E8%BC%83)”）。清单中（第2个表格）有很多【非】GPL 的协议，也得到了 FSF 的认可（可以算是“自由的协议”）

　　这条与前一条有点类似，也属于——连 FOSS 社区的人都会犯的错误。 　　“兼容 GPL 的协议”，其所属的软件必定是“自由软件”；但反过来就【不】成立。换句话说，还有很多【自由软件】的许可协议，与 GPL 是【不】兼容滴！

　　在 FSF（[自由软件基金会](https://zh.wikipedia.org/wiki/%E8%87%AA%E7%94%B1%E8%BD%AF%E4%BB%B6%E5%9F%BA%E9%87%91%E4%BC%9A)）官网上有一个清单（链接在“[这里](https://www.gnu.org/licenses/license-list.html)”），对各种许可协议进行分类，其中有一类是【GPL-Incompatible Free Software Licenses】。这一类协议，数量还不少。

　　首先要承认一下：有段时间，俺也犯了这个错误。

　　如今要澄清的是：绝大部分“自由软件许可证”同时也算是“开源软件许可证”。**但有少数【例外】**。

　　举个例子（例外）：[WTFPL](https://zh.wikipedia.org/wiki/WTFPL)

　　有一个比较鲜为人知的 license 叫做“WTFPL”，洋文全称是“Do What The Fuck You Want To Public License”。中文翻译成“你他妈的想干嘛就干嘛公共许可证”。

　　猛一看这名称，可能很多人以为这是个“恶搞的协议”（恶作剧）。但这个协议还是有点来头滴，其 2.0 版本的作者 [Sam Hocevar](https://en.wikipedia.org/wiki/Sam_Hocevar) 曾经担任过 Debian 社区的负责人。

　　这个协议就属于刚才提到的【极少数例外】——它获得了 FSF 的认可，但没有获得 OSI 的认证。 　　俺写的这篇，难免会有遗漏。欢迎大伙儿补充 FOSS 相关的其它误解。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[如何选择开源项目？](https://program-think.blogspot.com/2009/02/how-to-choose-opensource-project.html)》  
《[GitHub 通告：整理了一个 C 和 C++ 开源库的清单（含示例代码）](https://program-think.blogspot.com/2015/06/GitHub-C-Cpp-Open-Source-Libraries.html)》  
《[为啥俺推荐 Python\[5\]：作为瑞士军刀的 Python——顺便分享俺整理的 Python 开源库](https://program-think.blogspot.com/2013/02/why-choose-python-5-tools.html)》

