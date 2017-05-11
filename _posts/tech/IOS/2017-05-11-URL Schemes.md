---
layout: post
title: URL Schemes 简介
category: iOS
tags: iOS,URL Schemes，os x
description:
---

URL Schemes 简介

苹果是用沙盒来保障用户的隐私和安全，app之间不能相互访问数据，这个时候URL Scheme是为方便app之间互相调用而设计的。URL Scheme就是一个可以让app相互之间可以跳转的协议。要跳转到别人的app，就要知道别人app的跳转协议是什么，需要什么参数。

比较常见的打开系统App：

    [[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"mailto://123@qq.com"]]
    [[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"tel://10086"]];
    [[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"sms://10086"]];


新建一个工程A_app,找到info.plist 文件，右键add row  添加一行 URL types  

运行安装程序，到浏览器输入自定义的url scheme ，  abc://   此时就通过浏览器打开了app。

![](http://oolkmbv7h.bkt.clouddn.com/url_scheme03.jpeg)

![](http://oolkmbv7h.bkt.clouddn.com/url_scheme02.jpeg)


那么想要别人的app可以跳转到我们的app怎么办？再新建一个工程B_app  右键add row  添加一行 LSApplicationQueriesSchemes


![](http://oolkmbv7h.bkt.clouddn.com/url_scheme01.jpeg)


然后加一个button，点击事件

- (IBAction)btn:(id)sender
{
NSString *url = @"abc://?name=yu";
if ([[UIApplication sharedApplication] canOpenURL:[NSURL URLWithString:url]]) {
[[UIApplication sharedApplication] openURL:[NSURL URLWithString:url]];
}else{
NSLog(@"can not open");
}

}


然后回到A_app  在Appdelegate.m中

-(BOOL)application:(UIApplication *)application openURL:(nonnull NSURL *)url sourceApplication:(nullable NSString *)sourceApplication annotation:(nonnull id)annotation{
NSLog(@"sourceApplication: %@",sourceApplication);
NSLog(@"url shceme:%@",[url scheme]);
NSLog(@"para:%@",[url query]);
if ([sourceApplication isEqualToString:@"abc.aapp.com"]) {
return YES;
}
return NO;
}



<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


