---
layout: post
title: tableViewCell调整其中自带的imageView的大小
category: 技术
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

//调整cell.imageView大小
let itemSize = CGSize(width: 22, height: 22) //希望显示的大小
UIGraphicsBeginImageContextWithOptions(itemSize, _: false, _: UIScreen.main.scale)
let imageRect = CGRect(x: 0.0, y: 0.0, width: itemSize.width, height: itemSize.height)
cell.imageView?.image?.draw(in: imageRect)
cell.imageView?.image = UIGraphicsGetImageFromCurrentImageContext()
UIGraphicsEndImageContext()


```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

