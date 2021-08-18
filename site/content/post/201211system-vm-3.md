---
layout: default
title: '扫盲操作系统虚拟机[3]&#65306;虚拟机软件的选择'
date: None
author:
    display_name: 
---

　　最近10年来，虚拟化技术发展很快，市面上也冒出了一大堆（至少几十种）的虚拟机软件。所以，在介绍了[虚拟机的应用场景之后](https://program-think.blogspot.com/2012/11/system-vm-2.html)，俺再来介绍一下“如何选择虚拟机软件”。 　　为啥把知名度作为第一筛选标准捏？因为知名度高的软件，用的人通常也比较多。当你使用该软件碰到问题/困难时，也就更容易从网上找到相关的资料。如果是商业软件的话，用的人越多，也就越容易找到破解或者注册码 :-) 　　如今的虚拟机软件，名气比较大的有如下几款（按字母序排列）： KVM、Parallels、VirtualBox、Virtual PC 系列、VMware 系列、Xen 　　接下来再看虚拟机软件支持哪些操作系统。

　　对操作系统的支持包括两个层面：第一个层面是支持哪些 Host OS，第二个层面是支持哪些 Guest OS。**关于 Host OS 和 Guest OS 的概念，[本系列第一篇](https://program-think.blogspot.com/2012/10/system-vm-1.html)已经介绍过，这里就不再啰嗦了。**

　　当今的桌面操作系统，最流行的分别是 Windows、Mac OS X、Linux。考虑到俺博客的读者群，这三种系统的用户都有。所以，本系列推荐的虚拟机最好能在 Host OS 层面和 Guest OS 层面同时支持这三款操作系统。根据这个标准，就排除掉了 KVM、Xen、Virtual PC——因为 KVM 和 Xen 不支持 Windows 作为 Host OS；而 Virtual PC 不支持 Linux 做 Host OS。 　　两轮淘汰下来，剩下三个候选软件：VMware、VirtualBox、Parallels。下面简单介绍一下这三个候选者。  
　　VMware 的官网链接在“[这里](http://www.vmware.com/)”。 　　所谓的 VMware 虚拟机软件，其实是一个很大的家族，成员比较复杂。在这个家族中，面向桌面用户的产品有 VMware Workstation、VMware Fusion、VMware Player。 　　其中的 VMware Workstation 面向 Windows/Linux 用户，VMware Fusion 面向 Mac OS X 用户。至于 VMware Player 要特别说一下：这款软件虽然免费，但功能实在太弱了（连快照都不支持）。不支持“快照”的虚拟机软件，简直形同废物。所以俺就不考虑 VMware Player 了。本文后续部分提到的 VMware，均指 VMware Workstation 和 VMware Fusion。  
　　VirtualBox 的官网在“[这里](http://www.virtualbox.org/)”。 　　在这三个候选者中，VirtualBox 是仅有的开源软件（而且免费）。如果用它的话，你既不用花钱，也不用盗版。别看是免费，功能完全【不】逊色（具体细节后面会介绍）。  
　　Parallels 的官网在“[这里](http://www.parallels.com/)”。 　　Parallels 包括两款软件：Parallels Desktop 面向 Mac OS X 用户；Parallels Workstation 面向 Windows/Linux 用户。 　　这玩意儿的知名度可能不如前两个，但在苹果社区的口碑还是不错滴。据说 Parallels 公司把研发的重点放在 Parallels Desktop，导致 Parallels Desktop 在版本更新、功能、稳定性方面，都比 Parallels Workstation 要好。 　　俺个人觉得，用 Mac OS X 的同学可以考虑试试 Parallels Desktop，至于用 Windows/Linux 的同学，就甭考虑 Parallels Workstation 了。  
　　快照是基本功能，这三款软件自然都支持。而且都支持多层次的树形快照。 　　点评：三者持平 　　这是指在 Host OS 和 Guest OS 之间交换数据。常见的方式有三种：共享目录、共享剪贴板、鼠标拖放。 　　这三款软件同时都支持上述三种方式。提醒一下：VirtualBox 的拖放功能迟至 4.2.0 版本才加入，可能还不太完善。 　　除了上述三种方式，VMware 还支持把 Guest OS 的硬盘文件映射到 Host OS的某个盘符。通过此功能，即使 Guest OS 没有运行，你也可以方便地访问 Guest OS 里面的文件。 　　点评：VMware 占优  
　　所谓“CPU VT”就是在 CPU 硬件层面提供虚拟化相关的指令。利用这些指令，虚拟机软件可以更好、更快地实现虚拟化的功能。更多介绍请看维基百科“[这里](https://en.wikipedia.org/wiki/X86_virtualization)”。 　　目前 x86 芯片的 VT 技术主要是 AMD-V 和 Intel-VT，这三款软件都支持。 　　点评：三者持平 　　VMware 只支持自家的 VMDK 格式。 　　Parallels 除了支持自家的 HDD 格式，还支持 VMware 的 VMDK 格式。 　　VirtualBox 除了支持自家的 VDI 格式，还支持如下几种： VMDK（VMware 虚拟机的格式） VHD, VHDX（VirtualPC 虚拟机的格式） HDD（Parallels 虚拟机的格式） QCOW, QED（QEMU 虚拟机的格式） 　　点评：VirtualBox 占优 　　备注：因为 VirtualBox 支持的格式多，其它虚拟机软件制作的 VM 要迁移到 VirtualBox 会比较容易。 　　这个功能就是把 Host OS 上的光盘镜像文件映射到 Guest OS 的光驱，让 Guest OS 以为这是一张真实的光盘。 　　这三款软件都支持光盘镜像映射。 VMware 支持 ISO 格式 Parallels 支持ISO, DMG, CUE, CCD 格式 VirtualBox 支持 ISO, DMG, CDR 格式 　　点评：ISO 格式属于光盘镜像的事实标准，其它格式用的少。所以三者基本持平 　　“USB 支持”是指虚拟机软件把 Host OS 上的 USB 设备映射到 Guest OS 中。 　　这三款软件都支持 USB，差别在于 USB 的协议。（截至本文发布时）VirtualBox 最新的 4.2.x 版本仅支持到 USB 2.0；而 Parallels Desktop 从今年的 8 版本刚刚开始支持 USB 3.0；VMware 也是在今年发布的 9.0 版本刚刚支持 USB 3.0 　　点评：VirtualBox 落后 　　对于 VMware，在 Workstation 10 之前都没有提供原生的中文版（要靠汉化补丁）。Parallels 有中文版，VirtualBox 的界面内置多种语言，可以动态切换。 　　点评：VirtualBox 占优，VMware 落后。 　　虚拟机软件常用的显示模式有三种：窗口模式、全屏模式、无缝模式。 　　这三款软件同时都支持上述三种模式。

　　**1\. 窗口模式**

　　窗口模式是最基本的显示模式。在这种模式下，整个 Guest OS 桌面显示为 Host OS 桌面上的一个窗口。所有 Guest OS 软件的界面都在这个窗口中。

　　**2\. 全屏模式**

　　全屏模式就是让 Guest OS 独占整个显示器。在全屏模式下，你看不到 Host OS 的桌面。

　　**3\. 无缝模式**

　　所谓“无缝模式”就是：让 Guest OS 里面的软件界面从虚拟机的窗口中“跑”出来，直接融合在 Host OS 的桌面里。这种效果是很酷滴！ 　　这三款软件对“无缝模式”的叫法不同——VMware 称之为“Unity”，Parallels 称之为“Coherence”，VirtualBox 称之为“Seamless”。 　　点评：三者持平 　　这三款软件都有 3D 加速，它们都支持了 OpenGL 2.0（或更高）和 DirectX 9（或更高）。 　　点评：三者持平 　　VMware Workstation 几年前就具有“截屏”和“录像”功能； 　　VirtualBox 只有“截屏”，没有“录像”；Parallels 貌似也没录像功能。 　　点评：VMware 占优 　　所谓远程管理就是：虚拟机软件提供某种方式，让用户可以通过网络远程操作 Guest OS。提醒一下：这种远程操作能力是由虚拟机软件提供的，跟 Guest OS 没有关系。举个例子：你甚至可以远程操作一个 DOS 的虚拟系统。 　　VMware 支持基于 VNC 的远程操作；VirtualBox 支持基于 RDP（远程桌面协议）的远程操作；Parallels 貌似不支持远程操作。 　　点评：考虑到 RDP 比 VNC 普及，所以 VirtualBox 占优  
　　从刚才的“功能对比”，大伙儿应该可以看出，这三个候选者的功能，有些小差异，但没有**实质性**的差异。所以俺再来比较一下性能方面的高低。 　　要测性能，必须在同一台电脑里面，使用相同的 Host OS 环境进行测试，才有可比性。所以俺根据三种主流的桌面操作系统，分别介绍。 　　免责声明：下面列举的性能测评是网上找来的，未必全面，仅供参考。  
　　“[这里](http://www.ptt.cc/bbs/PC_Shopping/M.1349389173.A.450.html)”有一篇台湾同胞做的测评。Host OS 用 Windows Server 2012，Guest OS 用 Windows Server 2008 R2。 　　该测评针对三种虚拟机软件：VMware Workstation 9、VirtualBox 4.2.0、Hyper-V（这里的 Hyper-V 用的是 Windows 2012内置的） 　　测试结果是：Hyper-V 明显好于 VMware Workstation 9，VMware Workstation 9 好于 VirtualBox 4.2.0 　　考虑到 Hyper-V 是 Windows Server 2012 内置的，而且测试方法是 Windows 虚拟 Windows，所以 Hyper-V 的结果未必能说明问题。 　　不过捏，VMware Workstation 9 比 VirtualBox 4.2.0 快，倒是可以说明一定的问题。  
　　“[这里](http://www.macobserver.com/tmo/article/benchmarking-parallels-fusion-and-virtualbox-against-boot-camp)”有一篇很全面的测评，使用 Parallels Desktop 8, VMware Fusion 5, VirtualBox 4 这三款虚拟机软件，在苹果系统中虚拟 Windows。为了提供参照，还特意测试了 Windows 系统直接运行在 Mac 硬件上的性能指标，作为虚拟机性能的对比。 　　从这篇测评的发布时间看（Sep 17 2012）算是比较新鲜的。从测评的综合结果看，Parallels Desktop ＞ VMware Fusion 5 ＞ VirtualBox 4。而且 VirtualBox 4 落后较多。  
　　“[这里](http://openbenchmarking.org/result/1109086-DAIT-MINTVMW79,1109082-DAIT-VIRTUAL59)”有一篇去年（Sep 09 2011）的测评，基于 Linux Mint，测试了 VirtualBox 和 VMware。该测试中，至少有6项指标，VMware 明显好于 VirtualBox；只有一项指标是 VirtualBox 明显好于 VMware。  
　　“[这里](http://luhman.org/blog/2012/05/01/performance-hyper-v-vs-esxi-vs-kvm-vs-virtualbox)”还有一篇半年前（May 01 2012）的测评，对比了4款虚拟机（Hyper-V, ESXi, KVM, VirtualBox），其中的 ESXi 属于 VMware 家族。从这篇测评的结论看，VirtualBox 比 KVM 略好，不如 Hyper-V 和 ESXi。 　　功能上，三个候选者各有胜负，但差别不大。 　　性能上，VirtualBox 在三种系统都不如 VMware；苹果系统上，Parallels 明显占优。虽然 VirtualBox 性能不够好，但它是开源软件，无需花银子。 　　俺的建议是： Windows 的用户，在 VMware Workstation 和 VirtualBox 二选一（Parallels Workstation 用的人太少，明显不给力，不予考虑）。 Mac OS X 的用户，在 Parallels Desktop 和 VirtualBox 二选一（苹果系统的 Parallels Desktop 比 VMware Fusion 好，价格还便宜，于是排除掉 VMware Fusion）。 Linux 的用户，在 VMware Workstation 和 VirtualBox 二选一（如果你是铁杆 Linux 用户，这辈子铁定不用其它 OS 做宿主，或许也可以考虑 KVM 或 Xen）。

[回到本系列的目录](https://program-think.blogspot.com/2012/10/system-vm-0.html#index)

