---
layout: post
title: calculateLabelHeightWithString
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

calculateLabelHeightWithString


```javascript

//计算cell label 等行高

- (NSInteger)calculateLabelHeightWithString:(NSString *)string
{
NSMutableParagraphStyle *paraStyle = [[NSMutableParagraphStyle alloc] init];
paraStyle.lineSpacing = 3;
CGSize size = [string boundingRectWithSize:CGSizeMake(_screenWidth-40, MAXFLOAT)
options:NSStringDrawingUsesLineFragmentOrigin
attributes:@{ NSFontAttributeName : [UIFont systemFontOfSize:13], NSParagraphStyleAttributeName : paraStyle }
context:nil].size;
return (NSInteger)(ceilf(size.height));
}







```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


