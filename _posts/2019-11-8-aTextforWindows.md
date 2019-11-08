---
layout: post
title:  Windows 文字效率工具有了新选择：aText
tags:   效率应用
date:   2019-11-08 20:06:00
categories: [数字生活] 
---

## Windows 文字效率工具有了新选择：aText

aText 是什么？简单说，就是通过自动替换常用文本，大大缩减你的键盘敲击数，从而节约生命的应用。正如 [aText 官网](https://trankynam.com/atext/)的 slogan（下图）一样，aText 的价值体现在：轻松地解决「重复录入」的问题，节约你宝贵的时间。 ![aText-slogan](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwjqt45j310q08g74a.jpg) 说是「新」选择，是因为相比 TextExpander 来说，aText 并未被大家所熟知，其实 aText 早在 2011 年就发布了 1.0 版。2019 年 8 月推出了**用于 Windows 的**0.1 测试版，目前已更新到 0.60 版，个人经过一周的试用，自认已经达到了日常可用的状态。 效率存在于生活工作中的各个角落，一种比较好的方式，就是先记录短期内的时间都花费在哪里，然后去针对每一项重复动作分析提高效率的方法。作为经常使用键盘录入的我来说，会非常高频的遇到需要录入重复内容的情况，比如邮寄地址、网址、电话、回复相对固定模式的邮件，以及整理、重命名文件等等。「消除重复劳动」在现代社会变得越来越重要。今天我们就以消除重复录入为例，介绍一下 aText for Windows（beta）。

### aText 能做什么？

首先我们来看一下 aText for Windows 的设置界面，甩开 macOS 版好几条街，两者一起对比，高下立判： ![settings](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwkmxd4g30lu0gjq9v.gif)

![aTextformacOS](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwlc493j30yd0u0q9a.jpg)

#### 基本功能

通过输入几个字母/符号的方式快速录入内容，包括但不限于整段（可格式化）的文字、图片、链接、邮件签名等。

- 基本片段 ![1-basi](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwlqlnkg30i30ba3z9.gif)
- 需要按下空格或回车键才会触发的 Snippet ![2-thankyou](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwm6hplg30ep042749.gif)
- 插入箭头  ![3-arrows](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwmojnrg30bq02hgld.gif) 
- 插入时间  ![4-Time](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwniycig30bq0473yr.gif) 

#### 完形填空

适用于一大段固定文本中有个别变量的情况，例如范式邮件中，一般只需要修改收件人姓名。 ![5-Field1](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwojoi1g30en0bmmxu.gif) 再比如数学计算或英语完形填空： ![5-Field2](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwp0ow7g30en0b7t8u.gif)

#### 执行脚本

可以快速执行预设脚本，输出想要的内容。比如快速计算一个随机密码： ![6-Script](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwpxtgng308w031q2s.gif) 执行更加复杂的脚本： ![6-Script2](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwqx6tfg30ho0bot9b.gif) Snippet 编辑页面支持各种格式及语言： ![edit](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwrq8o6g30lm0bo40f.gif)

#### 自动拼写更正（英语）

有了它，再也不用担心写英语时的拼写错误了。 不同于 Word、Pages 等文本处理软件自带的拼写更正功能只能在本软件内应用，使用 aText 可以在「所有」支持文本录入的界面实现自动拼写更正。

### 我的应用举例及 Snippets 分享

日常使用过程中，我除了用 aText 快速录入收件地址、邮箱等内容外，还有更多有意思的应用场景。接下来，我将结合自己经常使用的几个应用场景，分享我的 Snippets 设定，并提供配置文件下载，以便帮你更加轻松地理解和掌握 aText 的用法。个人认为，「模仿」是学习成本最低的一种方式，毕竟我们使用效率工具的目的是为了提高效率，消除重复性劳动，简单粗暴的拿来主义未尝不可。

#### 插入多行格式化文本

只需**输入「;mcsm」**（不含括号，下同）即可快速获得格式化的多行文字。 ![input](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvws7xq9g30py0lywi2.gif)

#### 标准快速地录入专有名词和特殊符号

只需**输入「tc;」**，即可自动插入「Total Commander」。 ![name](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwt7bbvg30hy062t8o.gif) 范例下载：[Names](https://github.com/Thinkbond/profiles/blob/master/aText snippets/Names.atext) [特殊符号](https://github.com/Thinkbond/profiles/blob/master/aText snippets/Symbols.atext) 

#### 文件/文件夹命名

日常整理文件除了设定命名规则比较费心以外，也是一件重复性劳动，我们把「重命名」这项**重复又不好记忆**的工作交给 aText 来做，只需在保存文件时**输入「.fbn」**，勾选大类并自动插入「年月」，最后填上必要的信息回车即可得到预先定义的名称。 ![filename](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwtm6zeg30nh0ia0v5.gif) 范例下载：[File Name](https://github.com/Thinkbond/profiles/blob/master/aText snippets/File Name.atext) 

#### 统一各类编辑器中的 MarkDown 快捷键

支持 MarkDown 的编辑器数不胜数，但对影响写作效率的快捷键的处理并没有一个统一的标准，导致因为某种原因更换编辑器时需要重新适应新的快捷键。其实，我们可以反过来想，为什么非要被动接受不同开发者预置的快捷键呢？我们可以通过某种方法实现全平台统一，也许有人知道 macOS 平台下有著名的 Keyboard Maestro 可以「重定向」菜单的快捷键，但使用起来门槛有点高。针对 MarkDown 我们完全可以使用 aText 预置标准 MarkDown 语法的 snippets 来达到**不再依赖编辑器设定**的效果。 例如，我们要插入一段链接，只需要**输入「url`」**即可自动插入剪贴板中的链接，并能**将光标定位到链接描述处**，流畅自然。 ![url_markdown](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwu673kg30ni0iat9v.gif) 范例下载：[MarkDown](https://github.com/Thinkbond/profiles/blob/master/aText snippets/Markdown.atext) 

#### macOS 与 Windows 互通 snippets

本人使用 aText for macOS 已有很多年，储备了大量 snippets，aText 也适时更新了 macOS 版使其能够导出 json 格式供 aText for Windows 使用。 ![atextfromMa-w365](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwv075ej30ka0jewgv.jpg) 使用 aText for Windows 的菜单「文件」->「打开」得到的「aTextData.json」即可导入使用，对于单个 Snippets Group 的导入需要注意，选择「导入」将会保留原 snippets ，选择「恢复（restore）」将会清空所有 snippets。 经过多次测试，目前导入 macOS 的 snippets 后，个别 snippet 会出现一些小问题，比如菜单变成文本等情况，应该是测试版存在的 bug。

### 小结

aText 自从推出 Windows 版之后，可用性已大大提高，化解了 Windows 平台中文本输入效率软件只有 TextExpander 可选的尴尬。 在这里把典型的几款具备同类功能的 App 进行简单对比如下图所示： ![compare-w490](https://tva1.sinaimg.cn/large/006y8mN6ly1g8qvwvifs3j30r80dygm3.jpg) 若要求全平台制霸和性能，只有 TextExpander 可选（Linux 用户可以使用 Chrome 版替代），但对于平时主要使用 macOS 和 Windows 双平台工作的用户来说，aText 会是一个性价比颇高的选择。TextExpander 虽然支持 iOS 和 iPadOS，但对于主要使用中文键盘的用户并不方便，支持 TextExpander 集成的第三方 App 也较少，个人比较常用且支持的有 Drafts 和 DEVONthink 。对于已经有了 Keyboard Maestro 且具备一定动手能力的用户，不再购入其他 App 也是不错的选择。

```
- 目前测试版提供免费试用，无任何功能限制，感兴趣的朋友可去官网下载尝试。
- 题图来自 Pixabay，配图均已压缩方便您剪藏使用 ：）
```