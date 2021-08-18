---
layout: default
title: '扫盲 HTTPS 和 SSL/TLS 协议[0]&#65306;引子'
date: None
author:
    display_name: 
---

![不见图 请翻墙](https://lh4.googleusercontent.com/H_exzSD20W99qSJhGkLJFPwj3gU7VF_t9VGsbHS19Zkky6Vgrhcn8OG4c3--8-qr3DjL-H6lOQVfYcYEZ5qQp19yOycAvaL-Dnl29AqINsIhWK6ITliRP_tBL4nZ4z_Vw0IO)

  
　　今天这篇算是补之前的欠债——俺在4年前写过几篇关于 CA 证书的扫盲（“[这里](https://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html)”和“[这里](https://program-think.blogspot.com/2010/02/remove-cnnic-cert.html)”），之后有不止一位热心读者建议俺写一篇关于 HTTPS 的扫盲。因为俺比较懒，当时没动笔，一拖就是两三年，都有点忘了。正好今年出了两个跟 HTTPS 相关的高危漏洞（[Heartbleed](https://en.wikipedia.org/wiki/Heartbleed) 和 [PODDLE](https://en.wikipedia.org/wiki/POODLE)），于是俺又想起这事儿。 　　本来想单独写一篇。等写完“背景知识”这一章节，发现篇幅已经很长了。所以就再开一个系列吧。 　　事先声明： 　　既然叫做“扫盲”，所以俺尽量避免讲太多的“技术实现细节”（当然，更不会去讲“代码实现”）。本系列侧重于：尽可能通俗地介绍“设计思路”、“实现原理”，最后再聊聊“针对 HTTPS 的攻击手法”和“相关的安全防范措施”。一开始计划写3~4篇，后来篇幅有点失控，估计要写7~8篇。 　　虽然是扫盲，或许也能让 IT 技术人员从中获益——因为俺发现：连安全行业的某些程序员，对 HTTPS 的原理也所知甚少。

为了方便阅读，把本系列帖子的目录整理如下（需翻墙）：

  
1\. [背景知识、协议的需求、设计的难点](https://program-think.blogspot.com/2014/11/https-ssl-tls-1.html)  
2\. [可靠密钥交换的难点，以及身份认证的必要性](https://program-think.blogspot.com/2014/11/https-ssl-tls-2.html)  
3\. [扫盲几种密钥交换（密钥协商）算法](https://program-think.blogspot.com/2016/09/https-ssl-tls-3.html)  
4\. [历史版本的演变及 Record 协议的细节](https://program-think.blogspot.com/2018/09/https-ssl-tls-4.html) 5. 握手过程的细节 6. 针对 HTTPS 的各种攻击手法 7. 各种相应的防范措施

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[计算机网络通讯的【系统性】扫盲——从“基本概念”到“OSI 模型”](https://program-think.blogspot.com/2021/03/Computer-Networks-Overview.html)》  
《[扫盲 DNS 原理，兼谈“域名劫持”和“域名欺骗／域名污染”](https://program-think.blogspot.com/2014/01/dns.html)》  
《[对比4种强化域名安全的协议——DNSSEC，DNSCrypt，DNS over TLS，DNS over HTTPS](https://program-think.blogspot.com/2018/10/Comparison-of-DNS-Protocols.html)》  
《[如何隐藏你的踪迹，避免跨省追捕](https://program-think.blogspot.com/2010/04/howto-cover-your-tracks-0.html)》（系列）  
《[扫盲 netcat（网猫）的 N 种用法——从“网络诊断”到“系统入侵”](https://program-think.blogspot.com/2019/09/Netcat-Tricks.html)》  
《[如何让【不支持】代理的网络软件，通过代理进行联网（不同平台的 N 种方法）](https://program-think.blogspot.com/2019/04/Proxy-Tricks.html)》

