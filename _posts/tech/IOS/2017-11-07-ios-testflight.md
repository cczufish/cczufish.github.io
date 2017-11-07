---
layout: post
title: testflight 测试app问题汇总
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

1 ‘xxx’ isn't compatible with this device

最近在做ipad app开发，在最近一次把程序发布到testflight上给用户发了邀请码测试的时候，发现20个人有10几个就安装不成功，全部报这个错误，然后就找问题发现，这一次打包的程序只支持arm64，不支持armv7的架构。。。

定为问题找到了然后就重新打包发布，不知道跟我连接的ipad关系大么，港版的ipad，连接其他的ipad就没事。

正确的是这样的

设备要求

最低 iOS 版本 8.0

支持的架构 armv7, arm64

设备系列 iPad

所需性能 armv7

安装不了的是

设备要求

最低 iOS 版本 8.0

支持的架构 arm64

设备系列 iPad

所需性能 arm64






<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


