---
layout: post
title: wkwebview 白屏 post请求body数据被清空
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

post 请求 body 数据被清空

由于 WKWebView 在独立进程里执行网络请求。一旦注册 http(s) scheme 后，网络请求将从 Network Process 发送到 App Process，这样 NSURLProtocol 才能拦截网络请求。在 webkit2 的设计里使用 MessageQueue 进行进程之间的通信，Network Process 会将请求 encode 成一个 Message,然后通过 IPC 发送给 App Process。出于性能的原因，encode 的时候 HTTPBody 和 HTTPBodyStream 这两个字段被丢弃掉了(参考苹果源码： 
https://github.com/WebKit/webkit/blob/fe39539b83d28751e86077b173abd5b7872ce3f9/Source/WebKit2/Shared/mac/WebCoreArgumentCodersMac.mm#L61-L88 及bug report: https://bugs.webkit.org/show_bug.cgi?id=138169)。

因此，如果通过 registerSchemeForCustomProtocol 注册了 http(s) scheme, 那么由 WKWebView 发起的所有 http(s)请求都会通过 IPC 传给主进程 NSURLProtocol 处理，导致 post 请求 body 被清空；
--------------------- 
作者：腾讯Bugly 
来源：CSDN 
原文：https://blog.csdn.net/tencent_bugly/article/details/54668721/ 
版权声明：本文为博主原创文章，转载请附上博文链接！


在WKWebView上通过loadRequest发起的post请求body数据会丢失：

//同样是由于多进程间通信性能问题，导致HTTPBody字段被丢弃
[request setHTTPMethod:@"POST"];
[request setHTTPBody:[@"bodyData" dataUsingEncoding:NSUTF8StringEncoding]];
[wkwebview loadRequest: request];
workaround: 
假如想通过-[WKWebView loadRequest:]加载post请求request1:http://h5.qzone.qq.com/mqzone/index ,可以通过以下步骤实现：

替换请求scheme，生成新的post请求request2: post://h5.qzone.qq.com/mqzone/index, 同时将request1的body字段复制到request2的header中;
通过-[WKWebView loadRequest:]加载新的post请求request2;
通过 +[WKBrowsingContextController registerSchemeForCustomProtocol:]注册scheme: post://;
使用NSURLProtocol拦截请求post://h5.qzone.qq.com/mqzone/index ,替换请求scheme, 生成新的请求request3: http://h5.qzone.qq.com/mqzone/index ，将request2 header的body字段复制到request3的body中，并通过NSURLConnection加载request3，最后将加载结果返回WKWebView;


https://cloud.tencent.com/developer/article/1005691

https://github.com/didi/DoraemonKit/commit/b4ff6462b7641dc8874cc7b4d5d7734f8540f554




#import <Foundation/Foundation.h>

NS_ASSUME_NONNULL_BEGIN

@interface NSURLProtocol (DoraemonWebKitSupport)

+ (void)doraemon_wk_registerScheme:(NSString*)scheme;

+ (void)doraemon_wk_unregisterScheme:(NSString*)scheme;

@end

NS_ASSUME_NONNULL_END


#import "NSURLProtocol+DoraemonWebKitSupport.h"
#import <WebKit/WebKit.h>

FOUNDATION_STATIC_INLINE Class ContextControllerClass() {
static Class cls;
if (!cls) {
cls = [[[WKWebView new] valueForKey:@"browsingContextController"] class];
}
return cls;
}

FOUNDATION_STATIC_INLINE SEL RegisterSchemeSelector() {
return NSSelectorFromString(@"registerSchemeForCustomProtocol:");
}

FOUNDATION_STATIC_INLINE SEL UnregisterSchemeSelector() {
return NSSelectorFromString(@"unregisterSchemeForCustomProtocol:");
}


@implementation NSURLProtocol (DoraemonWebKitSupport)

+ (void)doraemon_wk_registerScheme:(NSString*)scheme{
Class cls = ContextControllerClass();
SEL sel = RegisterSchemeSelector();
if ([(id)cls respondsToSelector:sel]) {
#pragma clang diagnostic push
#pragma clang diagnostic ignored "-Warc-performSelector-leaks"
[(id)cls performSelector:sel withObject:scheme];
#pragma clang diagnostic pop
}
}

+ (void)doraemon_wk_unregisterScheme:(NSString*)scheme{
Class cls = ContextControllerClass();
SEL sel = UnregisterSchemeSelector();
if ([(id)cls respondsToSelector:sel]) {
#pragma clang diagnostic push
#pragma clang diagnostic ignored "-Warc-performSelector-leaks"
[(id)cls performSelector:sel withObject:scheme];
#pragma clang diagnostic pop
}
}


@end




```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

