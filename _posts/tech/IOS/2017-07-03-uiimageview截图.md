---
layout: post
title: ios截图保存本地相册
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

ios截图保存本地相册

```javascript


UIGraphicsBeginImageContextWithOptions(self.whiteboardVC.docView.bounds.size, NO, 0);
CGContextRef ctd = UIGraphicsGetCurrentContext();
[self.self.whiteboardVC.view.layer renderInContext:ctd];
UIImage *image = UIGraphicsGetImageFromCurrentImageContext();
UIGraphicsEndImageContext();

UIImageWriteToSavedPhotosAlbum(image, self, @selector(image:didFinishSavingWithError:contextInfo:), nil);


```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


