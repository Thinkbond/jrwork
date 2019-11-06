---
layout: post
title:  谈谈使用 DEVONthink 抓取网页时，选择何种格式
tags:   DEVONthink macOS
date:   2019-10-15 07:06:00
categories: [数字生活] 
---

今天谈谈 DEVONthink 抓取网页的「格式选择」，以便更好地兼容 DEVONthink to Go。

网文抓取最佳格式选择：

- Formatted Note：适用于图片不多（尤其是不大），同时还有移动端添加图片需求的网文。

- Rich Text：适用于多图网文，可以在抓取后展开并批量压缩图片，但不能通过移动端添加图片。

- 不推荐 Webachive，空间占用大，编辑不方便，额外元素较多。

- 无法正常抓取网页时，推荐试试 PDF。

附官方对 RTF 和 Formatted Note的描述：

Rich text and formatted notes
You can view and edit rich text documents (RTF and RTFD) and formatted notes.

RTF and RTFD: Rich text documents use the proprietary RTF format with good but not 100% compatibility to e.g. DEVONthink for Mac. DEVONthink To Go also supports rich text documents with attached images (RTFD) but as read-only.

Formatted notes: Based on HTML, formatted notes are 100% compatible to DEVONthink for Mac and can also displayed using any web browser on any platform. Images that you add are embedded. Formatted notes are fully self-contained.

