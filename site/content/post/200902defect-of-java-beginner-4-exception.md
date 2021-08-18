---
layout: default
title: 'Java 新手的通病[4]&#65306;异常处理使用不当'
date: None
author:
    display_name: 
---

　　上一个帖子讨论了“[编程习惯的问题](https://program-think.blogspot.com/2009/02/defect-of-java-beginner-3-code-style.html)”，今天来聊聊关于异常处理的话题。 　　犯这种错误的人比较少，一般发生在刚学会 Java 或者刚参加工作不久的人身上。 　　所谓“空 catch 语句块”就是在 catch 语句块中没有对异常作任何处理（比如记错误日志），导致异常信息被丢弃/忽略。一旦程序不能正确运行，由于查不到任何 log 信息，只好从头看代码，靠肉眼找 bug。 　　很多人在 catch 语句之后不使用 finally 语句。由于在 try 语句中可能会涉及资源的申请和释放。如果在资源申请之后、资源释放之前抛出异常，就会发生资源泄露。

　　（资源泄露的严重性，[上一个帖子](https://program-think.blogspot.com/2009/02/defect-of-java-beginner-3-code-style.html#gc)已经聊过了）

　　有些人为了省事，只在自己模块的最外层代码包一个 try 语句块，然后 catch(Exception)。不管捕获到什么异常，都作统一 log 了事。这种做法比“空 catch 语句块”稍好，但由于不能对具体的异常进行具体处理，对一些可恢复的异常（下面会提到），丧失了恢复的机会。而且也可能导致上述提到的资源泄露的问题。 　　有些人放着 Java 的异常机制不用，而用函数返回值来表示成功/失败（比如：返回 true 表示成功、false 表示失败），简直是“捧着金碗要饭”。个人感觉，从 C 转到 Java 的人比较容易有此毛病。这种做法会导致如下几个问题： 1. 返回值一般用整数值或布尔值表示，传递的信息过于简陋； 2. 一旦调用者忽略了错误返回码，就会导致和“空 catch 语句块”类似的问题；

2\. 对同一个函数的多处调用，都需要对返回值进行重复判断，导致代码冗余（代码冗余的坏处，[上一个帖子](https://program-think.blogspot.com/2009/02/defect-of-java-beginner-3-code-style.html#copy_and_paste)也已经聊过了）。

　　这个现象比较普遍，俺发现很多2年以上 Java 工作经验的人尚未完全搞明白两者的区别。看来这个问题得详细说一下。 当初Java的设计者有意区分这两种异常，是别有深意的。其中“Checked Exception”用于表示可恢复的异常（也就是你必须检查的异常）；而“Runtime Exception”表示不可恢复的异常（也就是运行时异常，主要是程序 bug 和致命错误，你【不需要】检查）。不过这种做法引来了很多争议（包括很多 Java 大牛），鉴于本帖子主要针对新手，以后再专门来聊这个争议的话题。 　　为了便于理解，下面我举一个例子来说明。假设你要写一个 Download 函数，根据传入的 URL（String 参数）返回对应网页的内容文本。这时候有两种情况你需要处理： 1. 如果传入的 URL 参数是 null，这表明该函数的调用者出 bug 了，而程序本身的 bug 是很难在运行时自我恢复的。这时候 Download 函数必须抛出 Runtime Exception。并且 Download 函数的调用者【不应该】尝试去处理这个异常，必须让它【尽早】暴露出来（比如让 JVM 自己终止运行）。 2. 如果传入的 URL 参数非 null，但是它包含的字符串不是一个合法的URL格式（可能由于用户输入错误导致）。这时候 Download 函数必须抛出 Checked Exception。并且 Download 函数的调用者必须捕获该异常并进行相应的处理（比如提示用户重新输入 URL）。

上面就是几种常见的Java异常处理的误用。下一个帖子我们来聊一下“[对虚拟机（JVM）了解不足](https://program-think.blogspot.com/2009/05/defect-of-java-beginner-5-jvm.html)”。

