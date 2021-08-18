---
layout: default
title: '学习技术的三部曲&#65306;WHAT&#12289;HOW&#12289;WHY'
date: None
author:
    display_name: 
---

　　最近几天有些网友在邮件里面问我关于学习的问题。有好几个人觉得工作了几年，也学会了不少的类库、框架、甚至语言，但是感觉自己的能力没有太大的提高。因此今天来说一下我个人对这方面的体会，希望对大伙儿（尤其是新手）有帮助。 　　先声明一下，本帖子讨论的三部曲是指你已经选定了某个技术方向之后，该如何学习；至于如何选定技术方向，则属于另一个话题，不在今天的讨论之列。 　　我把学习归类为三个步骤：What、How、Why。经过我对周围同事和朋友的观察，大部分感觉自己技术没有提高的人，都仅仅停留在 WHAT 阶段。下面我把这三个步骤解释一下。 　　所谓的“WHAT”也就是“What is it?”——这是最简单的层次。在这个层次，你要搞清楚某个东东是【什么】样子的？有【什么】用处？有【什么】特性？有【什么】语法？...... 　　举例如下：

> 对于学习语言（比如 C++、Java、Python），大部分人都能够掌握基本的语法和标准库，然后用它写一些小程序（诸如二分查找、冒泡排序、简单文件操作等）。  
> 对于学习类库（比如 JDBC 类库），大部分 Java 程序员都能明白 JDBC 主要包含哪些类，也能够用 JDBC 进行简单的数据库查询和增删改操作。

　　由于这个步骤是最基本的，假如你连这都做不到（可能你的理解力不够好），也别在 IT 行业混了。 　　但是光会 What 是不够的。仅仅停留在这个步骤，导致了很多程序员【只知其然，不知其所以然】。这就是目前大部分开发人员的现状。 　　所谓的“HOW”就是“How to do?”。在这个层次，你要搞清楚某个东西，其内部是【如何】运作的？【如何】实现的？...... 　　举例如下：

> 假如你在学习 C++ 语言，你是否搞明白函数传参数的实现机制？虚函数是如何实现？抛出异常时的栈回退是怎么回事？...... 假如你在学习 Java 语言，你是否搞清楚 GC 如何实现？反射是如何实现？......
> 
> 假如你在学习 JDBC 库，你是否清楚 JDBC Driver 的4种类型？不同游标类型的实现机制？事务的机制？......

　　在这个阶段，你必须多想想类似这些问题。然后通过各种途径（参见“[关于自学能力](https://program-think.blogspot.com/2009/01/2.html)”的几个方法），把问题彻底搞清楚。自然而然，你的提高就会比较明显。而且如果碰到一些深层次的问题（比如性能优化），也就知道该如何去解决。  
　　完成这个阶段之后，你基本上就属于该技术领域最优秀的20%的人（根据[二八原理](https://program-think.blogspot.com/2009/02/80-20-principle-0-overview.html)，80%的人不会去思考 HOW 的问题）。 　　一般来说，只有想清楚 HOW 之后，才能继续去考虑 WHY。 　　所谓的“WHY”，就是搞清楚某个东西【为什么】设计成这样？【为什么】不是另外的样子？这样的设计有什么讲究？...... 　　说实在的，善于问“为什么”有一定的天赋成分？好像某个科学大牛曾经说过“提出问题有时候比解决问题更难”。一般来说，只有当你【深刻理解】了某个东西，才能够针对这个东东的【设计】问出一些问题。所以，我前面强调过，要先把 HOW 的问题搞清楚，再来考虑 WHY 的问题。 　　举例如下：

> 对于C++语言：为什么 C++ 没有类似 Java 的 finally 关键字？为什么当初发明 C++ 的时候没有考虑 GC？...... 对于Java语言：为什么 Java 没有类似 C++ 的类析构函数？为什么 Java 要同时提供 String 和 StringBuffer 两个似乎冗余的类？......
> 
> 对于Python语言：为什么 Python 不提供类似 C++/Java 的访问控制机制？......

　　如果你能够【自己】问出诸如上述的“为什么”问题，并且能够通过各种途径找到解答，那你基本上已经吃透这个技术了，并且你已经【有可能】自己去【设计】一个类似的玩意儿了。到这时，你已经踏上了通向技术高手的康庄大道。 　　由于本博客偏重 IT 方面，所以今天举的这些例子多半都是 IT 相关的。但这个“三部曲”在 IT 之外的行业和领域，其实也适用。如何举一反三，就看各位的悟性了。  
　　写完本文3年之后（2012），俺又写了一篇《[用提问来促进思维——兼谈【非】技术领域的 WHAT HOW WHY 三部曲](https://program-think.blogspot.com/2012/03/think-what-how-why.html)》，谈“IT 之外的行业和领域”，如何运用这三部曲。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[用提问来促进思维——兼谈【非】技术领域的 WHAT HOW WHY 三部曲](https://program-think.blogspot.com/2012/03/think-what-how-why.html)》  
《[如何【系统性学习】——从“媒介形态”聊到“DIKW 模型”](https://program-think.blogspot.com/2019/10/Systematic-Learning.html)》  
《[如何完善自己的知识结构](https://program-think.blogspot.com/2013/09/knowledge-structure.html)》  
《[书评：＜你的灯亮着吗？——找到问题的真正所在＞](https://program-think.blogspot.com/2009/07/book-review-are-your-lights-on.html)》  
《[为什么独立思考这么难？——谈谈心理学的成因，并分享俺的经验](https://program-think.blogspot.com/2019/03/Why-Thinking-Hard-So-Hard.html)》  
《[批判性思维扫盲：学会区分“事实”与“观点”](https://program-think.blogspot.com/2013/05/difference-between-fact-and-opinion.html)》  
《[思维的误区：幸存者偏见——顺便推荐巴菲特最著名的演讲](https://program-think.blogspot.com/2015/05/Survivorship-Bias.html)》  
《[思维的误区：忽视沉默的大多数](https://program-think.blogspot.com/2010/07/silent-proof.html)》  
《[光环效应引发的认知误区](https://program-think.blogspot.com/2009/05/halo-effect.html)》  
《[学会透过现象看本质，即使现象有时候挺诡异](https://program-think.blogspot.com/2009/02/from-surface-to-essence.html)》

