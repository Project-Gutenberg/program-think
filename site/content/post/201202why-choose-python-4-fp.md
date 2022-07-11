---
layout: default
title: '为啥俺推荐 Python[4]&#65306;作为函数式编程语言的 Python'
date: None
author:
    display_name: 
---

　　春节前看到热心读者留言，提醒俺：Python 系列好久没更新了（不知不觉又过了一年多）。俺当时回复说：春节假期补上后一篇。昨天听到鞭炮声才发觉元宵已经到了，赶忙写出本文。  
　　[前一个帖子](https://program-think.blogspot.com/2010/08/why-choose-python-3-oop.html)介绍了 Python 作为“面向对象编程”（以下简称 OOP）语言的特点，今天来聊一聊 Python 作为“函数式编程”（以下简称 FP）语言的特点。考虑到本系列面向的是 Python 的门外汉或刚入门的新手，故本文仅介绍若干浅显的 FP 特性。 　　说实话，“函数式编程语言”是一个很大的话题。由于篇幅有限，本文不可能对这个话题做全面介绍。俺干脆偷一下懒，只简单说说。 　　从字面上看，所谓的函数式编程，就是以“函数”为中心的“编程范式”。估计有同学又会问了，啥是“编程范式”捏？哎呦，这又是一个很大的话题。通俗来讲，“编程范式”就是指编程的套路。比方说大家很熟悉的 OOP，就是一种“编程范式”。FP 跟 OOP 一样，都是一种编程的套路。做个简单类比：OOP 以“对象/类”作为程序设计的核心，而 FP 以“函数”作为程序设计的核心。 　　既然说到 FP，自然要稍微说一下 FP 的特色。 　　刚才说了，FP 是以函数为中心。既然如此，在支持 FP 的语言中，函数的功能自然十分牛X。通俗地说，OOP 语言中，类/对象能干的事情，FP 语言中的函数也能干。下面做一些对比，以加深大伙儿的印象。 　　OOP 中，对象可以互相赋值；FP 中，函数可以互相赋值。 　　OOP 中，对象可以作为函数的参数/返回值，FP 中，函数可以作为函数的参数/返回值。 　　某些 OOP 中，类可以嵌套定义；FP 中，函数可以嵌套定义。 　　某些 OOP 中，可以有匿名类；FP 中，可以有匿名函数。  
　　在 FP 中，特别强调函数不要有“副作用”（洋文叫“[side effect](https://en.wikipedia.org/wiki/Side_effect_%28computer_science%29)”）。没有副作用的函数，又称之为纯函数（pure function）。其输出完全依赖于输入。换句话说，只要输入一样，输出就一样。 　　要成为纯函数，函数内部不能读写函数外部变量、不能有设备 I/O（比如读写文件）...... 　　无副作用是 FP 的重要特性。FP的很多优点来自于此特性。 　　在 FP 中，尽量避免用控制流语句（循环语句、判断语句）。对于控制流语句，FP 有另外的替代方式。比如：常用递归或高阶函数来替代循环。如此一来，FP 的代码会显得更简洁，更可读。 　　大部分支持 FP 的语言，也都支持多态。函数参数支持多态化，便可实现非常灵活的功能。

　　说了这么多，不知道大伙儿明白了没？还是没整明白的同学，请看[维基百科的英文词条](https://en.wikipedia.org/wiki/Functional_programming)（中文词条太简单，看不明白滴）。

  
　　洋文实在看不下去吗？那不妨看看 IT 大牛 Joel 写的《[你的编程语言能这样做吗？](http://www.joelonsoftware.com/items/2006/08/01.html)》（中文版在“[这里](http://local.joelonsoftware.com/wiki/%E4%BD%A0%E7%9A%84%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80%E5%8F%AF%E4%BB%A5%E9%80%99%E6%A8%A3%E5%81%9A%E5%97%8E%EF%BC%9F)”）。此文以 JavaScript 来阐述 FP 的妙处。 　　再稍微说一下 FP 的好处，以强化大伙儿学习的动力。 　　在 FP 的思想中，函数最好是“纯”的，而且最好只完成“单一”的任务。在这种指导思想下，函数的模块化程度自然就高。 　　模块化程度高，直接的好处就是可复用性好。 　　刚才说了，FP 的思想强调函数又纯又小。这样的函数，代码的可读性自然好，修改起来也方便。 　　前面提到了纯函数。如果你的程序中大部分函数都是纯函数，则调试 Bug 会容易很多。像 OOP 中，类的多个成员函数都可以修改类的成员变量，有时候会导致调试极其困难。而纯函数没有此问题。

　　另外，多线程是调试的一大噩梦。当年俺还专门写过帖子，介绍 C++ 多线程的注意事项（在“[这里](https://program-think.blogspot.com/2009/04/debug-test-multithreaded-applications.html)”）。而纯函数由于没有副作用，不必担心各种“互斥”、“死锁”等问题。

　　除了易于调试，纯函数的输出仅仅依赖于输入，这一特点注定了它很容易进行单元测试。 　　在 FP 中，由于纯函数无副作用，很适合编写并行处理的代码。最典型并且在工业界获得巨大成功的例子就是 Erlang。 　　当然啦，FP 的好处远不止上述这些（比如还有：利于形式化证明）。限于篇幅，俺就不展开了。 　　Python 中，常见的函数定义和函数调用，想必各位都晓得了。下面说几种不太常见的，且跟 FP 有关的语法。 　　Python 可以把函数直接赋值给一个变量。举例如下：

def square(n) : \# 这是一个计算平方的小函数，后面会反复用它举例 return n \*\* 2 f \= square \# 此处赋值给变量 f
f(10) \# 此处返回100。注意：对该变量使用小括号，等同于调用函数

  
  
　　Python 可以用 lambda 关键字定义【**单行**】的匿名函数。套用刚才的例子  

square \= lambda x : x\*\*2 \# 定义一个单参数的匿名函数，并把该函数赋值给变量
square(10) \# 此处返回 100

  
Python 支持函数的嵌套定义（请看如下例子）。这种语法，在“闭包”中经常出现（后面会具体介绍“闭包”）。

def outer() : \# 外层函数 s \= "hello" def inner() : \# 内层函数 print(s) \# 此处引用的是外层作用域的变量 inner() \# 输出 hello s \= "world" inner() \# 输出 world

　　Python 内置了一大坨用于 FP 的函数，以方便程序猿写出简洁的代码。在接下去聊之前，俺有必要先介绍其中的2个。 　　为了省事，俺只介绍2参数的 map（正宗的 map 支持 N 参数）。 　　参数 func 是个函数，参数 iter 是个迭代器（也可以理解为集合） 　　map() 会把 iter 的每个元素传给 func，并把每次调用的结果保存到一个 list 中，然后返回此 list。 　　举例： 　　挨个计算整数 list 的平方：

map(square, \[1, 2, 3\]) \# 返回 \[1, 4, 9\]

  
　　参数含义同 map 　　filter() 会把 iter 的每个元素传给 func，如果 func 返回结果为 True，就把元素保存在一个 list 中，最后返回此 list。 　　举例： 　　要过滤出所有奇数，代码如下：

def odd(n) : return (n%2) \== 1 filter(odd, \[1, 2, 3\]) \# 返回\[1, 3\]

　　此处可以用上 lambda，把代码简化为一行：

filter(lambda n: (n%2)\==1, lst)

　　为了让大伙儿更深刻体会 FP 风格同传统风格的差别，俺把刚才两个例子组合一下——要求返回整数 list 中所有奇数的平方。 　　传统的写法（有控制流）：

def func1(old\_lst) : new\_lst \= \[\] for n in old\_lst : if odd(n) : new\_lst.append(square(n)) return new\_lst

　　FP 的写法（无控制流）：

def func2(lst) : return map(square, filter(odd, lst))

　　怎么样？是不是更简洁？连 for / if 这两个关键字都不需要了。 　　这个洋文比较难翻译。有人叫做“列表推导”，也有人称为“列表展开”或“列表解析”。（俺比较喜欢头一个翻译——不禁让人联想到“推倒”:） 　　在 Python 中，这是一个很好吃的语法糖——可以让你写出很简洁、很优雅的代码。 　　举例1： 　　还拿刚才过滤奇数的例子。

filter(lambda n: (n%2)\==1, lst)

　　上述写法可以等价替换为列表推导：

\[n for n in lst if (n%2)\==1\]

　　举例2： 　　再来一个稍微复杂的例子。假设有两个整数 list，分别存储矩形的宽度和高度。现在想把所有的宽度和高度进行两两组合，把大于 10 的面积打印出来。 　　传统的写法（2层循环，4行代码）

for w in width : for h in height : if w\*h \> 10 : print(w\*h)

　　FP 的写法（无循环，1行代码，多精致啊）

print( \[w\*h for w in width for h in height if w\*h \> 10\] )

　　除了列表推导，Python 中还有字典推导、集合推导等等。为了省点口水，暂且打住。  
　　闭包，洋文叫“closure”，解释在“[这里](https://zh.wikipedia.org/wiki/%E9%97%AD%E5%8C%85_%28%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%A7%91%E5%AD%A6%29)”。它是 FP 的常见手法。那闭包到底有啥用捏？俺举一个微积分中，函数求导的例子。（不懂微积分或者对高数有心理阴影的同学，别担心，请把注意力集中在代码上）  

def d(f) : def calc(x) : dx \= 0.000001 \# 表示无穷小的Δx return (f(x+dx) \- f(x)) / dx \# 计算斜率。注意，此处引用了外层作用域的变量 f return calc \# 此处用函数作为返回值（也就是函数 f 的导数）

  
现在，假设要计算二次函数 f(x) = x2 + x + 1 的导数，只需如下代码：  

f \= lambda x : x\*\*2 + x + 1 \# 先把二次函数用代码表达出来
f1 \= d(f) \# 这个f1 就是 f 的一阶导数啦。注意，导数依然是个函数

　　有了一阶导数，就可以很容易地计算该函数在某点的斜率 　　比如要计算 x=3 的斜率，只需： 　　如果要想得到二阶导数（导数的导数），只需依样画葫芦（瞧这代码写得多优雅） 　　看到这里，大伙儿不妨设想一下：如果不用 FP，改用 OOP，上述需求该如何实现？俺觉得吧，用 OOP 来求导，这代码写起来多半是又丑又臭。 　　今天聊了不少 FP 的语法特性，可惜还是没聊完。由于俺比较懒，而且怕写得太长没人看，所以一些高级话题（比如：迭代器、生成器、等），今天就不介绍了。假如列位看官对那些玩意儿感兴趣，再抽空单独写一帖。

[回到本系列的目录](https://program-think.blogspot.com/2009/08/why-choose-python-0-overview.html#index)
