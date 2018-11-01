---
layout: post
title: 去掉UINavigationBar底部的分割线
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---


```javascript

// 去掉UINavigationBar底部的分割线

//导航栏背景透明
self.navigationController?.navigationBar.setBackgroundImage(UIImage.init(), for: .default)
//导航栏底部线清楚
self.navigationController?.navigationBar.barStyle = .black;
self.navigationController?.navigationBar.isTranslucent = true;
self.navigationController?.navigationBar.shadowImage = UIImage.init()



```









<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


