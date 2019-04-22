---
layout: post
title:  如何为「高冷异常」的 Rime 添加双拼方案
tags:  双拼 输入法
date:   2019-04-23 6:45:35 +0800
categories: [数字生活] 

---

## Rime 升级后变的「高冷异常」

> 适用于兼容 Windows 10 的小狼毫 0.13.0 或更新版

为了在 Windows 10 下与家人共用电脑，需要将自己偏好的双拼方案与家人习惯的全拼共存。但又不想使用流行的「流氓」输入法。

> 如果只使用双拼方案的话，可以用[本方法](https://ifttl.com/add-flypy-to-win10-microsoft-pinyin-and-other-configuration/)，快速设置系统自带方案为小鹤双拼。

### 具体设置方法

首先在开始菜单中找到小狼毫的【输入法设定】工具

![3](Rime 升级后变的「高冷异常」.assets/3.PNG)

点击下部的“获取更多输入方案”，会看到如下命令行界面：

![2](Rime 升级后变的「高冷异常」.assets/2.PNG)

注意：想使用双拼输入法的话，就输入`double-pinyin`，而不是`double_pinyin` 抑或`double_py` 甚至`double_pinyin_flypy`…… 

当你想要质疑，小狼毫输入法为何越更新越「倒退」的时候，作者早回答了：

![1](Rime 升级后变的「高冷异常」.assets/1.PNG)

只能表示无语，不过话说回来，不能用着别人的东西还嫌弃不是？毕竟这是一次性操作。



##### 定制顿号

欲令 `/` 鍵直接輸出「、」，可如此定製 `luna_pinyin.custom.yaml`:

```
patch:
  punctuator/full_shape:
    "/" : "、"
  punctuator/half_shape:
    "/" : "、"
```