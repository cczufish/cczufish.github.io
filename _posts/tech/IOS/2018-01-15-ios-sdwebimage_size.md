---
layout: post
title: SDWebImage获取网络图片的size
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---


```javascript


SDWebImageManager *manager = [SDWebImageManager sharedManager];

//  判断是否有缓存
[manager diskImageExistsForURL:imageUrl completion:^(BOOL isInCache) {
UIImage * image;
if (isInCache) {
image = [[manager imageCache] imageFromDiskCacheForKey:imageUrl.absoluteString];
//                    NSLog(@"有缓存");
}else{
//                    NSLog(@"没缓存");
NSData *data = [NSData dataWithContentsOfURL:imageUrl];
image = [UIImage imageWithData:data];
}
CGSize gsize = image.size;
//                NSLog(@"image 宽%g  高%g  isInCache %d",gsize.width,gsize.height,isInCache);



}];



```









<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


