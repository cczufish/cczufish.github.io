---
layout: post
title: swift 关闭侧滑返回手势
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---
戳这里 https://www.jianshu.com/p/fcbde164ee1c


```javascript

// 关闭侧滑返回手势，。
if (navigationController?.responds(to: #selector(getter: navigationController?.interactivePopGestureRecognizer)))! {
navigationController?.interactivePopGestureRecognizer?.isEnabled = false
} 这个不起作用 有人遇到么


// 关闭侧滑返回手势，。
if (navigationController?.responds(to: #selector(getter: navigationController?.interactivePopGestureRecognizer)))! {


for popGesture in (self.navigationController?.interactivePopGestureRecognizer?.view?.gestureRecognizers)! {
popGesture.isEnabled = false
}
}









```









<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


