---
layout: post
title: shareSDK分享到第三方平台ShareManager
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

shareSDK分享到第三方平台ShareManager


```javascript



#import <Foundation/Foundation.h>

@interface ShareManager : NSObject

+ (id)sharedManager;

//获取用户信息
- (void)getUserInfoWithPlatformType:(SSDKPlatformType)platformType completion:(void(^)(id objects, BOOL isSuccess))callback;

//分享到QQ空间
- (void)sharedToQzone:(id)image sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback;
//分享到QQ
- (void)sharedToQQ:(id)image sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback;

//分享到朋友圈
- (void)sharedToWechatTimeline:(id)image sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback;

//分享到微信好友
- (void)sharedToWechatSession:(id)image sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback;

//分享到新浪微博
- (void)sharedToWeiBoSession:(id)imageUrl sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback;

@end





#import "ShareManager.h"
#import <ShareSDKUI/ShareSDK+SSUI.h>
#import "WXApi.h"
#import <TencentOpenAPI/TencentOAuth.h>

@implementation ShareManager

+ (id)sharedManager {
static ShareManager *instance = nil;
static dispatch_once_t onceToken;
dispatch_once(&onceToken, ^{
instance = [[ShareManager alloc] init];
});
return instance;
}


//获取用户信息  第三方登陆
- (void)getUserInfoWithPlatformType:(SSDKPlatformType)platformType completion:(void(^)(id objects, BOOL isSuccess))callback {
[ShareSDK getUserInfo:platformType onStateChanged:^(SSDKResponseState state, SSDKUser *user, NSError *error) {
if (state == SSDKResponseStateSuccess) {
callback(user, YES);
} else {
callback(error, NO);
}
}];
}


//分享到QQ空间
- (void)sharedToQzone:(id)viewImage sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback {
NSMutableDictionary *shareParams = [NSMutableDictionary dictionary];
//QQ空间不支持SSDKContentTypeImage这种类型，所以需要定制下。
[shareParams SSDKSetupQQParamsByText:detailtext title:title url:[NSURL URLWithString:url] thumbImage:nil image:viewImage type:SSDKContentTypeWebPage forPlatformSubType:SSDKPlatformSubTypeQZone];
[ShareSDK share:SSDKPlatformSubTypeQZone parameters:shareParams onStateChanged:^(SSDKResponseState state, NSDictionary *userData, SSDKContentEntity *contentEntity, NSError *error) {
switch (state) {
case SSDKResponseStateBegin:
break;
case SSDKResponseStateSuccess: {
callback(nil, YES);
break;
}
case SSDKResponseStateFail: {
callback(@"分享失败", NO);
break;
}
case SSDKResponseStateCancel: {
callback(@"分享已取消", NO);
}
default:
break;
}
}];
}



//分享到QQ
- (void)sharedToQQ:(id)image sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback {
NSMutableDictionary *shareParams = [NSMutableDictionary dictionary];
[shareParams SSDKSetupShareParamsByText:detailtext images:@[image] url:[NSURL URLWithString:url] title:title type:SSDKContentTypeWebPage];
[ShareSDK share:SSDKPlatformSubTypeQQFriend parameters:shareParams onStateChanged:^(SSDKResponseState state, NSDictionary *userData, SSDKContentEntity *contentEntity, NSError *error) {
switch (state) {
case SSDKResponseStateBegin:
break;
case SSDKResponseStateSuccess: {
callback(nil, YES);
break;
}
case SSDKResponseStateFail: {
callback(@"分享失败", NO);
break;
}
case SSDKResponseStateCancel: {
callback(@"分享已取消", NO);
}
default:
break;
}
}];
}



//分享到朋友圈
- (void)sharedToWechatTimeline:(id)image sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback {
if (![WXApi isWXAppInstalled]) {
callback(@"微信未安装", NO);
return;
}
NSMutableDictionary *shareParams = [NSMutableDictionary dictionary];
[shareParams SSDKSetupShareParamsByText:detailtext images:@[image] url:[NSURL URLWithString:url] title:title type:SSDKContentTypeWebPage];
[ShareSDK share:SSDKPlatformSubTypeWechatTimeline parameters:shareParams onStateChanged:^(SSDKResponseState state, NSDictionary *userData, SSDKContentEntity *contentEntity, NSError *error) {
switch (state) {
case SSDKResponseStateBegin:
break;
case SSDKResponseStateSuccess: {
callback(nil, YES);
break;
}
case SSDKResponseStateFail: {
callback(@"分享失败", NO);
break;
}
case SSDKResponseStateCancel: {
callback(@"分享已取消", NO);
}
default:
break;
}
}];
}


//分享到微信好友
- (void)sharedToWechatSession:(id)image sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback {
if (![WXApi isWXAppInstalled]) {
callback(@"微信未安装", NO);
return;
}
NSMutableDictionary *shareParams = [NSMutableDictionary dictionary];
[shareParams SSDKSetupShareParamsByText:detailtext images:@[image] url:[NSURL URLWithString:url] title:title type:SSDKContentTypeWebPage];
[ShareSDK share:SSDKPlatformSubTypeWechatSession parameters:shareParams onStateChanged:^(SSDKResponseState state, NSDictionary *userData, SSDKContentEntity *contentEntity, NSError *error) {
switch (state) {
case SSDKResponseStateBegin:
break;
case SSDKResponseStateSuccess: {
callback(nil, YES);
break;
}
case SSDKResponseStateFail: {
callback(@"分享失败", NO);
break;
}
case SSDKResponseStateCancel: {
callback(@"分享已取消", NO);
}
default:
break;
}
}];
}


//分享到新浪微博  显示内容编辑视图
- (void)sharedToWeiBoSession:(id)imageUrl sharedTitle:(NSString *)title andDetailText:(NSString *)detailtext sharedUrl:(NSString *)url completion:(void(^)(id objects, BOOL isSuccess))callback {
NSMutableDictionary *shareParams = [NSMutableDictionary dictionary];
NSString *contentTitle = [NSString stringWithFormat:@"%@+%@", detailtext, url];

[shareParams SSDKEnableUseClientShare];
[shareParams SSDKSetupShareParamsByText:contentTitle images:@[imageUrl] url:[NSURL URLWithString:url] title:title type:SSDKContentTypeAuto];
[ShareSDK share:SSDKPlatformTypeSinaWeibo parameters:shareParams onStateChanged:^(SSDKResponseState state, NSDictionary *userData, SSDKContentEntity *contentEntity, NSError *error) {
switch (state) {
case SSDKResponseStateBegin:
break;
case SSDKResponseStateSuccess: {
callback(nil, YES);
break;
}
case SSDKResponseStateFail: {
callback(@"分享失败", NO);
break;
}
case SSDKResponseStateCancel: {
callback(@"分享已取消", NO);
}
default:
break;
}
}];
}









```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


