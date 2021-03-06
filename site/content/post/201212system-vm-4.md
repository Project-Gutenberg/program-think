---
layout: default
title: '扫盲操作系统虚拟机[4]&#65306;虚拟系统的安装&#65288;多图&#65289;'
date: None
author:
    display_name: 
---

　　不少网友在博客留言中表达了对虚拟机系列的关注，所以今天再抽空发一篇。  
　　在[上一篇帖子](http://program-think.blogspot.com/2012/11/system-vm-3.html)，俺已经介绍了"如何适合你的虚拟机软件"。今天来扫盲一下如何在虚拟机软件中安装虚拟操作系统。因为本系列是扫盲，本文尽量写得傻瓜化一些，以迎合不懂技术的网友。  
  
　　由于篇幅有限，本文只介绍 VMware Workstation（**后面简称 VMware**） 和 VirtualBox 这两款虚拟机软件。

　　**VirtualBox**

　　因为是开源而且免费的，所以 VirtualBox 很容易获取。

　　用鼠标猛击“[这里](https://www.virtualbox.org/wiki/Downloads)”，打开 VirtualBox 官网的下载页面。该页面上提供了针对 Windows、Mac OS X、Linux 的安装包，根据你的操作系统择一下载即可。下载完安装包，再顺便把扩展包也下了（扩展包不区分操作系统的）。

　　顺便表扬一下 VirtualBox 的短小精悍。（截至俺写本文时）最新的 4.2.4 版本也才90兆。

　　**VMware**

　　VMware 因为是商业软件，下载稍微麻烦点。

　　用鼠标猛击“[这里](https://downloads.vmware.com/)”，打开 VMware 官网的下载页面。下载的时候，需要你输入一个 VMware 的帐号和口令。所以在下载前，你还得先用自己的邮箱去注册一个 VMware 的帐号（放心，是免费滴）。注册完帐号之后，你应该就可以顺利下载到安装包了。

　　拿到安装包还没完——这个安装包只能让你试用若干天。为了能长期用下去，你要么上网 Google 一下注册码，要么花银子买正版（因为俺博客搭建在 Google 平台，需要遵守美国法律，因此就无法在博文中公布“注册码”，还望谅解） 　　拿到虚拟机软件之后，再准备一张你要安装的操作系统的安装盘，可以是传统的光盘，也可以是 ISO 格式的光盘镜像文件。 　　俺个人建议用光盘镜像文件，比较方便。一来传统的光盘容易坏（比如不小心划伤）；二来传统光盘不论是自己刻录还是买盗版盘，都要花银子滴。反之，光盘镜像文件可以直接从网上下载，也可以找朋友 COPY，省钱又省力 :)

　　经常有人问如何搞到正宗的 Windows 7 光盘镜像。想知道的网友，请看《如何防止黑客入侵\[7\]：Web相关的防范》一文的留言（请耐心看完第12楼的前几条留言），链接在“[这里](http://program-think.blogspot.com/2012/10/howto-prevent-hacker-attack-7.html?comment=1350739642972)”。

　　不论是 VMware 还是 VirtualBox，安装过程都比较简单。如果你是菜鸟级用户，只需一路按 Next 即可。所以，这部分俺就不浪费口水了。 　　顺便提醒一下：VMware Workstation 从 6.0 版本开始就变得很臃肿——软件装好之后至少占掉你 1GB 的硬盘空间。 　　虚拟机软件装好之后，需要简单设置一下。下面分别介绍 VMware 和 VirtualBox 的全局设置。 运行 VMware，在主菜单上点“Edit”，再点“Preferences”，弹出 VMware 全局设置的对话框。 选“Workspace”标签页，设置今后你要创建的 Guest OS 的默认存放位置（如下图）。

如果你打算长期使用虚拟机，俺个人的建议是：单独开辟一个**大的硬盘分区**，专门用来存放你创建的 Guest OS。

  
![不见图 请翻墙](//lh3.googleusercontent.com/7V-kYPpFJ2XEMvGqCgWHpsnY01PzrxuMx_eq5fPl7gvat0PwOMzwJ_rgcB3U1VsFC1AYyhbU53KWgZaxAUG8Fx8-uTkoYoGKdiYUca7STH8PQdi1OOZIhZiqNKg) 选“Hot Keys”标签页，设置热键。 简单说一下热键的用途。 当某个 Guest OS 进入全屏模式，或者某个 Guest OS 捕获了鼠标键盘的输入，你可以通过按这个热键退回到 Host OS 如果你觉得默认的热键用起来还算顺手，就不用再设置了。

![不见图 请翻墙](//lh6.googleusercontent.com/V0gb4AaG7YWVzh78Zuco-oggoslB5RsWRfLhjLHyuH3GSqmAgP4_vQ5ANP6Qs0KUnk7USd2CmDjNhQh7VbWukgwz_IPgfGGrgbvt7KjODrUIp43cuJG4iKzhy5o)

选“Memory”标签页，设置内存参数。 首先，设置 VMware 预留的内存数量。如果你需要同时运行多个 Guest OS，就需要预留多一些内存。 其次，设置内存使用方式。有三个选项，俺简单解释一下： 选项1：所有的 Guest OS 都加载到物理内存 选项2和选项3：允许 Guest OS 使用 Host OS 的虚拟内存 如果你的物理内存足够大，建议用选项1（这样性能足够好）

![不见图 请翻墙](//lh5.googleusercontent.com/9JSs-MvebOqq203NVYM7XjVn2Eu69zAz3REuvX_MWCrJKY1ldLsuTjNmHpJQmC4UQY3jM24mTgA6_jhdwqnn6ygtn1-me1NY-SuvXEccESeCuxOiQbyKO2sWzXI)

运行 VirtualBox，在主菜单上点“管理”，再点“全局设定”，弹出 VirtualBox 全局设置的对话框。 在左边选“常规”标签页，设置今后你要创建的 Guest OS 的默认存放目录（如下图）

如果你打算长期使用虚拟机，俺个人的建议是：单独开辟一个**大分区**，专门用来存放你创建的 Guest OS。

  
![不见图 请翻墙](//lh5.googleusercontent.com/lpjPqj0-P7ZZ9x2Jo5_r4SW_cL8ieYXsE5npG4urXteK146zksT-x9WKE2ByjOjo7zjR9Z4EGw33MtaprFcWxRFxWUDkzD8wkm9jAtbYuUPthDjjyf9Qod6leuM) 在左边选“热键”标签页，设置 VirtualBox 的热键。 简单说一下热键的用途。 当某个 Guest OS 进入全屏模式，或者某个 Guest OS 捕获了鼠标键盘的输入，你可以通过按这个热键退回到 Host OS 如果你觉得默认的热键用起来还算顺手，就不用再设置了。

![不见图 请翻墙](//lh6.googleusercontent.com/G0tPAGjDFLJMx_WJ0QklrlW1arblfzD0n07T4HzrqE0W3x9cU2RCGbdPC_844BFmdLQQR8mH3B3V5pgAFWrE69VoHSLrieI5hjylSNP1_H0CqU2vm7Uasqgu69c)

在左边选“扩展”标签页，添加扩展包。 要添加的扩展包就是刚才下载安装包的时候，一起下载的那个扩展包。

![不见图 请翻墙](//lh6.googleusercontent.com/tvyVcmqw3TYA0B1PHoo_MKkD8f0z6yjXa87WKOCmCDErr6RRM3aSFF4rHNejnsKkG8kVvd5RloffzPw6kAToZ3ABgmxXfWKvedWC02C2dW05uyF6bByucS-7JiU)

下面分别介绍 VMware 和 VirtualBox 如何安装 Guest OS。 运行 VMware，在主菜单上点“File”，再点“New”，再点“Virtual Machine”，弹出创建 Guest OS 的向导。 向导第1步 作为新手/菜鸟，你显然要用默认的 Typical 向导。

![不见图 请翻墙](//lh3.googleusercontent.com/MvKAwhqGw4L0ztHiXq7daXdxv6KQGFZxcAwNj4ItYopQ-jwkOuti70Dt-M2gLYTmscBMTpXVfmL9Pjwo6vvGbIUdz4RLlaaDmcrLlJJjTPZ30JoYFlr4p84csQo)

向导第2步 选第三个选项，意思就是说：先创建一个空白的 Guest OS，最后再自己装系统。

![不见图 请翻墙](//lh5.googleusercontent.com/gE8ITfiVW_GQQfyzOCLoxHwEclrBtigZOBWW8ms6hQNyhQotTjJT1e3dGdcXaeXAdyS0WL5fOnoB3b7R1cFxuuJyctQdMi3X6wIZSy7vjBFWcTNuPIeATFIeDc4)

向导第3步 选操作系统类型和版本

![不见图 请翻墙](//lh6.googleusercontent.com/w6SWw-M5N80CB31_z8625fFwL2DX3COYFV9eRi-hQ2rjHZHbY6uy0tLWZhMUsQrIwwCkHm_kyN3ySDU_sfeO-WM7jNGwtSEabJ5VXjTEleh0bhzF6HBgURun584)

向导第4步 填写 Guest OS 的名称和存储目录

![不见图 请翻墙](//lh3.googleusercontent.com/XceRdE2XBSDwd48mhtfo9WYZTtGAotszQp-2Q3KV2Rdwr1gq2SatZbjwPl_T2NzBc5BJoEtqPcQ_fG5TxQq64jDQaFccRliow_jrF5fzdd4noVxgERIdZK2dNEQ)

向导第5步 这个向导默认只会帮你加一块虚拟磁盘。这一步是让你配置虚拟磁盘的大小。 如果你需要多块磁盘，待会儿自己到 Guest OS 的设置选项中配置。 这步完成后，向导就结束了，一个空白的 Guest OS 也创建好了。

![不见图 请翻墙](//lh3.googleusercontent.com/AoT_1A8Sathf_xoq05G2IZtTnDdHwX3W-JGGeJj7prNLWB4IbNkh0OHaKAgwoDd9F-RykXQOk9Z7rpseIJwPNUHmYfmE5NeuzRn5CO4n0xElji_NcTknMmvalT8)

Guest OS 创建好之后，调出它的设置对话框。 在“Hardware”标签页下，选择“Memory”，调整 Guest OS 的内存大小。如果你需要在这个 Guest OS 里面运行一些重量级的应用软件，就需要多配点内存给它。否则的话，直接用默认值即可。

![不见图 请翻墙](//lh4.googleusercontent.com/a3fWTVkVg2FFrhufAxM5aGyQcCVW2yH8eSZc5xs7J215iTbLny-KRu60LWtW8xvFb_X0XpHLle7l_2uCDmqfrKzp3amzlVMWjkwnT1G7ThxPUZ4VWMU7b77n2dA)

在“Hardware”标签页下，选择“Processors”，配置 CPU 的数量和每个 CPU 的核心数量。

![不见图 请翻墙](//lh4.googleusercontent.com/0oQPjX_oL0sppMKx_zL5_S48Y3QRKZjlo387BiFB_rAUhzWORUYFreIcaZGAVgSc3nvElzyYl5a-uHksgml-52my_VCFdpwg7ShxMZDVsVaIeSOIx_ZU-vVcpZE)

在“Hardware”标签页下，选择“CD/DVD”，然后在右边选（你要安装系统的那张安装光盘的）镜像文件。

![不见图 请翻墙](//lh5.googleusercontent.com/EmzJJA2bnvLOSyOjNZjSs1NSzPfTEr1gSyBWtdp9aGuXxUb4zYJqCyygpQWAerc6gOX73XrlQBi9tNUB7do3fdFnkJk9AFBdQNFFf7JcomYD6YGHgi-swMJOa2I)

上述步骤都配置完毕，点“Power On”按钮，Guest OS 就开机了。然后就是操作系统的安装过程（装系统就不用俺来教了吧？） 运行 VirtualBox，在工具栏上点“新建”，弹出创建 Guest OS 的向导。 向导第1步 选操作系统类型和版本

![不见图 请翻墙](//lh4.googleusercontent.com/uhcz_J97d6dBArorqAV6EwCXvuc-xzWUL8OVhFMk-mtwe_LF5LbhYEsFbf5ugSr437A64yeX1OI1t0tFzibGGskCoBmrC9vH7MfDLKL61ygGvO7whdjaPfI0iy4)

向导第2步 设置 Guest OS 的内存。 如果你需要在这个 Guest OS 里面运行一些重量级的应用软件，就需要多配点内存给它。否则的话，直接用默认值即可。

![不见图 请翻墙](//lh5.googleusercontent.com/IZ_dri-buWVHHP3NB8L0jzPArO4WzLMiWgzRA7Urasc208DDKJN8wKe3zkkfnvrlsUv4U8GSrG7h1u-h93OZaqYL6BmmiKJhK0DaaKbghZP1NfnV6vAYYK_ED4M)

向导第3步 创建一块虚拟硬盘给 Guest OS 用

![不见图 请翻墙](//lh5.googleusercontent.com/IVw5eIVaqEpDA5keZXU4kSTwg0GacHWCWqJSjF8vq-VC_Bfwi25lVDPYfkE4cAuY4TlRMQgYB63y8TL2RrcTKGlkwlf5IWXF7ZHFL_qogXaZmOaqETBsS90uinE)

向导第4步 选择虚拟硬盘的类型。 如果你不打算迁移到其它虚拟机软件，直接用 VirtualBox 自家的 VDI 格式。 如果今后有打算把创建出来的 Guest OS 迁移到 VMware，就可以选 VMDK 格式。

![不见图 请翻墙](//lh5.googleusercontent.com/kxEFyghdXa-6TbB7H6U7qwnfIWuOhDYP8sSE48rd-qqKc8QMmBxRF5zYtYR_IRPKdJVCrKOUDhGznrvxbERmwxjREKFig2udb6fweAIRpIQR7perVxQBOsF6Z4s)

向导第5步 选虚拟硬盘的分配方式。 除非你电脑的硬盘空间非常非常充裕，否则的话不要用“固定大小”。通常建议用“动态分配”方式。

![不见图 请翻墙](//lh6.googleusercontent.com/6DmhAlVgNtUGXDh3VDqAeT4J1wV6Hy6jHwv8Lr8rwT_KIUgu59cvDFE_s3C8xdEFT4rcDKR-GABl1BLkp_DMeTfTvQJcCltdtIWg0jr2jviwOSYTzfyF8ZutzVE)

向导第6步 这个向导默认只会帮你加一块虚拟磁盘。这一步是让你配置虚拟磁盘的大小。 如果你需要多块磁盘，待会儿自己到 Guest OS 的设置选项中配置。 这步完成后，向导就结束了，一个空白的 Guest OS 也创建好了。

![不见图 请翻墙](//lh3.googleusercontent.com/UrRrWZy-vxGODprOmsDlIbQ8gpJZVoSyfbl8v2gzBROIyAkkXTd17caoIRPja_5hw9xyLdPQ_2aB1acpsuYOoYDdVHxqgx8zQEPeDsR6ratJwuaUlpX3AvTdhYc)

Guest OS 创建好之后，调出它的设置对话框。 在对话框左边“系统”，配置 CPU 的数量。 VirtualBox 还有一个特色功能，就是设定 Guest OS 使用的 CPU 上限。这个功能可以防止某个 Guest OS 把 CPU 耗尽，导致你的 Host OS 失去响应（假死）。

![不见图 请翻墙](//lh4.googleusercontent.com/-4JGkiHbd5WNWT1_F7RZtaz1tytwVyggHYzw7iHVNJFQ95hOj9hkAR2rw6D-4vDxme62t5HvJzWEwHap7qXFLJB4HuVxf6CmK_zgp3ZVhgP0JPuevaUKG2EvJ1Q)

在对话框左边“存储”，然后在右边选（你要安装系统的那张安装光盘的）镜像文件。

![不见图 请翻墙](//lh6.googleusercontent.com/qQ77T2UQEyctXuJWm-NzEJk5VHYcic20FVaLinEtE3N3YcIKd9DSAD6KLDL6EzDmDT3v73iYXljoTViOS9CePCaDBnp99zUn4InCBtZlP-qdQ0mSpH673s-AA3Q)

上述步骤都配置完毕，点工具条上的“启动”按钮，Guest OS 就开机了。然后就是操作系统的安装过程（装系统就不用俺来教了吧？）  
　　以上就是两款常见的虚拟机软件安装 Guest OS 的过程。列位看官如果有啥疑问，请到[本文留言](http://program-think.blogspot.com/2012/12/system-vm-4.html)。本系列下一篇会介绍[虚拟系统的配置](http://program-think.blogspot.com/2012/12/system-vm-5.html)。

[回到本系列的目录](http://program-think.blogspot.com/2012/10/system-vm-0.html#index)

