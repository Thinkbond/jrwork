---
layout: post
title:  简单两步，有效缩减 DEVONthink 收集的带图文档体积
tags:   DEVONthink 图片压缩
date:   2019-06-02 13:00:00
categories: [数字生活] 

---

当看到有用的资料时，我们总会想要把它保存起来，以供以后查阅。所以网文收集类的工具变得流行起来，从早期的网文快捕、为知笔记再到现在盛行的印象笔记和 DEVONthink，都有着不错的网页捕获体验。
然而，随着网速的提高，人们渐渐习惯了使用高清图文发布内容，使得网页体积越来越大，单张图片甚至超过了 2MB，更不用说 GIF 图爱好者的狂轰滥炸了。虽然机械硬盘已经便宜的像 「白菜」，但多数笔记本电脑配备的固态硬盘仅有 256GB 甚至更少的空间。能省一点是一点，特别是同步到移动端的时候。
本文以 DEVONthink 为例，介绍一种有效缩减图文文档的体积的方法，只需两步：

## 第1步：批量缩放图片尺寸

在 DEVONthink 占用空间较大的 rtfd 文档（通过“Take Rich Note”获取的网页内容）标题上点击右键，选择「Show In Finder」，然后在 rtfd 文档图标继续点右键，选择「显示包内容」即可看到文档中的图片，例如我派一篇[手机摄影](https://sspai.com/post/53005)教程，多达 97 张图片，占用 23.2MB 空间。
![-w494](http://ww4.sinaimg.cn/large/006tNc79ly1g3mq611t2qj30rg0lwgqw.jpg)
此时，只需 `CMD A`全选照片（注意取消选择非图片文件），通过快捷键（个人设置为双击`Fn`）调出 LaunchBar 的 「Instant Send」功能，按`Tab`执行内置缩放图片的 Action 即可完成第一步压缩。
![-w494](http://ww3.sinaimg.cn/large/006tNc79ly1g3mq65s6xlj30rg07ygna.jpg)
缩放比例的选择根据实际情况灵活调整，在不影响观看效果的前提下选择尽量大的比例。

> 当然，如果你没安装 LaunchBar 也没关系，可以使用系统自带的 Automator 来完成，也非常简单。

扩展阅读：[利用 Automator 在 Mac 上快速批量压缩图片](https://sspai.com/post/35488)

## 第2步：利用 ImageOptim 进一步压缩图片

打开 [ImageOptim](https://imageoptim.com/mac) ，全选图片并拖放到 ImageOptim 窗口中，即可自动压缩。
![image-20190602084854241](http://ww3.sinaimg.cn/large/006tNc79ly1g3mq6e9l6qj310q0ny4e4.jpg)
还可以启用「有损压缩」，获得更好的压缩效果。

![image-20190602091539062](http://ww3.sinaimg.cn/large/006tNc79ly1g3mq6igktzj31720s2ahg.jpg)
压缩率对比，使用以上两步操作后，文档体积从 23.2MB 减少到了 7.4MB，效果显著。

| 压缩流程（源文件 23.2MB） | 压缩后 | 压缩率 |
| ------------------------- | ------ | ------ |
| LaunchBar 50% 压缩        | 13.6MB | 58.62% |
| ImageOptim                | 7.4MB  | 54.41% |

不过，如果捕获的是「Web Archive」等 Html 格式的话无法使用本方法，所以，使用 DEVONthink 捕获网文时，推荐使用「Rich Note」而不是「Capture Web Archive」。

> 题图 by Leah Kelley from Pexels