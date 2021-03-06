---
layout: default
title: '扫盲操作系统虚拟机[5]&#65306;虚拟系统的配置&#65288;多图&#65289;'
date: None
author:
    display_name: 
---

　　[上一篇帖子](http://program-think.blogspot.com/2012/12/system-vm-4.html)介绍了“虚拟系统的安装”。今天扫盲一下虚拟系统的配置。跟上一篇类似，本文继续拿 VMware Workstation（后面简称 VMware）和 VirtualBox 来说事儿。 　　首先确保你已经有一个安装完成的虚拟系统（Guest OS），然后进行如下的准备工作。  
　　先启动虚拟系统并以**管理员**用户登录到虚拟系统中；然后，在 VMware 软件的主菜单选“VM”再选“Install VMware Tools”。接下来，VMware 就会在虚拟系统中启动 VMware Tools 的安装程序（你会看到一个安装界面自己跳出来）。你只需要一路点“Next”就可以了。 　　提醒一下：VMware Tools 是对应到每一个虚拟系统的。假设你有多个虚拟系统，那每一个虚拟系统都需要装一次。如果不安装“VMware Tools”，可能会影响后续介绍的若干功能。  
　　在[上一篇帖子](http://program-think.blogspot.com/2012/12/system-vm-4.html)已经介绍了 VirtualBox 扩展包的下载和安装，此处不再啰嗦。 　　提醒一下：确保你已经安装了扩展包。如果不安装扩展包，可能会影响后续介绍的若干功能。 　　虚拟系统就跟真实的电脑一样，也有几种不同的运行状态。  
**运行** 　　处于运行状态时，虚拟系统会占用物理系统的内存和 CPU。如果去看真实系统的进程列表，会看到该虚拟系统对应的进程在内存中。

**关机**

　　虚拟系统处于关机状态时，既不占用内存，也不占用 CPU。

**休眠**

　　当虚拟系统休眠时，虚拟系统的内存会被写到硬盘上。处于该状态，虚拟系统完全不占用真实系统的内存和 CPU。 　　和“关机”状态相比，“休眠”会多出一个内存文件（该内存文件的大小也就是虚拟系统的内存大小）。所以“休眠”状态比“关机”状态会多消耗一点硬盘。 　　“休眠”的好处在于：启动一个“休眠”的系统比启动一个“关机”的系统更快，而且休眠的系统唤醒之后，你的虚拟系统会恢复到休眠之前的样子，省得你再重新开启一堆软件。

**暂停**

　　处于“暂停”状态的虚拟系统，会继续占用物理系统的内存，但是不占用物理系统的 CPU。这时候如果去看物理系统的进程列表，会看到该虚拟系统对应的进程还在内存中，但是该进程的 CPU 占用率为零。 　　“暂停”的好处在于：当你同时运行好多个虚拟系统（俺就经常这样），如果感觉真实系统的 CPU 吃不消了，可以先把没用到的虚拟系统暂停。 　　“暂停”操作比“休眠”操作更快，因为暂停操作不需要把虚拟系统的内存写入磁盘。坏处是——被暂停的虚拟系统依然占用你的物理内存。 　　因为 VMware 采用洋文的界面，先简单列出术语对照表 Power On　从关机状态中启动，变为运行状态 Power Off　把运行状态中的虚拟系统变为关机 Reset　重启动“运行”状态的虚拟机 Suspend　休眠 Resume　从休眠中唤醒 Pause　在“暂停”状态和“运行”状态之间切换 以下是 VMware 的截图

![不见图 请翻墙](//lh3.googleusercontent.com/PbHACi4G3D56eviSmPIWXvYu12cvXYGCT4_7Nj80VcovymlzllS8QVioosxoAZFUw6AvazeeEdewsXpGDZcgPcFpVcStu4DxiDyUPhhzTYokw45xDPX0RwRgCZg)

　　VirtualBox 是中文界面，俺就不用再给术语对照了，直接上图。VirtualBox 的关机功能做得比较细致，赞一个。它的“正常关机”相当于“软关机”；它的“关闭电源”相当于“硬关机”。

![不见图 请翻墙](//lh6.googleusercontent.com/WutHNF66mkgvTpTWd9eRzO_WQejmSeJXTxpNwvX2GhamCedumRXI_c5MUKzfZERTf288hZ8k_NT6vfs0Cu1b0y4iDuJdUqGjbyCO3UBL1ovR0GShHRuTDCJwCrk)

  
　　快照功能是虚拟机最重要的附加功能。在本系列第2篇《[介绍各种应用场景](http://program-think.blogspot.com/2012/11/system-vm-2.html)》，俺已经介绍了很多快照的用途。 　　所谓的“快照”，就是把虚拟系统在某一个瞬间的各种状态信息保存下来。这里的“状态信息”至少包括：该虚拟系统所有（非独立）磁盘的状态、所有内存的状态、所有其它虚拟硬件的配置、等等（关于“独立磁盘”，后面会提到）。

　　而且虚拟机软件提供的快照功能是支持【**树形层次**】的，你可以在某个快照的基础上，再建立其它快照。什么是“树形层次”，看下面这张图，你应该就明白了。

![不见图 请翻墙](//lh4.googleusercontent.com/Uh2a4j8Qpt7M7Ghh3Sc5--4uug3ax5C9y9IkNfPp676ylq-PrzKqsjnEMZQJLgJWI6RmVKlscB923dou0EoXbXGBF-Y5s1toY1X7r8nAcA7fvml4r6B9S78YloA)

　　在 VMware 中，快照称之为“Snapshot”。选主菜单的“VM”再选“Snapshot”二级菜单，就可以看到快照相关的功能项。

![不见图 请翻墙](//lh5.googleusercontent.com/zL_ZFqKWuEcoWXehFRp42D7CgC8yMlV6-nB3Gj4iUJmYnrIyjwnHEQEPtSt3dzdVe_zL4oE9thktrcWXvbtLzB1TP9Bf_fEVVGxBkRZffVEACs_ot0_psN1zsdE)

　　也可以在选中某个虚拟系统之后，直接用**快捷键**“Ctrl + M”调出该虚拟系统的快照管理界面。刚才那张“树形层次”的截图，就是 VMware 的快照管理界面。

　　VirtualBox 的中文界面把“快照”翻译为“备份”（这样翻译，俺总觉得不太爽）。在 VirtualBox 管理器界面上，选中某个虚拟系统，然后点工具条右边的“备份”按钮，就可以切换到快照管理界面。

![不见图 请翻墙](//lh4.googleusercontent.com/UnTPqa7Djc7IW0RKNC7nXCm_l3TmcjpJ6L5SRTzl_oNDQ0841nq-e0BLYAk11j1T--Tqu1K1Ax0nZallQcajlnsPUDmY4RsRc4jvuiaVOzL8zsMWeBUBlZrnr18)

  
  
　　在本系列[前面博文](http://program-think.blogspot.com/2012/11/system-vm-3.html)已经简单介绍过显示模式。考虑到某些同学比较健忘，再啰嗦一次（下面这三种模式，VMware 和 VirtualBox 都支持）

**窗口模式**

窗口模式是最基本的显示模式。在这种模式下，整个 Guest OS 桌面显示为 Host OS 桌面上的一个窗口。所有 Guest OS 软件的界面都在这个窗口中。

**全屏模式**

全屏模式就是让 Guest OS 独占整个显示器。在全屏模式下，你看不到 Host OS 的桌面。

**无缝模式**

所谓“无缝模式”就是：让 Guest OS 里面的软件界面从虚拟机的窗口中“跑”出来，直接融合在 Host OS 的桌面里。这种效果是很酷滴！ 　　在 VMware 的主菜单选“View”就可以看到和显示模式相关的功能项。

![不见图 请翻墙](//lh4.googleusercontent.com/QoKE1nTm3ko6QrW2mVRnjL_x_Zucd-MqK7Vk0uCl2w-5vU5NRXx9UU4cWP6XGai3I0Jg7PQV4UsM_oTJ7P6cMlWQDO-tiDcfemaxYhqZuD-SoujEivUgSc1m-TY)

　　对于窗口模式，VMware 采用标签页的方式显示，每一个标签页是一个 Guest OS。

VMware 的全屏模式有两种，分别对应上述菜单的“Full Screen”和“Quick Switch”两种。至于哪一种比较好用，那就见仁见智了。想退出全屏模式，可以按“虚拟机热键 + Enter”（虚拟机热键的设置，[前一篇博文](http://program-think.blogspot.com/2012/12/system-vm-4.html)有介绍），也可以把鼠标移到屏幕顶部，就会自动浮现一个工具条（对于“Full Screen”）或菜单条（对于“Quick Switch”）。

　　上述菜单的“Unity”就是“无缝模式”。该功能需要 VMware Workstation 6.0 或更新版本才能用。如果你的 Guest OS 是用 6.0 之前的版本创建的，可能就用不了 Unity。 　　最后，建议勾选上述菜单的“Autofit Guest”选项。勾选之后，VMware 会自动调整 Guest OS 的桌面分辨率，以适应 Host OS 的显示器分辨率。 　　VirtualBox 的窗口模式跟 VMware 不太一样。每一个 Guest OS 都有一个单独的窗口。在这个 Guest OS 窗口的主菜单选“视图”，就可以看到跟显示模式相关的功能项。

　　菜单项右边是快捷键的提示。其中的“Host”表示你设置的虚拟机热键（虚拟机热键的设置，[前一篇博文](http://program-think.blogspot.com/2012/12/system-vm-4.html)有介绍）。最好熟记这几个快捷键。

![不见图 请翻墙](//lh5.googleusercontent.com/oTsVUfmzYGz8IzZLjzyc_ULwpdGW9aI2rqAbktn6l6sBc5ELnmF9iAm14LoLHZ1Euh2tNQFLFkbWxCdiSacKpNMcl2Z5VC7TNCs2SWehGIAgdwKgY4nuePZc1XQ)

　　VirtualBox 的窗口模式有两种：“有自动缩放”和“无自动缩放”。所谓的“自动缩放”，就是当你调整这个 Guest OS 的窗口大小时，Guest OS 的桌面分辨率会自动跟着调整，以适应该窗口的大小尺寸。 　　如果想退出全屏模式，可以按“虚拟机热键 + F”从全屏模式返回窗口模式；也可以把鼠标移到屏幕顶部，就会自动浮现一个工具条。  
　　在介绍虚拟系统的硬盘配置之前，先聊一下控制器。所谓的“控制器”，通俗地说就是用于主板和存储设备之间进行数据传输的玩意儿。早期的硬盘控制器主要有两种：IDE 和 SCSI；到2010年之后，SATA 基本成为主流。 　　上次有读者在博客留言，询问这几种的差异，俺今天简单说一下。一个 IDE 控制器最多只能支持4个设备。举个例子：你已经在 Guest OS 上添加了一个 IDE 的硬盘和一个 IDE 的光驱。那么，今后如果要再加 IDE 硬盘，就只能再加2个了。而 SCSI 和 SATA 就没有这个限制——单个控制器可以支持好多个设备（到底是几个，你就甭管了，反正足够你用的）。 　　选中某个虚拟系统，在主菜单选“VM”再选“Setting”（也可以直接用快捷键 Ctrl+D），就会弹出虚拟系统的“设置对话框”。然后点“设置对话框”下面的“Add”按钮，就会出现一个添加硬件的向导。该向导会帮你一步步地添加一个硬盘。以下是向导的5张截图。 第1步，硬件类型选“Hard Disk”

![不见图 请翻墙](//lh6.googleusercontent.com/uRe-M4OfQ7x84R8sb36N1M0DvktngkcEhwAYrlf7WGBy4uIeaV9GABzPes4HM7f7WDCOZXDjR0Ev5PTZDOnkgBqpPA3jbSQWzfonZMabdBecgOqeLZHtv6_fPC0)

第2步

![不见图 请翻墙](//lh6.googleusercontent.com/HIHAHcohePPsMM7CxJvzAjRPJ6ZQcdcxslnoTgzCO4GPdzeblfw128j78w7wxbpNhongjoXw_epkyktRDh2PNRBRCgfHqZwrm9hzt4OsxNv5NEnNHdOAeKQySuk)

第3步，制器类型和磁盘模式 制器类型刚才已经介绍过了。磁盘模式俺稍微说一下。 默认情况下创建的都是“非独立磁盘”，也就是说，虚拟机快照会记录磁盘上的所有数据。如果你勾选“Independent”，则创建的是“独立磁盘”。“独立磁盘”的数据不会受快照的影响。 “独立磁盘”又分两类：持久性和非持久性。在“持久性磁盘”上，所以的数据修改都会永久保存，不受快照回退的影响；在“非持久性磁盘”上，所有的数据修改都不会永久保存，每次虚拟机关机之后，磁盘的数据就会恢复原状。

![不见图 请翻墙](//lh3.googleusercontent.com/1ad6fUu9krIs3xdiRNJowfNQ-vzI6GaVkw8NLkBgkhyENJr4MMiWMY3L-B8Jpnk2UKwYHVCb1yYrED80ZaMH9TYz-O22GLsccbiDDhILwqKMZSb55jjECmW0hIA)

第4步，设置磁盘最大容量

![不见图 请翻墙](//lh6.googleusercontent.com/x5bNeKmzAEf03ivI45DalNsJYxDsCwYKCaAICxwN_bml4VLTKLXPVG7IGm3LOzN9AnWJ8D79jfP0aeahLIl3AEiRLjEeRe47aDxBjaQ3BbhaTZ-Baknm_rsC66s)

第5步，设置虚拟磁盘在 Host OS 的存储位置 通常 VMware 会给出一个默认文件名，你直接用这个文件名即可。

![不见图 请翻墙](//lh5.googleusercontent.com/NQxncmjLZZd3DZsYW7ir7Q6UW1lIe-5Lpl4v-YSHned0G9MxrZIam3SbHZ0Jqrut-D-vkD5YpUntrOoOiY00yXLIK4EifrY9VYU3NB544un4CwKF3ngmq26beKI)

　　在 VirtualBox 管理器界面上选中某个虚拟系统，在工具条上点“设置”（也可以直接用快捷键 Ctrl+S），就会弹出虚拟系统的“设置对话框”。在左边选“存储”，右边就会出现磁盘管理的界面。默认安装的 VirtualBox 虚拟系统，已经存在一个 IDE 控制器。

![不见图 请翻墙](//lh6.googleusercontent.com/qQFoswiQ0OQ0xjGsVz0XWhm7YSrOgkoCHYji7ALD4vq5_WMfmqrgBgNp6IXuwWxOM-J009Cxve2GJ5gkDCoaz6KBeHHCrIaONt6jOxiKkpODcFEBH8KRUYtFNME)

选中这个 IDE 控制器，点下方第一个带加号的按钮，然后选“添加虚拟硬盘”。

![不见图 请翻墙](//lh6.googleusercontent.com/P7YNH052ikmMxwkJFv_pZrJOec_GF_hp5JjwcYwd4eNUyQOQ7Wf22jOt_RqXY_GGMNRSVlSi6Q_u2TM-dVvWYtHi9YcTFEcKDbCRGmVgirGD9XSudj9Dg86DxQA)

它会问你是是“创建新的”还是“使用现有的”，你选“创建新的”。

![不见图 请翻墙](//lh6.googleusercontent.com/QfydXJkjn_PdSLxyT_abe_7MFAPpKcpE5K32goSoZolfyoJObB11Z0AllvL2qN-UqSU4CNTxuXPXwEKHK6hsvi_jfn96wXllxzJrNGZGEoSOcy9PcetS_F_IDzE)

　　之后就会弹出创建虚拟硬盘的向导。这个向导在[前一篇博文](http://program-think.blogspot.com/2012/12/system-vm-4.html)已经介绍过，这里就不再浪费口水了。

　　万一你需要添加的虚拟磁盘（包括虚拟光驱）超过了4个，那就得改用 SCSI 控制器。还是在刚才这个界面，点下方第三个按钮，弹出一个快捷菜单，选“添加SCSI控制器”。

![不见图 请翻墙](//lh6.googleusercontent.com/f6cISlTA41bMFoI7KOo1_SsUm6opAVjr2klUlWIR9tbo3E0XbsiIGzubmtbOFgQU33l4tds08e2q7B4z-vh3Stk4tvN1YqKcRffVQ3HjMyfSrj89FO3qZNME0TI)

然后就会多出一个新的 SCSI 控制器。选中该控制器，点下方第一个按钮，就可以创建新的 SCSI 磁盘了。

![不见图 请翻墙](//lh6.googleusercontent.com/_XIAtGFuVeaPRUKMQ_r9CFd9Z8W7eDVqiD8modtDPQmSClgmWEc4ds6tAP9bs8a7TTX2zemUYU_8eHpW0TJPOXdLfbaC84w_cYqNbLLMLkOtUD3_VTR6B9FWokE)

  
　　网卡的配置有点复杂，俺多费点口水。那些等着看“[双虚拟机配置方案](http://program-think.blogspot.com/2013/01/howto-cover-your-tracks-7.html)”的网友，一定要先把这个章节看仔细喽。 　　虚拟系统的网卡和真实系统有较大差别。虚拟系统的网卡可以设置为不同的模式。不同的网卡模式主要影响网卡可访问的范围（可见性）。常见的网卡模式有如下几种：

　　**Host Only**（对外部网络不可见）

　　顾名思义，该模式的网卡只在 Host OS 的范围内可见。因此，该模式的网卡是无法访问 Host OS 的外部网络（也就是说：无法访问其它电脑）。 　　虽然 Host-Only 网卡不能访问外部网络，但是多个 Host-Only 网卡之间是可以互相访问滴。比如你同时运行多个 Guest OS，把这些 Guest OS 上的网卡都设置为 Host-Only 模式，那么这些 Guest OS 是可以相互访问滴。

　　**NAT**（对外部网络单向可见）

　　NAT 的全称是“网络地址转换”。考虑到本系列是扫盲性质，俺就不解释 NAT 的原理了。 　　处于 NAT 模式下的网卡，可以访问 Host OS 的外部网络。比方说你的 Host OS 已经接入互联网，那么 Guest OS 里面的软件可以通过 NAT 模式的网卡上网。但是，Host OS 外部（也就是其它电脑）是看不到这个 NAT 网卡的。

　　**对于普通网友，俺建议把网卡设置为 NAT 模式**。因为 NAT 模式可以起到类似防火墙的效果，比较有利于保护你的虚拟系统的安全。

　　**Bridge**（对外部网络双向可见）

　　所谓的双向可见就是——Bridge 模式的网卡可以看到外部的电脑，外部的电脑也可以看到该网卡。 　　普通网友一般不需要 Bridge 模式，NAT 模式就足够了。

　　**Internal**（对外部网络不可见）

　　这个模式类似于“Host Only”，两者的差别如下： “Host Only”模式既可以被运行在 Host OS 系统中的进程看到，也可以被运行在 Guest OS 中的进程看到。 “Internal”模式对于运行在 Host OS 系统中的进程【不】可见；只对运行在 Guest OS 系统中的进程可见。 　　到目前为止，Virtual Box 支持“Internal 模式”，但是 VMware 不支持。所以下面以 Virtual Box 为例来说明其配置。 　　当你把某个 VM 的网卡模式设置为“Internal”模式，这时候界面上会让你输入一个“名称”——这是用来区分不同的“Internal 网段”的。 　　在 VirtualBox 里面可以同时配置多个相互隔离的“Internal”网段，如果两个不同的 VM，其网卡都设置为“Internal”模式并且名称相同，那么这两个网卡可以互相通讯；反之（如果名称不同），则无法互相通讯。 　　选中某个虚拟系统，在主菜单选“VM”再选“Setting”（也可以直接用快捷键 Ctrl+D），就会弹出虚拟系统的“设置对话框”。对于默认装好的虚拟系统，通常只有一个虚拟网卡。在“设置对话框”左边选“Network Adapter”，右边就是这个虚拟网卡的设置选项。

![不见图 请翻墙](//lh3.googleusercontent.com/THwuhIJ19uD9q6KDoU9ohzOOWFXHrJDXkdKjQdf1-EIycNzIyAPHavP66hra-xDustNgBBz1n-7zF5SWCltqhlIttSaksqP1HgpJ3O7SIcu_0UqFfNog7e1HI9Y)

　　如果你想添加多个网卡，可以点“设置对话框”下面的“Add”按钮，会弹出“添加硬件的向导”。然后选“Network Adapter”这个硬件类型。

![不见图 请翻墙](//lh4.googleusercontent.com/TxLtkNL6kIQN7Uf84FL-64AqOcbBEodGI_gDiwfNU_y9daI2cZ2lwlIF_GrC3U2iNg6E4FZASynkAYT9WlCxlWhFjBQsx2cbX_mP_vBpSME7PAnHp3MA-VGmalM)

　　向导的第2步会让你选网卡模式。

![不见图 请翻墙](//lh6.googleusercontent.com/1DRTMxYE2R1bKHb6hGQ6t9rEoU_jAsGtpHOrUCKIJqzMajgY6Z4L4rlJSgOWsV-ovRObRF8jc7IhNvQ6MBJQrAYPjyfpkVlChKrGjWWBJXeWuYjsXU3_aH6S9bU)

　　在 VirtualBox 管理器界面上选中某个虚拟系统，在工具条上点“设置”（也可以直接用快捷键 Ctrl+S），就会弹出虚拟系统的“设置对话框”。在左边选“网络”，右边就会出现网卡的配置界面。界面上有4个标签页，代表4个网卡。默认只有第一个是启用的。“连接方式”的下拉框会列出 VirtualBox 支持的网卡模式。 　　VirtualBox 支持的网卡模式比较多，但是其它那几种模式平时难得用到。最常用的还是 NAT 模式。

![不见图 请翻墙](//lh3.googleusercontent.com/L6X8agxT2ZGUwIbA7YMLtBcN8Jtpbtv8b6YzVKcoOh3h0_A4hYd7HK9GAh4yKru3yDqUA62hiDmkhkG5Gck7Z9Kd5ycL4fpyI1jTcT6jCl3W7Aw5zvd9XIHX0-c)

　　所谓的“数据交换”，就是在 Host OS 和 Guest OS 之间交换数据。 　　大部分虚拟机软件都支持“文件共享”。所谓文件共享，就是把 Host OS 里面的某个目录映射到 Guest OS 里面。如果你的 Guest OS 是 Windows 2000及之后的版本，可以到 Guest OS 的“网上邻居”里面找到被映射进来的目录。

　　**对于 VMware**

　　照例打开虚拟系统的“设置对话框”，切换顶部标签页到“Options”，参照下图设置

![不见图 请翻墙](//lh5.googleusercontent.com/QgvaZFt0sl2TVhXHB7Qbp4ej4tXtZiwu-ecIUTNL-5EOtTsZiez6Je0VDKMD3ZuwhvImLa5vYD3j8eDPuk0i9wFS50FYRY5YgaFl3elZXo8TcRwegq4JkTZXFqM)

![不见图 请翻墙](//lh3.googleusercontent.com/vsz7fkyBKym3X4_zkK6BZmTbB1c6ptnLT6sqFKJlq6X66-aKq6L44st5iAKFg2vLtrtBe7WW_3P5LtTb9ZKFm7N2lEx0pG5dJFTBWf8Oo2ZVnqkok9oH-OC7i_A)

　　**对于 VirtualBox**

　　照例打开虚拟系统的“设置对话框”，选左边的“共享文件夹”，参照下图设置

![不见图 请翻墙](//lh3.googleusercontent.com/qPEMwjNJEOigYHvMv8MveUAE-kjU9RKA89wjRg4l6Nglsjy49LGzxg1COIjkoZMA6grBlCxaTxxm4SfEPDyLQ7Vm61LjYLUrgRk97ZDxqCGBUgDFoz9LBR77K_8)

![不见图 请翻墙](//lh4.googleusercontent.com/kGNGoEx0SO-u71Id2R3i5URFSspmJ7M57aWTox1aF1PwOJyiQqF0J7yvpgWmeWIJx2wVl_wlkjjqcFCRGgxEliUSyEZw4gUPTcMVB2Ns6tKZSwKmPtE3QnrmH5s)

　　利用“文件拖放”功能，你可以在 Host OS 和 Guest OS 之间拖拽文件。 　　所谓“剪贴板共享”，顾名思义，就是让 Host OS 和 Guest OS 共用一个剪贴板。你可以在一个 OS 里面拷贝，在另一个 OS 里面粘帖。 　　对于这两个功能，VMware 只支持双向同步；而 VirtualBox 做得比较细致，支持单向同步。不过 VirtualBox 的文件拖放功能迟至 4.2.0 版本才加入，还不太成熟。

　　**对于 VMware**

　　照例打开虚拟系统的“设置对话框”，切换顶部标签页到“Options”，参照下图设置

![不见图 请翻墙](//lh6.googleusercontent.com/piio2QBGSHx8m3IXrHrHtGsdvfVPt-MEjB0sW9MZrq3zBHJRGpWX0rC1CW3dZ2GtP5ze_QqXag7mb6bi3DEFFzwEHQb-3-VLTSTCW9CHyn-eheZSoXKyd02t3PI)

　　**对于 VirtualBox**

　　照例打开虚拟系统的“设置对话框”，选左边的“常规”，参照下图设置

![不见图 请翻墙](//lh3.googleusercontent.com/x1BjoMGsHdKhh88r1fVCn8DniVDho1pS1XcVcHmpY9tIPYab_fUdQbn1iTKhTQn7El_DyJ6C6YPMPZEWhez4QV4Qcmm5c7nTiT_8UDnuIqR_hCuyIv2CvArIMmQ)

![不见图 请翻墙](//lh3.googleusercontent.com/XVosKVbJ56DQFwmkzc3j7oROhPcP6oyFdwUZ0Gn4WuhyeVO9TwGfhwQQ1Xl-0-X0wl8IqpIBfKwowQMAWJWt6sUKKNFHg-2E8hUhbHWTMsOqSEKamDZ14SqX_Oc)

　　该功能可以把某个虚拟磁盘映射到你指定的某个 Host OS 的盘符。这样一来，你无需启动虚拟机就可以访问虚拟磁盘的文件。 　　对于这个功能，VMware 提供了图形化的配置界面，而 VirtualBox 只能在命令行下搞定。考虑到本系列是扫盲性质，暂且只介绍 VMware 的配置操作。 　　VMware 的设置如下：照例打开虚拟系统的"设置对话框"，选中要映射虚拟磁盘，参照如下截图设置。

![不见图 请翻墙](//lh5.googleusercontent.com/tBM9g54n-9NW-LxbaR6vSOV0A1-WKQhDSBHiePtkECJWfRf3RBH8MoOPNxMybAGl8HnnMaI1x7vLcD9E1n_LoCdsmImegFg4UYRftzarC3kPGpUrDj4ugbcpdAM)

![不见图 请翻墙](//lh6.googleusercontent.com/c64qY0-kCNWf-g-1x0b7H78tLsv2dluh4G1D6KPrWS6U1JlymF4Mt1dJTFEOptOpaESX9m87WgiuGeFblpz1ZKckYZxI9QCOJkttp7YKAFqdONraCLtr4B2nW20)

　　前面介绍的都是比较常见的配置。搞明白上述这些配置，基本上就可以满足虚拟系统的常规使用了。其它一些配置，要么比较简单（比如：声卡、USB口），要么很少用到（比如：串口、并口），所以今天的介绍就到此为止。

　　大伙儿如果有其它疑问，请**翻墙**[到本文留言](http://program-think.blogspot.com/2012/12/system-vm-5.html)。如果觉得还有哪些配置需要补充，也可以留言告知俺。

[回到本系列的目录](http://program-think.blogspot.com/2012/10/system-vm-0.html#index)

