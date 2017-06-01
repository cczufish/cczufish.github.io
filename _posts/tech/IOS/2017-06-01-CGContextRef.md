---
layout: post
title: 用CGContextRef绘制基本图形
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

 用CGContextRef绘制基本图形


```javascript

- (void)drawRect:(CGRect)rect
{
CGContextRef ctx = UIGraphicsGetCurrentContext();     //获得当前画板
CGContextAddRect(ctx, rect);    // 画矩形
CGContextSetFillColor(ctx, CGColorGetComponents([self.bgColor CGColor])); //填充颜色
CGContextFillPath(ctx);  //设置填充的路径

}



CGContextAddEllipseInRect // 画椭圆

CGContextAddArc  // 画圆


```






<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


