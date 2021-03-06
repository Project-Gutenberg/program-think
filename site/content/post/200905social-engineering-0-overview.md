---
layout: default
title: '扫盲&#8220;社会工程学&#8221;[0]&#65306;基本常识'
date: None
author:
    display_name: 
---

　　最近几年，信息安全方面的问题日益严重，许多同学深受其害（比如网络钓鱼、盗用银行卡、蠕虫木马泛滥、僵尸网络盛行等等）。俺窃以为，很大一部分原因在于相应的扫盲教育没有跟上。且不说普通的电脑菜鸟对信息安全一无所知，即便是很多 IT 公司的专业技术人员，对此也知之甚少。其后果就是：很多菜鸟级的攻击手法屡试不爽，很多平庸的攻击者屡屡得手。有鉴于此，俺打算抽空普及一下信息安全相关的东东，或许能对某些同学有所帮助。 　　其实信息安全方面的话题非常之多，俺经过左思右想之后，决定先拿社会工程学来扫盲一下。至于为啥先说它，后面会解释原因。 　　俺喜欢把信息安全分为【硬安全】和【软安全】两部分。所谓“硬安全”主要包括具体的 IT 安全技术（比如：防火墙、入侵检测、漏洞扫描、拒绝服务攻击、缓冲区溢出攻击 ......）；而“软安全”主要涉及管理、心理学、文化、人际交往等方面，与具体的 IT 技术无关。今天所说的社会工程学，实际上就是“软安全”的范畴。

　　通俗地说，社会工程就是：攻击者利用【**人**】自身的弱点（往往是心理学层面）来获取信息、影响他人，从而达到自己不可告人的目的。光这么说稍显简单，更详细的定义可以参见“[这里](https://en.wikipedia.org/wiki/Social_engineering_%28security%29)”。不懂洋文的同学可以看“[这里](https://zh.wikipedia.org/wiki/%E7%A4%BE%E4%BC%9A%E5%B7%A5%E7%A8%8B%E5%AD%A6)”。

　　开头已经提到了安全基础知识的普及度不够。那为啥俺要先介绍社会工程学捏？主要有如下几点原因： 　　首先，社会工程是信息安全中一个经常被忽视的偏僻角落。即便很多 IT 安全领域的从业人员，往往也缺少社会工程学的相关常识。比如很多人都知道什么是防火墙、杀毒软件，但却从来没有听说过“社会工程学”这个词。  
　　大部分的安全厂商都把注意力集中在“硬安全”方面（比如现在防火墙厂商、杀毒厂商多如牛毛），很少有安全厂商把社会工程挂在嘴边的。以此**相反**的是：现有的信息安全攻击，大都以“软安全”作为攻击者的突破口，只有一小部分是纯粹通过“硬安全”来进行的。（这又是一个[二八原理](https://program-think.blogspot.com/2009/02/80-20-principle-0-overview.html)的生动例子） 　　为啥攻击者喜欢从“软安全”层面进行突破捏？因为人性的弱点是很难在短时间内得到改善的（尤其是人多大公司、大机构，更是如此）。所以，“软安全”方面会遗留很多可以利用的漏洞，攻击者只要善于利用这些漏洞，就可以轻易侵入。 　　不过捏，光是鲜为人知、重视不足，还不至于让俺花这么多口水大力忽悠。还有另一个原因是：社会工程学的常识非常有用，而且它的用处不限于信息产业（几乎所有行业都用得着）。具体有些啥用处捏？

　　首先，了解起码的社会工程学常识能够让你对相关的攻击手法（具体参见“[这里](https://program-think.blogspot.com/2009/05/social-engineering-1-gather-information.html)”和“[这里](https://program-think.blogspot.com/2009/05/social-engineering-2-pretend.html)”）有**基本的**防范，不至于轻易上当。要知道，有很多人被攻击者利用了之后，自己还浑然不觉。

　　其次，如果你是公司的老板或者某个管理层的头头，你可以在自己的职权范围内进行相关的扫盲培训（后面的帖子会介绍如何防范）。

　　最后，假如你看完本系列后，发现自己在社会工程方面很有天赋，那或许可以考虑朝这个方向发展。比如搞个商业间谍之类的工作干干，没准也很有前途哦。不过捏，一旦将来被抓被关、被杀被剐，本博主是概不负责滴 **:-)**

　　如果你从来没有听说过社会工程学，仅仅想扫盲，那只需看本帖即可，后续的内容无需多看。

　　如果你希望对社会工程攻击能够有**基本的**防范，建议看看后续的“[攻击手法](https://program-think.blogspot.com/2009/05/social-engineering-1-gather-information.html)”、“如何防范”。

　　如果你对社会工程学这门学问很有兴趣，建议看完本系列所有帖子。 　　如果你已经是社会工程学的老手，请不吝赐教，本系列帖子您老就不用看了。  
　　本系列帖子【**不能**】帮你成为社会工程学的高手。如果你真想达到这个目标，请先【**确保**】自己有这方面的天赋，接着再通过《[欺骗的艺术](https://en.wikipedia.org/wiki/The_Art_of_Deception)》（[凯文·米特尼克](https://en.wikipedia.org/wiki/Kevin_Mitnick)所著）进行深造。 　　本系列帖子【不能】帮你化解【所有的】社会工程攻击。毕竟社会工程学的手法太多、涉及的面太广。有些新颖的手法，其设计之巧妙、用心之险恶，估计连俺都会入套。 为了方便阅读，把本系列帖子的目录整理如下（需翻墙）：

1\. [攻击手法之【信息收集】](https://program-think.blogspot.com/2009/05/social-engineering-1-gather-information.html)

  
2\. [攻击手法之【假冒身份】](https://program-think.blogspot.com/2009/05/social-engineering-2-pretend.html)  
3\. [攻击手法之【施加影响】](https://program-think.blogspot.com/2009/05/social-engineering-3-influence.html)  
4\. [【综合运用】举例](https://program-think.blogspot.com/2009/06/social-engineering-4-example.html)  
5\. [你该如何【防范】？](https://program-think.blogspot.com/2009/07/social-engineering-5-defend.html)  
6\. （未完待续）

