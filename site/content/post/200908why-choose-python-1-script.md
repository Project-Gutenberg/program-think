---
layout: default
title: '为什么俺推荐 Python[1]&#65306;作为脚本语言的 Python'
date: None
author:
    display_name: 
---

　　俺窃以为，Python 的所有特征中，作为**脚本语言**（“脚本语言”的定义参见“[这里](https://en.wikipedia.org/wiki/Scripting_language)”）是它的首要特征。因此，在本系列帖子中，俺首先来忽悠一下 Python 作为脚本语言，有些啥好处？ 　　要聊 Python 作为脚本语言的好处，首先得说说脚本语言自身有哪些优点。一般来说，当我们提及“脚本语言”，都是强调其解释执行的特性（虽然有些脚本语言也支持编译）。所以，后面陈述的这些优点，大都是拿编译型语言来进行对比。 　　大部分脚本语言都提供了（内置了）比较高层次的抽象和封装。像很多脚本语言都内置了字符串处理能力以及正则表达式（典型代表就是 Perl）。还有很多脚本语言都内置了高级的数据结构。比如 Python 在语言层面支持了链表（Python 的术语叫 List）、映射（Python 的术语叫 Dict）、元组（Python 的术语叫 Tuple）。 　　有了这些高层次的封装，你写起代码来，就特别滴简单、特别滴爽。比如，在 Python 中要把一个 List 翻倍，只需这么写：

\[1,2,3\] \* 2

就得到  

\[1,2,3,1,2,3\]

  
　　得益于高层次的封装，在完成相同功能的前提下，脚本语言的代码量会比编译型语言少很多。 　　比如说，要打印出某个文本文件的内容，如果用 Java 实现，正常的写法大概要七、八行代码（把所有代码硬挤到一行的，不予讨论）；用 Python 也就三、五行。 　　再比如说，抓取某个网址对应的 web 网页，用 Python 自带的标准库实现，大概3到5行代码；但如果用 C++ 实现，代码量会增加许多（具体要写多少代码，取决于你用了哪个 http 的库）。 　　代码量少了之后，至少你看代码的时候（无论是看自个儿滴还是看别人滴），能少敲很多次翻页键，大大延长了键盘的寿命，顺便降低了手指头的劳损。 　　当然啦，延长键盘寿命还不是关键，关键在于——代码量少了之后，（通常情况下）会有助于提高可读性。而可读性恰恰是 Python 的强项之一。 　　比方说：Python 在【语法层面】强制约定了作用域缩进（这是俺很喜欢 Python 的地方之一）。如此一来，即便是新手程序猿写出的 Python 代码，缩进风格也很统一。反观 C/C++/Java 的新手，写出的代码就没有这么整齐了。 　　通常，脚本语言的语法都比较简单、傻瓜化。因此，入门也就容易很多。稍微有一些编程基础的人，就能够在短时间内上手。 　　比如俺手下的 C++、Java 程序员，以及某些测试人员，都可以在一周内（程序员用不着一周，一般就1、2天）掌握 Python 的语法并用来写一些辅助的小工具。大大节约了俺培训的口水。 　　很多脚本语言的 IDE 支持【交互式写代码】。也就是说，你每写完一行代码，解释器就执行一把。这样能很快发现输入错误，而且还可以立即看到执行结果。 　　前面说了那么多优点，那脚本语言有啥缺点捏？ 　　主要的缺点就是【性能差】。这是他们为上述优点所付出的沉重代价。所幸当今的计算机硬件突飞猛进，性能差的缺点已经越来越不明显了。 　　有同学可能要问了，脚本语言有很多，为啥俺独独青睐 Python 捏？ 　　为了回答这个问题，下面俺拿 Python 和一些常见的脚本语言作一些【肤浅的】比较。 　　鉴于后面的内容极易引发语言的口水战，俺特此声明：虽然接下来会提及某些语言相对于 python 的缺点，但俺绝无贬低这些语言的企图，也无意证明 python 比这些语言优秀！俺只是陈述一下：当年是如何在几种脚本语言中进行取舍的？ 　　除了 Python 之外，常见的脚本语言还有很多，比如：PHP、JavaScript（以下简称 JS）、Perl、VBScript（以下简称 VBS）、Ruby、Bash、Lua、Tcl（可别误以为是某家电厂商）......Python 是如何从这些脚本语言中脱颖而出的捏？俺挑选的时候，主要考虑了如下几点： 　　因为俺懒得学太多编程语言。所以，俺希望熟悉一门脚本语言之后，能够尽量多帮俺搞定不同领域的事儿。从这点来看，俺就不会选择 PHP（太偏重于 Web 服务端）、JS（太偏重于 Web 客户端）、诸如 Bash 之类的 Shell 脚本（太偏重于系统管理）。 　　而 Python 则属于通用的脚本语言，覆盖范围很广。比如 Web 开发、桌面 GUI 应用、系统管理、网络应用、科学计算等许多领域，Python 都可以轻易搞定。  
　　关于“人气”的重要性，俺在《[如何选择开源项目](https://program-think.blogspot.com/2009/02/how-to-choose-opensource-project.html)》一文中，有介绍过。人气越高、越流行，就意味着更多的资源（包括文档、相关软件），当你碰到问题需要解决，也有更多的人可以咨询。  
　　关于编程语言的流行程度，可以大致参考 [TIOBE](http://www.tiobe.com/content/paperinfo/tpci/) 的排名（虽然 TIOBE 不能全面反映流行程度，但至少可作为某种参考）。  
　　像 Tcl、PowerShell、Groovy、JavaFX 等都排在３０名之外（截至写本文的2009年8月），感觉用的人太少了，俺暂时不予考虑。而 Python 最近几年的排名则一路上升（请看“[这里](http://www.tiobe.com/content/paperinfo/tpci/Python.html)”），截止到2009年8月，已经高踞排行榜第６位。Perl 虽然也身居高位，但是最近几年的排名一路下滑（请看“[这里](http://www.tiobe.com/content/paperinfo/tpci/Perl.html)”）。俺个人认为，其人气不容乐观。  
　　另一个俺很看重的地方是功能是否够强大。在这点上，Python 和 Perl 都算是比较强悍的。关于 Python 如何强悍，俺会在本系列的第5篇帖子《[作为瑞士军刀的 Python](https://program-think.blogspot.com/2013/02/why-choose-python-5-tools.html)》中加以介绍。 　　反观 JS、Ruby、Tcl 等语言，则稍显不足（当然，也有可能俺孤陋寡闻）。 　　由于俺平时会使用不同的操作系统，再加上俺负责的产品也是跨平台的。所以，俺对脚本语言有跨平台的要求。说到跨平台，诸如VBS、Bash之流就不予考虑了。 　　其实，很多脚本语言都支持跨平台。而 Python 在这方面，更为出众。不光支持主流的操作系统，还支持一些冷门的（比如古老的 DOS），还支持手持设备（比如智能手机和平板）。  
　　最后这一点，估计大多数同学不会太关心。俺因为要在公司的产品中引入脚本技术，所以俺还得考虑该脚本语言和其它语言的整合能力。整合能力强的脚本语言，可以作为复杂系统中的胶水，用来把不同模块粘合在一起（关于 Glue Language，可以参见“[这里](https://en.wikipedia.org/wiki/Glue_language)”）。 　　在这方面，Python 和 Ruby 的表现都不错：

它们和 Java 的整合有[Jython](https://en.wikipedia.org/wiki/Jython)、[JRuby](https://en.wikipedia.org/wiki/JRuby)；

  
和 dotNet 平台的整合有[IronPython](https://en.wikipedia.org/wiki/IronPython)、[IronRuby](https://en.wikipedia.org/wiki/IronRuby)。  
至于俺常用的 C++，Python 整合得比 Ruby 好。比如 C++ 社区大名鼎鼎的 Boost 库里面，就内置了一个 Boost.Python 的子库（参见“[这里](http://www.boost.org/doc/libs/release/libs/python/doc)”）。 　　关于 Python 如何用作胶水，俺会在后续的帖子“作为胶合语言的 Python”中会详细介绍。 　　基于上述几个方面的考虑，俺最终选择了 Python 作为日常使用的脚本工具，并把它引入到公司的产品中，作为模块之间的胶合剂。

　　啰嗦完Python作为脚本语言的方方面面，[下一个帖子](https://program-think.blogspot.com/2009/08/why-choose-python-2-dynamic.html)，咱来聊一下它作为动态语言的那些事儿。

[回到本系列的目录](https://program-think.blogspot.com/2009/08/why-choose-python-0-overview.html#index)

