---
layout: default
title: '开源点评&#65306;cURL&#8212;&#8212;优秀的应用层网络协议库'
date: None
author:
    display_name: 
---

　　今天来点评一下 [cURL](https://en.wikipedia.org/wiki/CURL)，这是一个老资格的开源项目，使用它可以基于多种应用层网络协议进行数据传输（包括上传和下载）。它的特点是：支持的协议多、跨平台、支持多种编程语言接口。后面俺会针对这些特点作一些简单的介绍。  
  
　　cURL 项目实际上包含两个部分：命令行工具 ＆ 编程库（[libcurl](https://curl.haxx.se/libcurl/)）。两者支持的功能基本相同。由于开发人员更多地是和 libcurl 打交道，所以本文主要介绍 libcurl。 　　这里所说的“应用层协议”指的是 OSI 模型中的第7层。如果你不了解“OSI 模型”，可以看如下这篇很全面的扫盲：

《[计算机网络通讯的【系统性】扫盲——从“基本概念”到“OSI 模型”](https://program-think.blogspot.com/2021/03/Computer-Networks-Overview.html)》

　　“支持的网络协议【很多】”是 cURL 的主要卖点。（截至到俺写本文时）cURL 最新的是 7.19.4 版本，它支持的网络协议至少有：FTP、FTPS、HTTP、HTTPS、[SCP](https://en.wikipedia.org/wiki/Secure_copy)（secure copy）、[SFTP](https://en.wikipedia.org/wiki/SSH_file_transfer_protocol)（SSH FTP）、[TFTP](https://en.wikipedia.org/wiki/Trivial_File_Transfer_Protocol)（trivial FTP）、[Telnet](https://en.wikipedia.org/wiki/Telnet)、[DICT](https://en.wikipedia.org/wiki/DICT)、[LDAP](https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)、LDAPS、[FILE](https://en.wikipedia.org/wiki/File:URL)，挺多的吧？

　　HTTP 估计是最常用的一种协议，俺简单说一下 cURL 对 HTTP 支持的程度。 对于协议版本：cURL 支持 HTTP 1.0 和 HTTP 1.1（注：俺写此文时，HTTP 2.0 还没诞生；等到 HTTP 2.0 发布后，cURL 也很快支持了） 对于请求方式：cURL 支持 GET、POST、PUT、File Upload POST

对于代理（Proxy）类型：既支持 HTTP 代理，也支持 [SOCKS 代理](https://en.wikipedia.org/wiki/SOCKS)（SOCKS4 ＆ SOCKS5）。

　　另外，cURL 还支持 HTTP 认证的用户名/口令，cookies，referer 等许多杂七杂八的东东。  
　　假如你要支持某些依赖 SSL/TLS 的协议（比如 HTTPS、FTPS），则需要用到 [OpenSSL](https://en.wikipedia.org/wiki/OpenSSL) 库。在 cURL 的[下载页面](https://curl.haxx.se/download.html)上标注有 SSL 标志的压缩包，都已经内置了 [OpenSSL](https://en.wikipedia.org/wiki/OpenSSL) 的动态库。另外，如何在 cURL 配置 SSL 证书，可以参见其官网的“[这个页面](https://curl.haxx.se/docs/sslcerts.html)”。 　　cURL 支持的平台相当多。即使是一些冷门的操作系统（比如：DOS、OS/2），它也支持得很好。

　　另外，cURL 官方网站的[下载页面](https://curl.haxx.se/download.html)提供了基于不同平台的、编译好的、二进制文件供大伙儿直接使用。对于 Linux，它还根据不同厂商、不同发行版本，分别提供二进制文件，考虑相当周到。相比某些开源项目只提供源代码（使用者需要自己动手编译），cURL 算是很方便的一个。

  
　　和上次 [点评的 SQLite](https://program-think.blogspot.com/2009/03/opensource-review-sqlite-database.html) 一样，libcurl 也支持多种编程语言的绑定，而且 cURL 整合的编程语言比 [SQLite](https://en.wikipedia.org/wiki/SQLite) 还要多。下面列了一些比较常见的编程语言和平台提供的 cURL 接口。 　　cURL 本身是 C 写的，因此 C 和 C++ 都可以直接调用它的 C 接口 API。在 cURL 的源码包中带有很多 C 的示例，大伙儿可以依样画葫芦。

　　喜欢 OO 风格的同学，可以使用 [cURLpp](http://curlpp.org/) 提供的 C++ 包装类。这玩意儿使用 MIT 许可协议。

  
　　cURL 和 Java 的整合通过 JNI 实现。可以在“[这里](https://curl.haxx.se/libcurl/java/)”下载压缩包，然后自己编译出相关的动态库和 class 文件。那些懒惰的同学可以到“[这里](http://www.gknw.de/mirror/curl/curl_java/)”捡现成。  
　　[pycurl](http://pycurl.sourceforge.net/) 是 cURL 的 Python 包装库。如果你觉得 Python 内置的 [urllib](https://docs.python.org/library/urllib.html) 功能不够，可以考虑用它。（这玩意儿使用双重许可协议：LGPL 和 MIT/X）  
　　cURL 和 dotNET 的绑定 [libcurl.NET](http://libcurl-net.sourceforge.net/)。这玩意儿只支持 Win32 操作系统。不过不要紧，对于非 Windows 系统，可以使用 cURL 的 [Mono](https://en.wikipedia.org/wiki/Mono_%28software%29) 绑定 [libcurl.mono](http://forge.novell.com/modules/xfmod/project/?libcurl-mono)。  
　　cURL 和 VB 的绑定 [libcurl.vb](http://libcurl-vb.sourceforge.net/)。这个项目和上述的 [libcurl.NET](http://libcurl-net.sourceforge.net/) 都由同一个作者维护，也都使用 MIT 许可协议。  
　　PHP 要支持 cURL 相对简单多了。在 [PHP 官方网站](http://cn.php.net/curl)上有相关的安装/配置说明。  
　　cURL 的 Ruby 的绑定 [Curb](http://curb.rubyforge.org/)。（这玩意儿使用 Ruby 许可协议）  
　　cURL 和 Perl 的绑定 [WWW::Curl::Easy](http://search.cpan.org/%7Ecrisb/WWW-Curl/Easy.pm.in)。（这玩意儿使用 MPL 或 MIT/X 许可协议） 　　前面说了很多 cURL 的特点，下面来随手举几个应用的例子。 　　如果你需要在程序中进行文件的上传、下载，使用 libcurl 会非常方便。由于它支持的协议很多。一旦将来你的应用程序发生需求变更，改用其它协议，你的代码也不用大改。 　　随着 SOA 风格的流行，很多比较复杂的系统都会提供很多 Web API 接口。如果你要在程序中调用 Web API 接口，可以考虑使用 libcurl 来实现。  
　　还记得之前[善用自动化](https://program-think.blogspot.com/2009/02/7.html#test)的帖子里提到自动测试的好处吗？由于 cURL 对 HTTP 的支持很全。在 HTTP 协议方面，浏览器能干的活它基本上也能干。再加上它可以和很多脚本语言绑定（除了前面提到的，还可以支持 Lua、Tcl、Lisp 等脚本）。所以你可以用“脚本语言 + cURL”的方式，来进行某些自动化的 Web 测试。 　　比如测试某 Web 站点的安全性（是否有 SQL 注入、XSS 跨站脚本等安全漏洞）或者测试某 Web 接口是否符合文档的约定或者测试某些 Web 接口的性能或者......  
　　如果你想定期了解 cURL 的新版本、新特性、新 Bug，可以订阅[相关的邮件列表](https://curl.haxx.se/mail/)。 　　另外，cURL 使用 MIT/X 衍生协议，可以用于商业软件中。如果你不太熟悉“开源许可协议”，可以看如下这篇介绍：

《[澄清“自由软件、开源软件”相关概念及许可证的误解](https://program-think.blogspot.com/2019/03/Misunderstand-Free-and-Open-Source-Software.html)》

**俺博客上，和本文相关的帖子（需翻墙）**：

  
《[计算机网络通讯的【系统性】扫盲——从“基本概念”到“OSI 模型”](https://program-think.blogspot.com/2021/03/Computer-Networks-Overview.html)》  
《[架构设计：生产者/消费者模式](https://program-think.blogspot.com/2009/03/producer-consumer-pattern-0-overview.html)》（系列）  
《[开源点评：ZeroMQ 简介](https://program-think.blogspot.com/2011/08/opensource-review-zeromq.html)》  
《[开源点评：Protocol Buffers 介绍](https://program-think.blogspot.com/2009/05/opensource-review-protocol-buffers.html)》  
《[开源点评：SQLite 数据库扫盲](https://program-think.blogspot.com/2009/03/opensource-review-sqlite-database.html)》  
《[澄清“自由软件、开源软件”相关概念及许可证的误解](https://program-think.blogspot.com/2019/03/Misunderstand-Free-and-Open-Source-Software.html)》  
《[如何选择开源项目](https://program-think.blogspot.com/2009/02/how-to-choose-opensource-project.html)》

