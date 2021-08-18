---
layout: default
title: '聊聊大伙儿&#65288;包括某些职业围棋手&#65289;对 AlphaGo 的误解'
date: None
author:
    display_name: 
---

　　最近2-3天的新闻，大伙儿想必也知道了——AlphaGo 基于【公平规则】对阵人类第一流的围棋手，已经先胜两局，而且都是完胜。 　　俺也算是一个围棋的业余爱好者，而且俺也比较关注 AI（人工智能）的发展，今天冒昧写一篇点评。

　　所谓的“冒昧”，因为这两方面都只是俺的爱好，而【不是】擅长。说得不对之处，欢迎大伙儿拍砖。

　　本来想先写一段背景介绍，让大伙儿稍微了解一下 Alpha Go（俗称“阿尔法狗”）的原理。后来发现知乎上有一篇现成的，写得挺详细，而且比较通俗易懂。链接如下：

[https://www.zhihu.com/question/39905662](https://www.zhihu.com/question/39905662)

（如果你不希望让知乎看到你是从俺博客跳转过去的，可以把这个网址复制，然后新开一个浏览器标签页，再粘贴到地址栏） 该问题下面有好几个回答，参见其中的《左右互搏，青出于蓝而胜于蓝？—阿尔法狗原理解析》 　　这篇文章通俗介绍了“深度卷积神经网络”、“蒙特卡洛搜索树/MCTS”、“通过强化学习自我进化”。这几项是 AlphaGO 战胜人类的法宝。  
　　很多人**误以为**：围棋程序【仅仅】依靠大量的历史对局来作为参考。一旦出现全新的下法就不知所措。 　　至少 AlphaGo 这两局的表现，表面这是一种误解。下面俺来聊一下。 　　实际上，李世石一开始也抱有这种错觉，所以第一局的开局，李世石采用了一个罕见的开局。据说在职业比赛中，从来没人用过这个开局（棋谱如下）。

![不见图 请翻墙](https://lh3.googleusercontent.com/pBXhMg2e-kFTdYaD-30ocFiwQY6APV6pwFBndazI-zjxwIHlQiCl29V0bg18Sm6DCoZZN8fmbn3lgDcEoh7-x3VGZERrCm2eQXTyf1XelIufobWNwzkmFtKoEjJtnc7SjHaNxnd2d0w)

　　李世石估计是想调戏一下电脑，看看电脑如何应对一个从来没出现过的开局 　　（请注意：首局是“猜先定黑白”，李世石猜中之后，主动选黑。如果是职业比赛，通常是选白。说明李世石想要主导布局） 　　但是 Alpha Go 对这个开局应对自如（以下是 AI 在后续几手的应对）。

![不见图 请翻墙](https://lh4.googleusercontent.com/7VjlkN_h2-yIFktMFKyEw241u1wBc6wqAwNwrOx7NvRJy1RMXoMy3-tk-RFlPMf7SGGcyrqVxUy22ohVDQP33VrP3BCeteCzIimAvSiOLMkz7Rq4VSVeGPHYzEZ-iWeORDS6uRsrOY4)

![不见图 请翻墙](https://lh4.googleusercontent.com/WDJP3ZxAM0kc-zP6Sdw-bqlgyNaziUE1uNLuCJvskJPQyvi0I26P9PyXawDZwr1D-dH65xxPSujnWTETQIig6gB6QLCs5loUsQFJ89koZxcTXc0LS8SI6x0C38zUrQPkeVot9lOmk5w)

　　职业棋手李喆的评价是（粗体是俺标注滴）：

> 白8挂角正常，黑9二间高夹最为激烈。**白10，这一手……非常出色。**  
> 通常情况下，在右上白8遭遇二间高夹的时候，**白10是“不存在”的一手，它不在任何定式之中**。面对黑9，白棋有诸多定式选择，却没有白10这一手。  
> 然而，我认为白10是好手。白10的好处在于使黑7变成效率低下的一手，虽然在右上局部白棋稍稍亏损，但加上黑7的低效，白棋一点也不吃亏。

　　还有一种常见的误解是：围棋程序不擅长布局。 　　为啥会有这种误解捏？确实在早期的围棋程序中，布局都比较烂。因为电脑擅长的是【计算】，而布局阶段凭的是【感觉】。“棋感”这种东西，是很难用程序来进行量化的。 　　但是 AlphaGo 就不同了——这个家伙的布局很牛。请看第2局的布局阶段，电脑下出了布局的妙手。

![不见图 请翻墙](https://lh3.googleusercontent.com/L7JawEKL7jK9kh_7zEkor_MK_l2cfk_vXz-iSO7HWMDTTpS66x2yTFLSGdj0Y6ubDNrBZ0ZvpP89l6bifg3iiNjTbt4yArNb2-kTy3ljPxdUhYOdDkFgPJAgZWvEoAn5R71GBPOQP6o)

　　这是 AlphaGo 的又一个妙手。对这一手，职业棋手评价非常高：

  

> 聂卫平说“对狗的下法脱帽致敬” 现场的英语解说员雷德蒙德和加洛克点评说“黑37手具有围棋名宿吴清源的风范”（雷德蒙德是目前唯一的非东亚裔的职业九段）。 曹大元说“这是特别意外的情况，在此之前没人这么下过。职业棋坛对这一手棋褒贬不一，有人特别赞赏，有人特别业余。但是这一手棋是超出职业棋手想象的，对棋手有很大的启发。”

  
　　其实在前面第1个例子，AlphaGo 已经体现出很好的大局观了。它没有按照定式去走右上角，是为了消解右下方的“黑7”子。

![不见图 请翻墙](https://lh4.googleusercontent.com/7VjlkN_h2-yIFktMFKyEw241u1wBc6wqAwNwrOx7NvRJy1RMXoMy3-tk-RFlPMf7SGGcyrqVxUy22ohVDQP33VrP3BCeteCzIimAvSiOLMkz7Rq4VSVeGPHYzEZ-iWeORDS6uRsrOY4)

![不见图 请翻墙](https://lh4.googleusercontent.com/WDJP3ZxAM0kc-zP6Sdw-bqlgyNaziUE1uNLuCJvskJPQyvi0I26P9PyXawDZwr1D-dH65xxPSujnWTETQIig6gB6QLCs5loUsQFJ89koZxcTXc0LS8SI6x0C38zUrQPkeVot9lOmk5w)

　　另外，同样在第1局，电脑下出了“白102”。在当天的评论中，有职业棋手认为：这一手可以载入史册。

![不见图 请翻墙](https://lh4.googleusercontent.com/dj2VmreDQw0RcpM7tZSUv8CqoSyssaBNz9EZI0TBQPVJv287YXJjJ-UYfsX1Fpdor73ex9LwojgJshil8whwmlfuT8DD3WUUoVb76Y-y1j5B7IdB4Oqy7p3TEhBHQKHWsu95VSddiWM)

　　面对这一手，李世石长考很久，后来依然吃了大亏。

　　大多数职业棋手都没有想到 102 这一手，即使少数人想到了，也未必敢在实战中使用——因为后续的变化分支太多太复杂。 　　之前很多人都觉得——只有人类棋手才有创造性，围棋程序是不可能创造性的。 　　但是你看这两天的对局，AlphaGo 下出了很多职业比赛从来没有出现过的下法。并且这些全新下法，对它而言是有利的。但是从来没有人类棋手这么下过。 　　这当然就是创造性！

　　比如第一局的“白86”，韩国金成龙九段的评价是：成为职业棋手27年来，第一次看到白断这手棋！

  

![不见图 请翻墙](https://lh6.googleusercontent.com/Sxlr4dvNcpkJwPGMAkRSbV8aNpVWqjuldiYOw5a0WV8yOvjE5Fqg66OfruwvuiZ-tFEBWE-Dqt8nlS6yyCyseBj6BoPJv-TYkSIlQmXuyMg2ySQ29o-ObkvCDqvtOrQ4O8mVukEoXtM)

　　这两局比赛，AlphaGo 出现了好几个奇怪的下法，被某些职业棋手认为是“缓手”（比如下面几例）。

![不见图 请翻墙](https://lh6.googleusercontent.com/Dlrtpc46qITc9LiNmnizG3r0z5u2fwrh9Sqc80UmtaWlU_ZRGsnU-pIPwMIbOCVA9KAz4n7zl5m3euDxIzSlPATCqOvUe_QWjZH25as4zgaImTYhdgP_tvrIBrhF2rzR5NucB1jtJKY)

  

![不见图 请翻墙](https://lh6.googleusercontent.com/YQbQAVG6S8-crWRgefTM2MuBI2IdKB-cUdWAi2_vVUoMgSA7pmw9-ciqlUNuHjbR14dpPGlWKTFBs9e_-DXWgYRoq9Aq6sOvTSvex9HKCxuai6GJiRWIgRJ_XpxUtCUBQAuNFOzhHE4)

　　但实际上他们不了解 AlphaGo 与人的差异。AI 追求的是【获胜的概率大小】，而不在乎赢多少目。当电脑面临 X Y 两个选择。有可能 X 比 Y 会多赢很多目，但 X 比 Y 的获胜概率略小。那么电脑还是会选择 Y 而不是 X。 　　或许可以这么说：当 AlphaGo 开始下出所谓的“缓手”，就意味着——它认为自己胜券在握了。 　　从这两天的对战情况，也大体是如此。 　　因为这两局比赛都没有出现劫争，于是又冒出一种说法——“AlphaGo 不擅长打劫”。甚至还有小道消息称：Google 与李世石之间有保密协议，约定不得使用打劫。 　　俺觉得：AlphaGo 在两天之内能下出这么多妙手，不至于连打劫都不擅长。它的“深度神经网络”既然如此优秀，评价“劫争”的局面优劣，应该不在话下。 　　很多人都希望——后续的对局中，能看到 AlphaGo 下出精彩的打劫。 　　补充： 　　本文发出后，某热心读者在评论区4楼1单元贴出了 AlphaGo 作者的【辟谣】——没有所谓的“保密协议”，Google 团队也希望 AlphaGo 能下出劫争。 　　继续补充： 　　本文发出的次日，俺在晚上看到某个职业棋手的辟谣——早在5个月前，AlphaGo 对战樊麾的时候，已经有两盘棋【出现了劫争】。

　　**所谓“AlphaGo 不擅长劫争”的言论，可以休矣！**

　　比赛前，几乎所有职业棋手都看好李世石，大部分职业棋手断定李世石能以5：0全胜。李世石赛前也说——自己的目标是一盘都不输。 　　如今的局面，很多人已经大跌眼镜。 　　为啥大多职业棋手出现如此严重的误判，有如下两个原因： 1、长期以来，围棋软件的水平都很烂，连业余选手都无法战胜 2、虽然 AlphaGo 已经在5个月前，战胜了欧洲冠军樊麾（职业二段）。不过捏，很多人都认为樊麾的棋力太弱，而 AlphaGo 赢得也不够漂亮。 （殊不知，AlphaGo 可以通过不断自学习来自我提升，5个月的时间，AlphaGo 已经今非昔比了） 　　第一天（3月9日）的比赛结束后，柯洁九段在个人微博上称：“就算阿尔法狗（AlphaGo）战胜了李世石，但它赢不了我。” 　　俺不清楚他这句话是真实想法，还是为了替自己造势。如果这是柯洁的真实想法，很可能柯洁严重低估了 AlphaGo。

　　在第二天（3月10日）的比赛中，小李明显是全力以赴的。曹大元九段评价说：如果昨天李世石的发挥只有70到75分的话，那么今天是90到95分。

　　结果捏，小李再次完败。英文发布会上的翻译是“clear loss”。整个比赛都是 AlphaGo 在主导，小李貌似没啥机会。 　　某些职业棋手称——看第2局的中盘，AlphaGo 已经超过全盛时期的李昌镐。 　　前面俺说了——电脑在乎的是【获胜的概率】，而不是赢多少目。所以，千万不能以胜负目数来衡量 AlphaGo 的棋力。你让它跟业余选手下，它或许也是赢这么多目。 　　俺觉得：如果真的要进一步衡量 AlphaGo 的棋力，没准应该安排 AlphaGo 与人类顶尖旗手下“让子棋”（让人先下N子） 　　在本文的结尾，俺引用国际围棋联盟秘书长李夏辰（韩国棋手、职业3段）的一段话：

> 第一次听说电脑要挑战顶级棋手李世乭时，我非常惊讶。我觉得挑战者一定对顶级棋手有多强毫无概念；  
> 但事实上，是我对电脑有多强没有概念。

　　俺觉得：大部分职业棋手对 AlphaGo 有多强，依然缺乏足够的认识。

**俺博客上，和本文相关的帖子（需翻墙）**：

  
[每周转载：关于人工智能对人类的影响（网文3篇）](https://program-think.blogspot.com/2012/07/weekly-share-10.html)

