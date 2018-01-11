---
layout: post
title: ipad侧滑白屏，禁止侧滑返回手势
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

plist文件中添加下面2个

```javascript


- (void)viewDidAppear:(BOOL)animated
{
[super viewDidAppear:animated];
// 禁用返回手势
if ([self.navigationController respondsToSelector:@selector(interactivePopGestureRecognizer)]) {
self.navigationController.interactivePopGestureRecognizer.enabled = NO;
}
}


- (void)viewDidLoad {

[super viewDidLoad];
self.navigationController.interactivePopGestureRecognizer.enabled = NO;

id traget = self.navigationController.interactivePopGestureRecognizer.delegate;
UIPanGestureRecognizer * pan = [[UIPanGestureRecognizer alloc]initWithTarget:traget action:nil];
[self.view addGestureRecognizer:pan]; // 一定要加在view上

}




```









<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


