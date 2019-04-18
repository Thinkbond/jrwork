---
layout: post
title:  DIY「NAS」，低成本打造家庭数据管理系统
tags:   NAS 数据管理 DIY
date:   2019-03-4 22:25:35 +0800
categories: [数字生活] 
---
> 看到标题，估计你会认为这是又一篇黑*晖文，nonono，本文所述的「低成本」，不仅仅是硬件购入成本低，搭建难度也相对较低。

## 1 写在前面

本文目的是充分利用已有资源的前提下，购入基本的设备将现代家庭中必不可少的电子数据（照片、视频、音频、文档、软件等）管理起来，包括数据的输入、存档、取用及备份归档。先来看一下家庭数据管理的整体框架：

![img](https://ws4.sinaimg.cn/large/006tNc79ly1g26yafy27aj30md0d1jw4.jpg)

首先，一般家庭都已配备了电视、电脑（PC）、笔记本电脑、手机以及路由器（虽然有可能不满足要求而需更换），整套方案一般仅需要新购入用于存储数据的容器——硬盘以及必要的几款软件。

其次，本套方案也不需要多少知识储备，会用电脑，**懂搜索**即可。

## 2 实现原理

使用支持外接硬盘的路由器作为管理中枢，通过网线和无线与家庭常用数码产品实现数据互通、流转、备份、归档的目的。搭建完成后，主要价值体现在如下场景：

- 平时使用相机、手机拍摄的照片、视频只需像平时一样拷贝到家里的 PC 中，照片会自动被传送入主硬盘（与路由器连接的）中存档。
- 打开电视，随时可以观看之前在 PC 上使用迅雷下载的视频以及自己拍的照片。
- 16G 存储空间的手机里拍了很多张照片，无需担心会很快爆仓，后台会原原本本地把照片上传到「完全属于自己」的硬盘中。
- 辛苦做的文档，再也不用心惊胆战地按无数次 “Ctrl-S”，电脑会自动存档多个拷贝到硬盘中。
- 用于存储数据的硬盘难免会有一天会崩溃，没有备份怎么行，只需设置一个提醒，定期将外置移动硬盘插入 PC ，无需任何操作，即可实现数据同步。

相信不少朋友感受过文件数据丢失的烦恼吧，手机里照片不见了，电脑中的文件被误删了等等。为了避免文件丢失，需要采用科学的备份方式。关于备份，**「3-2-1 原则」**扩展了解一下：

「3-2-1 原则」是一种久经考验且直观易行的方法，文件备份时的具体规则如下：

- 3：存储 3 份完整的文件，一份原件加上两份拷贝。
- 2：将文件至少保存在两种不同的介质上（比如两块硬盘，注意尽量避免使用同一批次买入的硬盘，避免同时出现故障，虽然几率较低）。
- 1：将一份拷贝保存在异地，比如办公室、值得信懒的朋友家等。

## 3 资源准备

### 硬件资源

- 支持 USB3.0 接口的千兆无线路由器，建议华硕、网件等可刷梅林固件的产品。例如本文中使用的[华硕 RT-AC68U](https://item.jd.com/1035733.html)，支持 2 个 USB 口，802.11ac 无线协议。
- 硬盘 ≥ 3 块，建议至少选一块 3.5” 机械硬盘，因具有独立供电可提高硬盘数据的安全性，作为主硬盘的容量建议 2T～4T （根据路由器最高支持容量选择，AC68U 最高 4T），其他硬盘大大宜善。
- 硬盘盒 ≥ 2，也可采用 1 个硬盘盒加 1 个硬盘底座的方式，用于搭配安装硬盘。
- 一台 PC，可以是家里闲置的台式机或笔记本，能联网有一定可用存储空间即可。
- 一台大屏智能电视（可选），主要用于安装 Kodi 观看硬盘中的影片或照片。

### 软件资源

- [Goodsync](https://www.goodsync.com/cn) 实现各种软硬件互通的纽带，虽然免费版也能实现「半自动」同步，但还是付费版用起来爽。
- [Kodi](https://kodi.tv/download) 支持全平台的免费媒体播放器，本文主要用到 [Kodi 电视版](https://kodi.tv/download)（安卓系统），请根据电视的处理器平台选择，比如 ARM v7 或 v8，目前最新版本是 18.1，推荐 17.6 版，除非您的电视是最新款。
- [FolderSync](https://play.google.com/store/apps/details?id=dk.tacit.android.foldersync.lite&hl=en_US) 可实现安卓手机/平板全自动按计划频率增量上传照片至 「NAS」的硬盘中。
- [Ext2Fsd](http://www.ext2fsd.com) 是一款免费的能够让 Windows 系统读取 etx3/ext4 文件系统的驱动。可以查看和复制文件及文件夹。——备选，防止紧急需要拷贝主硬盘（Linux 分区）中的数据。

## 4 环境搭建

### 硬件连接

- 将新购入的 3.5“ 硬盘装入硬盘盒中，在格式化 ext3 格式并拷贝家庭数据后接入路由器 USB 3.0 端口（蓝色）；
- 将电视、电脑分别使用网线与路由器 LAN 口连接，这么做的目的是保证数据传输的稳定性且减少无线路由带宽占用；
- 笔记本电脑、手机、iPad 等连接家中的 Wi-Fi；

### 软件安装

- PC：安装 GoodSync；
- 电视：安装 Kodi；
- 手机：安装 FolderSync；

### 准备主硬盘

**制作 Live 版 Linux 启动 U 盘**，需要用到的工具有：

- [Etcher](https://www.balena.io/etcher/?ref=etcher_menu) 或者其他可以将 ISO 格式文件烧录到 U 盘的工具
- U 盘，容量大于 2GB
- 下载Linux 镜像（本文以 [elementary OS](https://elementary.io) 为例）

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26ya92fefj31eo0rcahj.jpg)

将 Linux 镜像烧录至 U 盘中，然后使用该 U 盘启动 PC 至 Linux 环境下，将要作为主硬盘使用的硬盘连接至 PC 。打开系统自带的磁盘管理工具，将主硬盘格式化为 ext3 格式。

为什么需要格式化成 ext3 而不是常见的 NTFS？

因为一般路由器系统均对 Linux 友好，虽然很多也支持 NTFS，但根据本人多年经验，NTFS 不那么稳定而且连接路由器使用时，性能较低。下图是使用 NTFS 格式时，路由器管理页面总是提示硬盘存在错误。

![img](https://ws4.sinaimg.cn/large/006tNc79ly1g26yaabqhyj30hs0j0425.jpg)

另外，不使用最新的 ext4 格式是因为 AC68U 不识别。

回到正题：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1g26yam6c0cj30lm0evmyy.jpg)

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26yaouvxmj30jg07b3yo.jpg)

如图所示，将硬盘格式化成 ext3 格式，别急着退盘关机，还需要调整一下磁盘权限，不调整的话，下一步会出现**数据无法写入硬盘**的故障，当你打开磁盘属性时会看到类似下图的信息：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1g26yaf15bdj30cy0gpgm0.jpg)

磁盘处于只读状态，一劳永逸的调整权限其实很简单，只需打开系统自带的终端（Terminal），输入 `sudo chmod 777 /media/elementary/NAS` （其中 “/media/elementary/NAS” 是当前硬盘挂载的路径，应根据实际情况填写）

![img](https://ws2.sinaimg.cn/large/006tNc79ly1g26yae7e3mj30n708oq45.jpg)

运行结束后再看磁盘属性，已经改为了可读写状态。

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26yajc0ykj30cy0gp3z0.jpg)

将现存的数据拷贝至主硬盘中

![img](https://ws1.sinaimg.cn/large/006tNc79ly1g26yacbihtj30iu080t8r.jpg)

完成后，推出硬盘并将其接入路由器的 USB 3.0 接口。

### 设置路由器

进入路由器后台管理页面，会在主页看到硬盘状态，已挂载且健康度正常。

![img](https://ws1.sinaimg.cn/large/006tNc79ly1g26yah0no8j30tc0uqafo.jpg)

点击左侧的 USB 相关应用，打开「服务器中心」。

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26yalct2qj31ee0u0wuy.jpg)

依次打开 Samba 共享（用于同步操作及一般数据共享）和 FTP （用于手机端 FolderSync 上传照片）

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26yad6txbj311g0u0tf8.jpg)

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26yabv7knj30v80pcgpi.jpg)

如果需要对手机端访问权限进行更加精细的管控，可以新建一个照片备份专用账户，只分配「照片」目录的读写权限。

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26ya7qvyyj312w0q0wi8.jpg)

除了文件共享以外，根据需要还可以进一步设置家庭打印机共享、脱机下载及 Macbook 需要的备份服务： Time Machine 。

![img](https://ws1.sinaimg.cn/large/006tNc79ly1g26yapygxvj30u00v1tif.jpg)

以设置  Time Machine 为例，建议空间设置为笔记本硬盘同样大小，避免浪费过多主硬盘空间。

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26ybxj9h0j316a0pgqaf.jpg)

Macbook 端设置，选择位于路由器上的主硬盘；

![img](https://ws2.sinaimg.cn/large/006tNc79ly1g26yc0lsxxj316e0u0whb.jpg)

输入路由器管理员名称及密码即可正常进行备份。

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26yais3xhj30u40hqjw2.jpg)

至此，路由器设置完毕，如果主硬盘中已拷贝了数据，正常应该是如下界面：

![img](https://ws2.sinaimg.cn/large/006tNc79ly1g26yaka48oj30nc0myn1i.jpg)

### PC 端设置

根据文件分类，分别设置不同目录的同步规则，一般选择双向同步，自动运行参数设置如下，可根据需要灵活调整。

![img](https://ws4.sinaimg.cn/large/006tNc79ly1g26yanyd9sj30hy0iggml.jpg)

如果一切正常的话，就可以静待其自动完成剩下的工作了：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1g26yafgntcj311y0k8dk0.jpg)

同样道理，可以设置路由器上的主硬盘与移动硬盘、主硬盘与 PC 硬盘等存储设备进行同步，分享一个小技巧：由于一般 PC 自带硬盘大小有限，对于视频等空间占用较大文件，如何避免占用本地空间。以迅雷下载的视频为例，设置一个自动同步规则，在过滤器中添加常见的视频格式类型，例如 `*.avi` `*.mkv` `*.mp4`等，并将模式设置为「移动模式」，即可在文件同步至主硬盘后自动删除本机文件。

### 手机端 FolderSync 设置

添加之前在路由器中添加的 FTP 账号和密码；

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26yahxzf2j30u01hc0va.jpg)

设置同步文件夹，安卓手机一般是 DCIM 目录；

![img](https://ws2.sinaimg.cn/large/006tNc79ly1g26ya9kyeyj30u01hcn0d.jpg)

以下是为确保顺利同步需要的必要设置，篇幅关系就不展开讲了。

![img](https://ws4.sinaimg.cn/large/006tNc79ly1g26ycev3jtj30u01hctbm.jpg)

![img](https://ws3.sinaimg.cn/large/006tNc79ly1g26yamz7ynj30u01hctca.jpg)

### 电视端设置

电视中安装 Kodi 后可参考少数派中一篇文章的做法：[安装 Kodi 展示播放 NAS 电影](https://sspai.com/post/53069) 。

### 结尾 

最少仅需要投入 1～2 块硬盘的成本及大约半天的时间，即可基本实现至少数千元「NAS」的效果，何乐而不为呢？