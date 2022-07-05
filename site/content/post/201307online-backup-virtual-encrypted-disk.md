---
layout: default
title: '文件备份技巧&#65306;组合&#8220;虚拟加密盘&#8221;与&#8220;网盘&#8221;'
date: None
author:
    display_name: 
---

　　今天要聊的招数，其实在前不久（2013年3月）的博文《[Google Reader 之死——原因分析、应对措施、教训](https://program-think.blogspot.com/2013/03/google-reader-dead.html)》中已经稍微提到过了。当时俺承诺说：抽空单独写一篇介绍，所以就有了今天这篇博文。  
　　在进入正题之前，先稍微做一下名词解释。“网盘”就不用解释了吧？大伙儿应该都明白。“加密盘”这个概念，技术菜鸟可能没听过，俺稍微解释一下。 　　磁盘加密有两种常见的类型：物理加密盘 和 虚拟加密盘。下面分别介绍。 　　磁盘加密工具直接对你的某个分区（或整个硬盘）进行加密。加密之后，该分区（或硬盘）上存储的数据全部变成密文。即使有人盗取你的硬盘，也无法读取其中存储的数据。 　　加密工具先创建一个虚拟分区。这个虚拟分区其实对应于物理硬盘上的一个大文件（以下称“卷文件”）。你创建的虚拟分区有多大，这个“卷文件”就有多大。然后捏，加密工具可以挂载（Mount）该文件，挂载之后，你的系统会多出一个盘符。给你的感觉就好象多了一块硬盘（虚拟硬盘）。你存放到这个虚拟硬盘上的数据，都自动被加密。  
　　**“虚拟加密盘”的优点 和 “物理加密盘”的缺点** 　　主要就是便于备份。因为“虚拟加密盘”说白了就是一个大文件，你只要把这个大文件 copy 到其它地方，就相当于完成了虚拟盘的备份。 　　而“物理加密盘”要备份，就相对麻烦一些。你需要使用专门的磁盘备份工具（比如 Ghost）

　　**“物理加密盘”的优点 和 “虚拟加密盘”的缺点**

　　对于操作系统的系统分区，只能采用“物理加密盘”的方式，而无法采用“虚拟加密盘”的方式。  
　　所谓的“加密盘搭配网盘”，其实说来很简单，就是找一个**带同步功能**的网盘。然后把你本地的加密盘文件同步到网盘上（再啰嗦一下：是同步加密盘的“卷文件”本身，而不是加密盘里面的文件）。这么干有如下几个好处 　　这个好处是最明显的。因为你同步到网盘的是“加密盘文件”，别人很难偷窥你上传的数据。至少可以防止如下几种情况。

　　**1\. 防止网盘提供商偷窥**

　　大伙儿千万不要相信网盘提供商，美国的网盘提供商会被 NSA（美国国安局）偷窥，中国的网盘提供商会被朝廷偷窥（金盾工程）。

　　**2\. 防止上传过程的网络监视**

　　除了网盘提供商的风险，还有数据传输过程的风险。因为有些网盘在同步的时候，没有进行加密传输（比如某些国内网盘）。在这种情况下，一旦有人对你的网络传输流量进行监控（术语叫“嗅探”），就有可能拿到你同步的所有文件。

　　**3\. 防止网盘被入侵**

　　即使网盘帐号被盗，入侵者拿到的也只是加密盘——看不到你原始的数据。

　　不要以为网盘的密码复杂了，就不会被盗。有些时候不是你的密码出问题，而是网盘提供商出问题。即使是大名鼎鼎的 Dropbox 也曾经出现过严重的安全问题（[2011年，Dropbox曝出安全漏洞：任意密码均可登录](http://mi.itxinwen.com/2011/0621/298159.shtml)）

　　这个好处也很明显，因为你使用了网盘，提高了数据的“可用性”。即使你电脑的硬盘坏了、家中失火了、家中被盗了、遭遇地震了，都不用怕数据丢失。 　　有些同学看到这个小标题，可能会感到奇怪并反问——“网盘”不也属于云端吗？别着急，请听俺细细道来。 　　就拿2013年7月初刚刚关闭的 Google Reader 来说事儿。 　　俺的读者中有很多 GR 的重度用户，他们不光用 GR 来阅读博客，而且用 GR 来保存自己喜欢的文章——每当看到一篇好文章，就“加星”。也就是说，这些同学不光拿 GR 当阅读器，而且拿 GR 当资料库。一旦 GR 关闭，那可就麻烦啦！ 　　再来说说俺的做法。 　　俺也是 GR 的重度用户，但是俺不依赖 GR 的“加星”功能。每次看到一篇好文章，俺会把文章的内容（包括内嵌图片）都复制到本地的资料库。这个资料库存放在“虚拟加密盘”，然后俺把“虚拟加密盘”同步到某个网盘上。 　　这么做的主要好处是：你个人的数据还是放在本地而不是云端，网盘只是用来备份。所以 GR 关闭不影响俺收藏的文章。另外，即使俺用的网盘倒闭了，也只需要另外注册一个免费的网盘，然后重新同步一下加密盘。整个过程很简单，点几下鼠标就搞定了。  
　　在《[如何保护隐私\[1\]：关于软件和服务的选择](https://program-think.blogspot.com/2013/06/privacy-protection-1.html)》一文中，俺提到商业公司和非营利组织的差异，也提到“开源软件”与“闭源软件”的差异。那篇博文提到的原则也适用于磁盘加密工具的选型。比如早些年俺用的是 PGPdisk，2010年之前已经改用 TrueCrypt。因为 PGP 是商业公司（已经被 Symantec 收购），而 TrueCrypt 是开源组织维护的。 　　到目前为止，TrueCrypt 是最靠谱的磁盘加密工具。这玩意儿不光功能齐全，而且应用很广；当然最重要还是它的坚固性——据说美国 FBI 碰到嫌犯使用的 TrueCrypt 加密盘也束手无策。

　　关于 TrueCrypt，俺在2011年写过一篇介绍《[TrueCrypt——文件加密的法宝](https://program-think.blogspot.com/2011/05/recommend-truecrypt.html)》。没用过的同学，不妨先看看。

　　**补充说明**

　　本文写于2013年7月。而 TrueCrypt（以下简称 TC）这个开源项目已经在2014年死掉了 :( 　　不过别担心！ TC 的替代品 VeraCrypt（以下简称 VC）已经能完全兼容 TC 的功能和加密盘格式。另外，集成到 Linux 内核的 dm-crypt 也支持 TC 的加密格式。相关教程参见如下几篇博文：

《[扫盲 VeraCrypt——跨平台的 TrueCrypt 替代品](https://program-think.blogspot.com/2015/10/VeraCrypt.html)》

  
《[扫盲 dm-crypt——多功能 Linux 磁盘加密工具（兼容 TrueCrypt & VeraCrypt）](https://program-think.blogspot.com/2015/10/dm-crypt-cryptsetup.html)》  
　　显然，免费空间越大越好。这个无需多解释。

　　维基百科上有一个**网盘对比清单**（在“[这里](https://en.wikipedia.org/wiki/Comparison_of_online_backup_services)”），里面列出不同网盘的免费空间大小。

　　通常来说，提供网盘的公司，服务器速度都不会慢。但是天朝是一个奇葩的国家，GFW 把墙外的很多网盘都给封了。

　　如果你要用网盘来同步“加密盘”，考虑到加密盘都比较大（通常都是 GB 级别），你要么使用墙内的网盘，要么使用墙外**尚未被封**的网盘。

  
　　很多网盘都会限制单个文件的大小上限。详情请看上述[网盘对比清单](https://en.wikipedia.org/wiki/Comparison_of_online_backup_services)中的 "Maximum per-file size" 这一列。 　　使用本文的方案，你最好找一个文件大小无上限的网盘。

　　如果你使用的网盘有文件大小上限，并且该上限**小于**你的加密盘“卷文件”，那在同步之前还得先分割“卷文件”，太麻烦了（如何分割加密盘的卷文件，待会儿介绍）。

  
　　带同步功能的网盘，几乎都支持**文件级**的差异同步（只上传修改过的文件）。但很多都不支持“**字节级**”的差异同步。  
　　采用这种同步方式，网盘客户端会分析某个文件被修改的部分，然后只上传修改过的那些字节。这里面用到一种技术叫“差分编码”（洋文叫“Delta Encoding”），有兴趣的同学可以看维基百科“[这里](https://en.wikipedia.org/wiki/Delta_encoding)”的介绍。

　　对于本文介绍的招数，字节一级的差异同步很重要。刚才说了，“卷文件”通常比较大（GB 级别）。如果网盘客户端不支持“差分编码”，每次修改过加密盘里面的内容，就需要把**整个**“卷文件”上传，（时间和流量）太不划算啦。

　　在知名的网盘中，Dropbox 可能是最早实现“字节级差异同步”的。因为这玩意儿太技术化，很多网盘的介绍资料都没有提及。所以俺也不太清楚哪些网盘支持“字节级差异同步”，哪些网盘不支持。 　　如果你想知道自己使用的网盘是否支持，可以做个小测试。假如你手头已经有一个加密盘（至少是上百兆的），先把加密盘的“卷文件”同步到网盘。然后在加密盘中“修改某个小文件”或“增加某个小文件”。然后再把加密盘的卷文件同步一次。如果第二次同步很快完成，说明该网盘的客户端支持“字节级差异同步”。

　　有读者在留言中提出质疑，加密盘到底能不能使用“差分编码”。于是俺在《[TrueCrypt 使用经验\[1\]：关于加密算法和加密盘的类型](https://program-think.blogspot.com/2013/08/truecrypt-1.html)》一文中专门增加了一个章节——“磁盘加密的操作模式”，介绍大部分磁盘加密工具（包括 TrueCrypt）使用的磁盘操作模式（XTS 模式）。

  
　　（补充一下）某热心读者在留言中提醒，维基百科的[网盘对比清单](https://en.wikipedia.org/wiki/Comparison_of_online_backup_services)，里面有列举某些支持（字节级）差异同步的网盘。关注此功能的同学，请自行到该页面上搜索 **delta sync**  
　　几乎所有的磁盘加密工具，当挂载虚拟加密盘的时候，都会锁住加密盘对应的物理文件。“卷文件”一旦被锁住，就无法直接对其进行读写——包括网盘客户端也无法读写这个文件。

　　解决方法就是：**先“卸载”（Umount）加密盘，然后再同步**。换句话说：**挂载**加密盘的时候不要同步；加密盘**卸载**之后再同步。

　　比如你可以利用睡觉时间或吃饭时间，卸载加密盘，然后同步。 　　碰到这种情况，俺首先强烈建议换一个网盘。 　　如果你实在不想换网盘，可以考虑把加密盘分割之后再同步。但是这么干会比较麻烦，而且分割之后再同步有一个缺点：你需要占用两倍的本地硬盘空间。 　　分割文件的工具很好找，Google 上能搜到一大把。

　　对于 Windows 用户，名气比较大的是 [hjsplit](http://www.hjsplit.org/windows/)（这玩意儿支持的平台很多，连 DOS 都支持）。

　　对于 Linux 用户可以直接用命令行的 split 分割文件，用 cat 命令合并分割后的文件。 　　除了用专门的文件分割工具，还可以考虑用压缩工具进行分割（7Zip 和 WinRAR 都支持分文件压缩，类似于“文件分割”的功能）。

　　但是切记一点：**加密内容是难以压缩的**（稍微了解“密码学”和“信息论”的同学应该知道，加密之后的“熵”极大，再牛的压缩软件也压不下来）。所以，使用压缩工具对加密盘进行“分文件压缩”，一定要关闭压缩选项（对于 7zip，在“压缩等级”那个选项中选择“仅存储”）。

　　碰到这种情况，你有两个选择： 1. 换一个空间大的网盘 2. 申请多个网盘帐号，然后使用前面提到的“分割文件”的方案——把加密盘的“卷文件”分割成 N 块，分别同步到不同的网盘。 　　对于使用 Dropbox 的同学，很可能会碰到这种情况。Dropbox 有很多优点，而最明显的缺点就是空间小。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[文件加密的扫盲介绍](https://program-think.blogspot.com/2011/05/file-encryption-overview.html)》  
《[如何用“磁盘加密”对抗警方的【取证软件】和【刑讯逼供】，兼谈数据删除技巧](https://program-think.blogspot.com/2019/02/Use-Disk-Encryption-Anti-Computer-Forensics.html)》  
《[TrueCrypt 使用经验](https://program-think.blogspot.com/2011/05/recommend-truecrypt.html#index)》（系列）  
《[扫盲 VeraCrypt——跨平台的 TrueCrypt 替代品](https://program-think.blogspot.com/2015/10/VeraCrypt.html)》  
《[扫盲 dm-crypt——多功能 Linux 磁盘加密工具（兼容 TrueCrypt 和 VeraCrypt）](https://program-think.blogspot.com/2015/10/dm-crypt-cryptsetup.html)》  
《[扫盲 Linux 逻辑卷管理（LVM）——兼谈 RAID 以及“磁盘加密工具的整合”](https://program-think.blogspot.com/2020/06/Linux-Logical-Volume-Manager.html)》  
《[如何保护隐私](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)》（系列）
