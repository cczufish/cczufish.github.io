---
layout: post
title: iOS的Library/Cache目录内容会被删除
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---


```javascript

网上搜索基本的都是说这个目录的内容不会被删除，只是不会被icloud备份而已。
之前的同事将下载的文件放到了Library/Cache目录，之前只是觉得有点奇怪，也没太在意，于是我就背锅了。生产环境偶尔出现用户数据全丢的情况，发现是数据被删除了。再查一下官方文档：

https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html





```









<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


