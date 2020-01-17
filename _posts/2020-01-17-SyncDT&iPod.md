---
layout: post
title:  妙用 NAS 服务，将你的知识库和音乐库搬上「云」
tags:   效率应用
date:   2020-01-17 20:06:00
categories: [数字生活] 
---

想必你也遇到过这样的问题：

- 资料库体积越来越大，内置硬盘的容量却没有跟着长大或者不方便扩容；
- 平时需要在多个终端（电脑/手机/iPod 等）共享 APP 自有的「资料库」，例如 DEVONthink 和 Evernote 的 Database、音乐 app（iTunes）的 Music Library 等，但 App 默认数据存放路径在本地或同步方式不稳定，导致各个终端之间数据同步出错，处理起来不仅麻烦还容易丢失数据。

对于我来说，具体体现在如下两个场景：

- 平时使用 DEVONthink 作为知识库管理工具，需要笔记本、台式机和手机之间能够自动进行数据交换以保持一致。起初使用 DEVONthink 内置的 iCloud 进行同步，但经历过多次同步失败、报错后终于下定决心要解决。鉴于个人的网络环境限制，剩下能选的就是 Bonjour 和 WebDAV，Bonjour 只能点对点同步，三个及以上终端就有点麻烦了，所以只有自建 WebDAV 这一个选项（坚果云虽然有 WebDAV，但有诸多限制，并不能胜任）。
- 目前出门随身携带的播放设备是古早的 iPod classic，我希望通过 iPod classic 随时同步新买或转录的音乐，同时能够把播放数据（播放次数、星级评价等）回传给电脑，以便维护属于自己的离线音乐库，但它只能与同一个 Music Library（资料库）同步，否则就会被后同步的音乐 app（iTunes）抹掉，导致重来一遍。而且随着不断的积累，电脑可用空间越来越小。

### 把知识库搬上「云」

#### 解决思路

结合现有条件，我可以在群晖中建立 WebDAV 服务，通过 WebDAV 将桌面端的 DEVONthink 与手机端的 DEVONthink to go 进行数据同步。

> WebDAV 是一个 HTTP 的扩充服务，可让用户编辑和管理存储在远程服务器上的文件。通过 Synology DiskStation Manager 的 WebDAV 服务，支持 WebDAV 的客户端程序（如 Windows 资源管理器、Mac OS Finder、Linux 文件浏览器）将能够远程访问 Synology NAS，如同访问本地网络硬盘。
>
> 本方法适用于拥有 NAS 的朋友，实测入门版配置即可，本人使用 7 年前发布的 DS213+，在进行数据同步时，CPU 和内存占用都在30%以内。经 @Brick73 提醒，如果是自建 NAS 的小伙伴可以考虑使用万由的 NAS 系统，免费且能满足基本需求。
>
> 由于我个人没有太多远程同步的需求，本文仅介绍了「局域网」内的方法，若要实现远程访问，请参考具体NAS 的帮助文件进行，例如群晖可以使用 QuickConnect，为了提高速度可能还要与运营商打交道。
>
> 注意：由于 DEVONthink 数据库的特殊性，请不要依赖 WebDAV 进行资料库的备份，需要用定期拷贝 *.dtBase2 的方式进行备份。

#### 实现步骤

##### 配置 WebDAV 服务

进入群晖的管理页面，打开套件中心，搜索 WebDAV Server 并安装。
![1安装WebDAVServer](https://tva1.sinaimg.cn/large/006tNbRwly1gazsxtx1l4j30yp0u0aav.jpg)

打开 WebDAV Server 套件，启用 HTTP 或 HTTPS，对于需要外网访问的朋友请一定要使用 HTTPS，但必须先从 Synology NAS 导出有效的 SSL 证书，然后将该证书导入客户端设备才能访问 WebDAV 服务。具体为：在 WebDAV Server 套件中勾选「启用 HTTPS」，然后进入**控制面板** > **安全性** > **证书**来创建和导出证书。我只在本地局域网中使用，所以使用 HTTP 就够了。
![2启用WebDAV服务](https://tva1.sinaimg.cn/large/006tNbRwly1gazsxygv74j31h30u0q3u.jpg)

接下来，需要在 NAS 中建立一个共享文件夹，用于存放同步的数据。在这里，我创建了「DEVONthink」共享文件夹并分配了权限。
![创建DEVONthink共享文件夹](https://tva1.sinaimg.cn/large/006tNbRwly1gazsy301c4j30ss0b0jrj.jpg)

设置 macOS 端 DEVONthink，**Preferences** > **Sync** > **Locations** 此时同步选项中会出现刚才设置好的 WebDAV，点击并将路径、登陆用户名和密码填写完成即可。这里有两个地方需要注意：1. 「URL」栏除了填写 NAS的地址外，还需在后面添加新建的共享文件夹路径；2. 「Sync Store Name」 会影响你存入NAS的数据库名称，可随意命名，本例中，会在 NAS 创建「DEVONthink.dtCloud」资料库。

![设置macOS端DEVONthink](https://tva1.sinaimg.cn/large/006tNbRwly1gazsy6v86fj30w80oaq7y.jpg)

设置 DEVONthink to go，点击右下角按钮进入 Settings ，选择「Locations」，此时会自动在底部找到刚才创建的 WebDAV 网络，点击选择，并填入 macOS 端一样的信息，最后点击「Save」。
![设置DTTG1](https://tva1.sinaimg.cn/large/006tNbRwly1gazsyc4qgkj30yp0u0juo.jpg)

接着点击创建好的 Location，勾选需要同步的数据库，本例中是「Global Inbox」和「Personal」即可。
![设置DTTG2](https://tva1.sinaimg.cn/large/006tNbRwly1gazsyhkp5pj30yh0u00v3.jpg)

之后会立即进行同步，由于是局域网，速度非常快，本人近两千条内容 5分钟内即完成了同步和索引过程。
![设置DTTG3](https://tva1.sinaimg.cn/large/006tNbRwly1gazsynbx6wj30xr0u0adc.jpg)

至此，所有准备工作完成，可以享受到畅快稳定的同步服务了。像知识库这种同步时效性要求不高的应用，基本可以忽略掉不能远程访问带来的遗憾。

### 把音乐库搬上「云」

#### 解决思路

先说一下为什么都 2020 年了，还要保留离线音乐库。虽然如今的在线流媒体服务已经非常好用且看起来价格也可以接受。但基于以下原因，我暂时还不会以在线流媒体音乐服务为主：

- 版权分散：目前流行的 Apple Music、QQ 音乐、Spotify、网易云音乐以及虾米音乐等服务，各具特色，拥有的音乐版权也各有侧重，使得听歌杂食风格的我使用起来有很明显的割裂感，况且分散在各处的云端歌曲加上以前积累的转录或下载的离线歌曲，管理起来也非常麻烦。
- 成本考量：除了 Apple Music 和 Spotify 以外，其他几家在付费方面存在各种套路，买了 VIP 包月还不算，大部分热歌、新歌还需要单独购买，无形中堆高了本就不经常使用的听歌成本。
- 音乐库体验：使用音乐 app（iTunes）统一管理歌曲，我可以得到信息丰富的「个性化」音乐库，比如我可以给每首歌打上星级（通过 iPod classic），统计播放次数，使用音乐 app 统计每首歌的播放次数等，逐步完善听歌的「智能化」程度。况且，我的 iPod classic 是完完全全的离线设备（连蓝牙都不支持 :( ），只能用来听离线音乐和**播客**。没错！我一直坚持使用 iPod classic 的另外一个原因就是可以在同步音乐的同时，将最新的播客同步进去，比如「一派」等优质播客）。

实现方法很简单，把所有音乐导入至音乐 app，把整个音乐资料库迁移到 NAS 中，然后通过 afp 或者 smb 协议访问，做到多端共用一个资料库。同时，无论哪台电脑与 iPod 同步都可以。

##### 迁移音乐资料库

将从 iTunes Store 下载的 AAC 和从 CD 转录而来的 ALAC 统统放一起，然后可以在 `～用户名/Music`目录下找到名为「Music」（iTunes 下为「iTunes」）的文件夹，将其整个拷贝至 NAS 的「Music」共享文件夹中。

##### 设置音乐 app

为避免第一次设置失败，建议先使用 Finder 连接一次 Music 共享文件夹。打开 Finder ，**前往** > **前往文件夹** ，输入 NAS 地址（在这里我开启了 afp 协议，也可以用 smb 代替），登录即可。
![连接NAS](https://tva1.sinaimg.cn/large/006tNbRwly1gazsyr06umj31kb0o6af9.jpg)

按住 Option 键的同时，点击音乐 app 图标，点击「选取资料库」，浏览到刚刚打开过的 Music 文件夹，选择「Music Library.musiclibrary」这个音乐资料库配置文件并打开。
![选取资料库](https://tva1.sinaimg.cn/large/006tNbRwly1gazsyv32wmj310u0r40wf.jpg)

稍等片刻，即可像在本地一样使用音乐 app 了，实测本地局域网内播放或导入音乐完全无压力。
![音乐APP](https://tva1.sinaimg.cn/large/006tNbRwly1gazsz0fl9gj31940u01kh.jpg)

##### 同步使用

最后，将 iPod 接入任意一台电脑，等待同步完成，一台存放着自己所有音乐库的离线播放设备就准备好了。
![与iPod同步](https://tva1.sinaimg.cn/large/006tNbRwly1gazsz5w3ccj30u0140gsb.jpg)

这台 iPod classic 三代已更换了大容量电池和固态硬盘，完全装的下我的音乐库（毕竟穷）且能接近一个月不需要充电，完美解决了我的离线听音需求。