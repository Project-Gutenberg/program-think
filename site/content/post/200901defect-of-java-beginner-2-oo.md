---
layout: default
title: 'Java 新手的通病[2]&#65306;缺乏面向对象的基本功'
date: None
author:
    display_name: 
---

　　按理说 Java 是一个很 OO 的语言，Java 社区也一向是充满了“对象”的氛围。但俺在面试 Java 程序员时，却屡屡碰到令人大跌眼镜的事情。俺碰到不止一个求职者，连什么是“多态”都讲不清楚。很多人号称用过设计模式，但一半以上都仅限于单键模式和抽象工厂模式。当我深入问他/她抽象工厂模式到底有什么好处时，很多人语焉不详。 　　为什么很多 Java 程序员会缺乏面向对象基本功？这得怪那些 Java 框架。现在 Java 的各种框架太发达、太傻瓜化了，导致很多程序员只需要按部就班、照着框架进行代码填空，基本已经丧失了 OOA 和 OOD 的能力。我手下有些个 Java 程序员，对 Spring、Hibernate 等框架了如指掌；但如果给他一个简单需求，让他写一个脱离 Web 框架的独立 Application，他就不知所措了。这样的开发人员，将来只能成为所谓的“软件蓝领”，岗位很难得到提升。

　　同[上一个帖子](https://program-think.blogspot.com/2009/01/defect-of-java-beginner-1-algorithm.html)一样，我这次也提如下几个问题：

★基于接口的继承和基于实现的继承各有什么优缺点？ ★继承（包括 extend 和 implement）有什么【缺点】？ ★多态（polymorphism）有什么【缺点】？ ★为什么 Java 可以多继承 interface，而不可以多继承 class？ ★假如让你写一个小游戏（比如人机对战的五子棋），你会如何设计类结构？ ★类结构设计时，如何考虑可扩展性？

　　如果上述这些问题你都能够搞得比较清楚，说明你的 OO 基础还过得去。否则的话，我建议你一边找些 [OOAD](https://en.wikipedia.org/wiki/Object-oriented_analysis_and_design) 和设计模式的书看看，同时自己动手写些简单的小程序（不依赖那些框架），把学到的模式理论结合到实践中。通过这种方式来提高自己 OOAD 的能力，效果会比较好。

　　后面来聊一下第3个通病：[缺少良好的编程习惯](https://program-think.blogspot.com/2009/02/defect-of-java-beginner-3-code-style.html)。

