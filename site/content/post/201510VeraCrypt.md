---
layout: default
title: '扫盲 VeraCrypt&#8212;&#8212;跨平台的 TrueCrypt 替代品'
date: None
author:
    display_name: 
---

　　这个长假前后出了不少新闻，除了“连环爆炸、TPP、诺贝尔医学奖”，还有一个信息安全方面的新闻——TrueCrypt 被发现存在高危的安全漏洞。这些新闻中，TPP 的影响最大，但不是很紧迫。所以俺先发一篇博文聊聊 TrueCrypt 的替代品（这事儿比较紧急）。  
  
　　当年（2014）TrueCrypt 死亡的时候，俺发过一篇《[分析一下 TrueCrypt 之死（自杀 or 他杀？），介绍一下应对措施](https://program-think.blogspot.com/2014/06/truecrypt-dead.html)》。当时俺提到：  

> 因为 TC 的源代码是公开的，任何人都可以拿它的代码克隆出一个新的磁盘加密工具。所以官网变脸之后，已经陆续出现了几个克隆（代码 fork）。假以时日，或许其中的某个克隆会再次成为主流。如果真这样的话，TC 就涅磐重生了。  
> 提醒一下：如果你对安全性的要求比较高，短期内（至少1年之内）不要急着去用这些克隆的 TrueCrypt（这些克隆需要一定的时间才能成熟、稳定）。

　　从“TrueCrypt 死亡”到现在已经过了大约一年半，再加上 TrueCrypt 又曝了高危安全漏洞。所以俺估摸着：是时候写一篇【扫盲教程】来介绍 TrueCrypt 的替代品了。  
　　这次的安全漏洞由 Google 的安全研究人员（James Forshaw）发现。共有2个漏洞（漏洞编号：CVE-2015-7358、CVE-2015-7359），影响的是 Windows 平台，Linux 和 Mac OS X【不受影响】。 　　（因为该漏洞只影响 Windows 平台，这说明该漏洞与“加密盘格式”【无关】）

　　对技术感兴趣的同学，可以到“[这里](https://code.google.com/p/google-security-research/issues/detail?id=538)”和“[这里](https://code.google.com/p/google-security-research/issues/detail?id=537)”看这2个漏洞的详细描述。

  
　　顺便表扬一下 Google 的安全研究团队，确实有两下子。之前大名鼎鼎的“[Heartbleed 漏洞](https://program-think.blogspot.com/2014/04/openssl-heartbleed.html)”也是 Google 安全研究团队曝光的。 　　俺选择 Blogspot 作为博客平台，就是考虑到 Google 在安全方面的实力； 　　与之对比，WordPress 虽然功能很牛，市场份额排名第一，但是经常曝出安全漏洞，不适合俺这种政治危险分子。  

![不见图 请翻墙](https://lh6.googleusercontent.com/VILcwWDdxVVlCVyVdRDVs_W3B-pPkkmPINa8BCA4DXfKyX24uZhBxRaLpYKsVD-OpppzectxcG_bdYf7t9v-qWq9MrlxArRn76sX3nFE9cA0UHdEo6IZzJ4jfOIZ8L2rlHRLQVhKQg)

  
　　VeraCrypt 是从 TrueCrypt 派生出来的开源项目，成立于2013年6月。其官网在 [https://www.veracrypt.fr/](https://www.veracrypt.fr/) 　　它刚成立那会儿，TrueCrypt 尚未死亡，所以 VeraCrypt 没有吸引太多的注意力。TrueCrypt 死亡之后，VeraCrypt 的使用量开始多起来。 　　此次曝光了高危漏洞之后，VeraCrypt 很快就在8天之后（9月26日）发布了 1.15 版本，修复了该漏洞。此举令其曝光率大增。 　　俺之所以首先推荐 VeraCrypt，除了此次修复漏洞及时，还有一个原因——其它替代品要么质量不如 VeraCrypt 成熟，要么功能不如 VeraCrypt 完备。

　　比如另一个名气比较大的替代品是 [CipherShed](https://en.wikipedia.org/wiki/CipherShed)，目前还停留在“Pre-Alpha”阶段——也就是说，连“Beta 品质”都没有达到。

  
　　建议直接从[官网下载](https://veracrypt.codeplex.com/)，【不要】从其它第三方的软件网站下载（大伙儿要吸取“[XcodeGhost 事件](https://zh.wikipedia.org/wiki/XcodeGhost%E9%A3%8E%E6%B3%A2)”的教训）。 　　目前 VeraCrypt 支持三大桌面操作系统，具体如下： Windows（WinXP 或之后的版本，包括新出的 Windows 10） Linux（内核主版本号大于等于 2.6） Mac OS X（版本号大于等于 10.6）

　　对于 Windows 用户，下载的 exe 安装包自带数字签名（如何校验数字签名，请看[这篇博文](https://program-think.blogspot.com/2013/02/file-integrity-check.html)）。另外，其官网还附上了不同平台安装包的“SHA 散列校验值”和“PGP 签名”。如果你下载的是 Linux 或 Mac OS X 的安装包，下载完之后，也请校验一下，以防万一。

  
　　（考虑到大部分读者是 Windows 用户，为了节省口水，**本文后续章节只聊 Windows 下的 VeraCrypt。使用其它平台的同学，请依样画葫芦**） 　　安装前，先确保当前用户具有“管理员权限”。 　　双击下载好的安装包（就是那个 exe 文件），然后一路点 next 就可以了。 　　下面开始聊功能，这是本文的重点，看仔细喽。 　　前面说了，VeraCrypt 是从 TrueCrypt 衍生出来的。所以其功能与 TrueCrypt 非常类似。关于 TrueCrypt 的功能介绍，俺已经写过一系列的傻瓜教程，包括如下：

《[TrueCrypt——文件加密的法宝](https://program-think.blogspot.com/2011/05/recommend-truecrypt.html)》

  
《[TrueCrypt 使用经验\[1\]：关于加密算法和加密盘的类型](https://program-think.blogspot.com/2013/08/truecrypt-1.html)》  
《[TrueCrypt 使用经验\[2\]：关于加密盘的密码认证和 KeyFiles 认证](https://program-think.blogspot.com/2013/08/truecrypt-2.html)》  
《[TrueCrypt 使用经验\[3\]：关于加密盘的破解和防范措施](https://program-think.blogspot.com/2013/08/truecrypt-3.html)》  
《[TrueCrypt 使用经验\[4\]：关于隐藏卷的使用和注意事项](https://program-think.blogspot.com/2013/10/truecrypt-4.html)》

　　（**如果你之前【没有】使用过 TrueCrypt，强烈建议你先看完上述这几篇扫盲教程**）

　　为了打字省力，那些与 TrueCrypt 类似的功能，俺就【不】介绍了。下面俺只聊 VeraCrypt 的【新增功能】。 　　考虑到某些网友是洋文菜鸟，先说一下如何配置界面的语言。 　　如果你打开 VeraCrypt 之后，界面是英文，先到主菜单中点击“Settings”，然后再点击“Language”菜单项，就会弹出一个选择语言的对话框，你把列表框的滚动条拉到底部，就会看到“简体中文”和“繁體中文”。具体截图如下：

![不见图 请翻墙](https://lh6.googleusercontent.com/y7cF9avhexDGngDSVILoCR9QQ2PUZbjZIAVkEW48KupIJRYTN2tSnghFlbzPvGew7Q-OF_4uRePy3aDd7AvYPxB3ikTzN0LYCIdWSuQlV_U7mRqvbcYmAwkmcgr00895fWFSKWQGCg)

（之所以出现2个“繁體中文”，是分别对应“港/台”）

　　选完中文之后，界面变为如下：

![不见图 请翻墙](https://lh3.googleusercontent.com/FABE5dOfVuRa5e2DJiprEy3zHROK230JBlxmnZ3H9rlFvp01ivxnInss7Sn9wTJNprSqBNepdz73zCXbaasiCbEUmVsyTKe8IpBgbgtVxFo-5l4f_thloBQJU6fc1hTTk3SOjRrFNQ)

　　VeraCrypt 支持两种加密盘的格式，其中一种就是原先 TrueCrypt 使用的格式，另一种是 VeraCrypt 自己新创的格式。因此，如果你手头有原先 TrueCrypt 创建的加密盘，也可以用 VeraCrypt 直接挂载（mount）。 　　这两种格式的【唯一差异】在于——VeraCrypt 的新格式支持 PIM 功能（关于此功能，待会儿介绍）。 　　为了防止混淆，再唠叨一下关于加密盘的类型（“类型”与“格式”是两个概念，别混淆了）。 　　TrueCrypt 支持两种类型的加密盘——物理加密盘（加密分区、全盘加密）和虚拟加密盘（卷文件）；VeraCrypt 也支持这两种类型。 　　所以，排列组合之后，VeraCrypt 共支持如下4种： 旧格式（TrueCrypt 格式）的虚拟加密盘 旧格式（TrueCrypt 格式）的物理加密盘 新格式（VeraCrypt 格式）的虚拟加密盘 新格式（VeraCrypt 格式）的物理加密盘 　　当你使用旧格式（TrueCrypt 格式）的加密盘，其操作方式与原先的 TrueCrypt 基本一样。 　　当你使用新格式（VeraCrypt 格式）的加密盘，你可以配置 PIM 参数，也可以不配置（此时用的是默认值）。这个 PIM 参数有助于提升加密盘的安全性——主要是对抗“暴力破解”（本文后续章节会专门聊 PIM 功能）。 　　这方面，VeraCrypt 与 TrueCrypt 大同小异——加密算法一样，散列算法多了一个 SHA-256。

　　更详细的介绍，请大伙儿自行翻阅前些年的博文《[TrueCrypt 使用经验\[1\]：关于加密算法和加密盘的类型](https://program-think.blogspot.com/2013/08/truecrypt-1.html)》，俺就不浪费口水了。

  
　　TrueCrypt 原先支持两种认证方式：“密码 ＆ keyfiles”。这两种方式，VeraCrypt 也都支持。相关的介绍，请大伙儿自行翻阅前些年的博文《[TrueCrypt 使用经验\[2\]：关于加密盘的密码认证和 KeyFiles 认证](https://program-think.blogspot.com/2013/08/truecrypt-2.html)》，俺就不浪费口水了。 　　另外，VeraCrypt 还新增了一个 PIM 功能。从某种意义上讲，PIM 也可以算是一种认证方式（因为挂载加密盘到时候也需要它）。关于 PIM 功能，本文下面专门用一个章节来详述。 　　跟 TrueCrypt 类似，会出现一个“向导界面”，引导你一步步完成加密盘的创建。开头几步跟 TrueCrypt 类似，俺就不贴图了。 　　到最后一步，稍微有点不同，俺来聊一下。 　　以下是向导最后一步的界面，此时你选好文件系统格式之后，直接点击“格式化”按钮。

![不见图 请翻墙](https://lh4.googleusercontent.com/qj1rY_MELtSWPG-AwWgSRRAuvUfOSTUDq_XCve4aV9lUbq6BS4aq0jC7_gZNTWW0-XyGjeyXc4cTkwkJppYVsorHMGyeyzeSXSNnHbEbl7QGIyCU2OrSWunghAFtbfgycAoD3CRD8A)

　　点击之后，你会发现进度条没有动静。因为 VeraCrypt 需要收集到足够多的随机信息，用来创建相关的加密密钥。 　　此时，你必须在当前这个窗口内，频繁并迅速地移动鼠标（随机移动）。大约四分之一柱香的功夫，就会出现进度条。

![不见图 请翻墙](https://lh3.googleusercontent.com/e_MdtZaYbzMhwOAEnY5cgyj7Pd9bmZYry3HR1bhVZ7v8hIjVyRIfgMQxnh1QLYAqCzbza3toiKc4im2R9Kc2HqYPo-Rc2A4gp0aUFG8MnB7ngfCem-QShyBBQMk3iB9nVHgOkQv6eQ)

　　出现进度条，说明已经开始格式化。格式化完成后，会提示你。

![不见图 请翻墙](https://lh3.googleusercontent.com/h0SgjYN7nJBJpo7HPBREyxcfqMyLachIZsywJpKHolhTez0KZb39DJyLJ5lAhNWo-MRpmWjrqDu6KLNzA81tkBdfyx42-XOGaw4tBf49c188_OFhY2xdQAqaC27YAKNBPhuwfsh85w)

　　挂载加密盘的界面，跟 TrueCrypt 有点小区别——多了两个复选框。 　　其中一个复选框是“TrueCrypt Mode”——勾选它是为了挂载旧格式（TrueCrypt 格式）的加密盘。

![不见图 请翻墙](https://lh5.googleusercontent.com/x4XLr8XXOSK-DfTWRE2RlhAXKytd8ppKNI1HNVunQQUzQf579V2HFUVecovs0eTOEhHdbJnuYzbpEwMhPjKUmo9JH_d8u0ijAAXtlnutWGhKXgPhw7Zp9MeencZimYgGkBS-EUX5pQ)

  

![不见图 请翻墙](https://lh6.googleusercontent.com/Q9YSw8LrGpYI3O-GOtHWjoirQLpwW-hVYpfbMDAAesgZG0VhXAxrFfcZWLFrmb2HBBLQqUkDULpzRZKVdrFHdLzB1X-Bz_hFWiafBV24wAnxEKykx5tYL5DBB39xvlDzreCUwcF91Q)

　　另一个复选框是“Use PIM”——这个复选框的作用，留到后面的章节介绍。 　　提醒一下： 　　VeraCrypt 挂载【新格式】加密盘的时候，你会明显感觉很慢。主要是因为 VeraCrypt 强化了安全性（具体的技术细节后面会提及）。 　　VeraCrypt 不但可以打开旧格式（TrueCrypt 格式）的加密盘，而且可以把旧格式转化为新格式（VeraCrypt 格式）。 　　转换过程很简单——通过修改认证信息来进行。 　　也就是说：当你修改了某个旧格式加密盘的密码或者 keyfiles，修改成功之后，该加密盘就变为新格式了。

　　提醒：**该转换是【不可逆】的。也就是说，你无法用 VeraCrypt 把新格式转为旧格式。**

　　现在开始讲 PIM——这是 VeraCrypt 新增的功能，因此俺就多费点口水。 　　所谓的 PIM 是洋文“Personal Iterations Multiplier”的缩写。通俗地说就是：你可以自定义“加密盘的头部密钥生成时的迭代次数”。这句话比较绕口，要想解释清楚，需要聊相关的技术实现机制（如下）。 　　（对技术细节【不】感兴趣的同学，就不用看俺的解释了。直接跳到下一节“VeraCrypt 相对 TrueCrypt 的改进”）

　　**加密盘格式简介**

　　不论是新格式还是老格式，加密盘的数据大致可以分为两部分：“头部”和“数据区”。 　　所谓的“数据区”，存放的就是加密盘中文件系统的数据（通俗地说，就是你放到加密盘中的文件和目录的信息） 　　所谓的“头部”（header），存放的是加密盘本身的一些信息。刚才提到的“数据区”，其加密的密钥叫“Master Key”（也叫“主密钥、数据区密钥”），这个“Master Key”就是存储在加密盘头部的。此外，像“加密盘格式的版本号”、“是否有隐藏卷”等信息，也是存储在头部的。

　　**“Header Key”的生成机制**

　　头部包含了很多加密盘的关键信息，自然也是要加密的。那么加密头部的密钥从哪里来捏？这个“Header Key”（也叫“首密钥、头部密钥”）是根据你输入的认证信息，来生成的（提醒一下，认证信息有2种：密码 和 keyfile）。

　　VeraCrypt 采用“PBKDF2 算法”来生成“Header Key”（该算法的具体描述参见“[这里](https://en.wikipedia.org/wiki/PBKDF2)”）。

　　在生成“Header Key”的过程中，会采用你指定的散列算法进行 N 次迭代，以生成一个难以猜测的密钥。这个 N 就是前面所说的“迭代次数”。 　　每当用户要挂载某个加密盘，软件界面会提示用户输入“密码和 keyfile”。然后根据用户的输入，计算出“Header Key”，然后用这个密钥对加密的头部进行解密（解到内存中）。如果解密成功，就说明用户输入的是对的。反之，则提示用户输入错误。

　　**为啥要“迭代 N 次”？**

　　从上述可以看出：这个“迭代次数”越大，计算头部密钥的时间就越长，因此挂载加密盘的过程就越慢；表面上看，这是一个缺点。但其好处在于：如果某个攻击者想要采用暴力破解的方式对“头部”进行穷举解密，每次一次尝试也需要花很长时间（同样要迭代 N 次）。所以，当 N 足够大，暴力破解就变得【不可行】。

　　**“Header Key”与“Master Key”分离的好处**

　　从上述可以看出，加密盘中存在两种密钥：“Header Key ＆ Master Key”。为啥要搞出两种密钥捏？其中一个好处是为了方便用户修改密码。当用户修改加密盘的密码或 keyfile，只需要“重新加密头部”，数据区不用改动（因为“Master Key”【没有】发生变化）。 　　对于那些超大的加密盘（TB 级），这个好处非常明显。 　　如果你刚才没有看技术细节的解释，直接跳到这里，你只需记住如下结论： PIM 功能就是用来配置加密盘的某个“迭代次数”的。“迭代次数”越大，暴力破解就越难；同时，挂载加密盘也越慢。 　　对于原先的 TrueCrypt，它的迭代次数是写死在程序代码中的。而且 TrueCrypt 使用的迭代次数偏小（这是 TrueCrypt 被批评的主要问题之一）。 　　到了开发 VeraCrypt 的时候，其开发团队把原先默认的迭代次数调大（大约增加了两到三个数量级）。迭代次数调大之后，就显著增加了“暴力破解”的难度。 　　此外，从 VeraCrypt 1.12 版本开始，在界面上提供了一个功能，允许用户自定义每个加密盘的“迭代次数”——这就是下面要讲的“PIM 的用户界面”。 　　VeraCrypt 提供了相关的用户界面，让你可以自定义 PIM 数值的大小。前面说了，PIM 越大，暴力破解越难；但同时，挂载加密盘也越慢。由于不同的用户有不同的需求，所以，VeraCrypt 干脆提供一个界面让你自己设定 PIM 的大小。当然，如果你懒得设置，也可以直接用内置的默认值。

　　**创建加密盘时**

　　VeraCrypt 同样提供了“创建加密盘的向导”。该向导前面5步跟 TrueCrypt 是一样的，俺就略过不提。 　　下面是创建加密盘的向导界面第6步。如果你想使用 PIM 功能，需要勾选“Use PIM”这个复选框。

![不见图 请翻墙](https://lh3.googleusercontent.com/A1dpt4OujJiZP6cBHmndcMgbkaykY66CPRb_AI5W2ILjrqrYQDGcN-uYlNGbpsIahElT9uKctdvVtl90Tr4tU5OFYTnA5fs-Hi2wHiX01mzUKuiC50Fr31GFZ-T4OHtbuqO0JwJNmA)

　　下面是创建加密盘的向导界面第7步

　　如果第6步勾选了“Use PIM”，下一步就会让你输入 PIM 数值。**这个数值要牢记，其重要性等同于认证信息（密码 和 keyfile）。**

　　（如果输入 0 或者不填写，则表示——使用默认的 PIM 数值）

![不见图 请翻墙](https://lh4.googleusercontent.com/SJVjTH7R73LcONTOQ-b4V684jT6heB4ueNSsBvModz8mW-AL26ICrXaC-A75QjwN9tcO6Yu83O4haMYq4n2LGp2bWTDJXB2pvi648x-4PWHIkhDaEoC-5YtY2_SgmVqcKmU6MeSCuA)

　　如果你设置的密码过于简短，那么 VeraCrypt 会强制让你输入一个比较大的 PIM 数值（大于 485）。

![不见图 请翻墙](https://lh6.googleusercontent.com/N1WiiQtMASwjArURp8d1HZfKBeN9HqePrwLTc-QZp1yvWW5MYNLbjW2o-dfu4SMDN1VTwjLhQCwkztEWt-1y5Iixj5GG3wIQG_xsRNggp_5xB7-d6AAmbfoWzbJxwHTD-bZIxAzy6Q)

  
　　**挂载加密盘时**  
　　下面是挂载加密盘的界面。如果你创建加密盘的时候，指定了 PIM 数值，那么在挂载的时候，需要输入【相同的】PIM 数值。**如果输入的数值与创建时指定的 PIM 数值不一致，则挂载失败。**  
　　再次罗嗦一下：**一旦你在创建加密盘时设置了“PIM 数值”，【千万别忘了】——忘记它的后果就如同忘记密码！**

![不见图 请翻墙](https://lh6.googleusercontent.com/GtnE1AM8HURqEsa1PCLXV54QtxL8g1EI1t9fxYp6rRREfmTy-FLMuEEeYox_-xf65SWOybKkMlYodwIlmYUWQMhhf4tZYDnIJ2cmXr3LwrL1vOfz4i3Rba14wA5B70j46HAQNhZfAA)

  

![不见图 请翻墙](https://lh5.googleusercontent.com/CgfQgzCnIShLTBqmcADRaw1G9fLOy7zKsKuiL0qnIY4JqLpbnFY-eKzR6vr4PdG1BYBP-zxtVLSikr0yVB7_MQrg6293Zl20wCFMK4DIujo8acWezLasbUuog8ilQouzCgWFEd4svg)

  
　　（如果你不关心技术细节，这个换算公式你可以不用看） 　　根据 VeraCrypt 的文档，PIM 根据如下公式换算成迭代次数。

1\. 对于“系统加密分区”：**迭代次数 = PIM x 2048**

  
2\. 对于“虚拟加密盘”或者“非系统加密分区”：**迭代次数 = 15000 + (PIM x 1000)** 　　另一个比较显著的新功能是“加密盘扩容”。原先的 TrueCrypt【没有】扩容功能——如果你的加密盘，空间不够了，你不得不重新创建一个更大的加密盘，然后把原先加密盘的文件拷贝到新加密盘（步骤繁琐）。

　　如今有了这个扩容功能，你可以直接扩大原有加密盘的容量。**前提是：文件系统必须是 NTFS。**

　　下面给出扩充操作的系列截图（共8张），描述文字都标注在截图中了。

![不见图 请翻墙](https://lh4.googleusercontent.com/XD1GpTBWJNlHD7M9f-f7vEe3zrzVoZzHi6muM0Chl66bRLKFKTHouMGmLaBaJuilXpBw4OBrhJaWutF_EfQwHfs01h0yA_bRb6GGOUg5xsOdOf9IW11OdAW9cALanzQb8s3fzeucrQ)

  

![不见图 请翻墙](https://lh4.googleusercontent.com/NKwNUc22fDNiJPtMQixLDfDuJ8fSCMhtZZgdNbcvvx01CVloqtPmuP5McVGQjw4Jbzk6NHOGdcwpXbNmb8FRZRMh337p4HypUzrT0e6ic9vVRjVHKNF6RSD4sk8HgP33EKRSZazc0A)

  

![不见图 请翻墙](https://lh6.googleusercontent.com/RMfuuXekJnW0CphWoqPMuAQYhT5DIRPgl1LEsgHIGAvK3l_ZMrpF5u05fbQjTFDcX01AuBdNQ8-gY6a32l8ZT9TvIGJXBCvE_ke97pNsc2bjyhjSCmKJ3JxoFXtt-vZcS-wh1dvVPA)

  

![不见图 请翻墙](https://lh6.googleusercontent.com/CR3Jb4Ylkl7TCgijbVmvKQ-gsUlM-QIYqpA11ifPMjU7ak-x0fgNql4aXjWU_2Gl1n-h80RgypgfxZqUnzmBE3VYDU2GI0lO_f5GaO6FwFi-uo5WKLP70SBHGgq8GqX9M_W0ghJEXQ)

  

![不见图 请翻墙](https://lh4.googleusercontent.com/s_a8pugEtYIx1WQuogiy6nqo6ciWbyyCc2czbEg6H7UviEixhF2ZWPsQba1AjXlFGRD0ZbvKrU5msTvRNXL0_IROvEasK80rkOzgubdOsALUX9q3JxiFN7o5jE2eMFDzvRK0seKXBA)

  

![不见图 请翻墙](https://lh4.googleusercontent.com/X-Aw3F_46w27YymAkFkqO1Wa8LIBLJod3dDLEo30jW3EVqrtQkV56lQ3Ysvmh5WYmXQAay-hlw25Nw7696Rp3ffmjBLM7NVTtmwrJYalUfy3cJcFtvsdDHokfICCA3RTZsiu9VStSQ)

  

![不见图 请翻墙](https://lh4.googleusercontent.com/4mQjtExfAfcHaBMdNUSFo-zfxh2_TwRy_IkDg1lr7jChYaGxePaIPKGzeHTT0EZtG3G1MFRNe2rQ2iWuVlVSfPGq7qB-5qUkkBKERSZg83QItX0g7VMIVCUNKsvnmIDoke6Dw2bZnw)

  

![不见图 请翻墙](https://lh4.googleusercontent.com/CrmnyBzbypS9DSzidnv31l55UoO12Esm87NFqoJflJWR2syGoYM3iEu0LquMt6cmOXPjRuiz5Jg5B-Q7tIRW14zg2NFu5Lh2o2MF5k1mZVoXnMRUPELDV1vAss9a9krLcqlHsGSEVA)

　　下面这篇博文，其实已经包含在本文开头列出的 TrueCrypt 教程中。

　　[TrueCrypt 使用经验\[3\]：关于加密盘的破解和防范措施](https://program-think.blogspot.com/2013/08/truecrypt-3.html)

  
　　因为这篇的内容比较重要，俺再次唠叨一下：**如果你对安全性的要求很高，一定要把上述这篇仔细看完。** 　　俺写这篇博文时，VeraCrypt 最新的是 1.16 版本。本文的截图就是根据这个版本制作的。 　　从截图中可以看出，某些界面还未彻底汉化。今后如果继续汉化，新版本的界面可能与本文的截图会略有不同。 　　另外，VeraCrypt 的开发比较活跃，今后多半还会增加新的功能。到时候俺会补充到这篇博文中。 　　大伙儿如果有啥疑问，欢迎到俺博客留言。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[TrueCrypt——文件加密的法宝](https://program-think.blogspot.com/2011/05/recommend-truecrypt.html)》  
《[TrueCrypt 使用经验\[1\]：关于加密算法和加密盘的类型](https://program-think.blogspot.com/2013/08/truecrypt-1.html)》  
《[TrueCrypt 使用经验\[2\]：关于加密盘的密码认证和 KeyFiles 认证](https://program-think.blogspot.com/2013/08/truecrypt-2.html)》  
《[TrueCrypt 使用经验\[3\]：关于加密盘的破解和防范措施](https://program-think.blogspot.com/2013/08/truecrypt-3.html)》  
《[TrueCrypt 使用经验\[4\]：关于隐藏卷的使用和注意事项](https://program-think.blogspot.com/2013/10/truecrypt-4.html)》  
《[分析一下 TrueCrypt 之死（自杀 or 他杀？）——兼谈应对措施](https://program-think.blogspot.com/2014/06/truecrypt-dead.html)》  
《[文件加密的扫盲介绍](https://program-think.blogspot.com/2011/05/file-encryption-overview.html)》  
《[文件备份技巧：组合“虚拟加密盘”与“网盘”](https://program-think.blogspot.com/2013/07/online-backup-virtual-encrypted-disk.html)》  
《[如何用“磁盘加密”对抗警方的【取证软件】和【刑讯逼供】，兼谈数据删除技巧](https://program-think.blogspot.com/2019/02/Use-Disk-Encryption-Anti-Computer-Forensics.html)》  
《[扫盲 dm-crypt——多功能 Linux 磁盘加密工具（兼容 TrueCrypt 和 VeraCrypt）](https://program-think.blogspot.com/2015/10/dm-crypt-cryptsetup.html)》  
《[扫盲 Linux 逻辑卷管理（LVM）——兼谈 RAID 以及“磁盘加密工具的整合”](https://program-think.blogspot.com/2020/06/Linux-Logical-Volume-Manager.html)》

