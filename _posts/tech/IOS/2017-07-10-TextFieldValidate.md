---
layout: post
title: TextFieldValidate验证手机号，密码，邮箱
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

TextFieldValidate验证手机号，密码，邮箱


```javascript



#import <Foundation/Foundation.h>

@interface TextFieldValidate : NSObject

//验证手机号码
+ (BOOL) validateMobile:(NSString *)mobile;

//验证电子邮箱
+ (BOOL) validateEmail:(NSString *)email;

//验证密码
+ (BOOL) validatePassword:(NSString *) password;

@end




#import <UIKit/UIKit.h>
#import "TextFieldValidate.h"

@implementation TextFieldValidate


//验证手机号码
+ (BOOL) validateMobile:(NSString *)mobile
{
if (mobile.length == 0) {
NSString *message = @"手机号码不能为空！";
UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:nil
message:message
delegate:nil
cancelButtonTitle:@"确定"
otherButtonTitles:nil, nil];
[alertView show];
return NO;
}
//手机号以13， 15，18开头，八个 \d 数字字符
NSString *phoneRegex = @"^((13[0-9])|(15[^4,\\D])|(18[0,0-9]))\\d{8}$";
NSPredicate *phoneTest = [NSPredicate predicateWithFormat:@"SELF MATCHES %@",phoneRegex];
if (![phoneTest evaluateWithObject:mobile]) {
NSString *message = @"手机号码格式不正确！";
UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:nil
message:message
delegate:nil
cancelButtonTitle:@"确定"
otherButtonTitles:nil, nil];
[alertView show];
return NO;
}
return YES;
}


//验证电子邮箱
+ (BOOL)validateEmail:(NSString *)email {
if (email.length == 0) {
NSString *message = @"邮箱不能为空！";
UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:nil
message:message
delegate:nil
cancelButtonTitle:@"确定"
otherButtonTitles:nil, nil];
[alertView show];
return NO;
}

NSString *expression = [NSString stringWithFormat:@"^\\w+([-+.]\\w+)*@\\w+([-.]\\w+)*\\.\\w+([-.]\\w+)*$"];
NSError *error = NULL;
NSRegularExpression *regex = [[NSRegularExpression alloc] initWithPattern:expression
options:NSRegularExpressionCaseInsensitive
error:&error];
NSTextCheckingResult *match = [regex firstMatchInString:email
options:0
range:NSMakeRange(0,[email length])];
if (!match) {
UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:nil
message:@"邮箱格式错误！"
delegate:nil
cancelButtonTitle:@"确定"
otherButtonTitles:nil, nil];
[alertView show];
return NO;
}
return YES;
}

//验证密码
+ (BOOL)validatePassword:(NSString *)password
{
if (password.length == 0) {
NSString *message = @"密码不能为空！";
UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:nil
message:message
delegate:nil
cancelButtonTitle:@"确定"
otherButtonTitles:nil, nil];
[alertView show];
return NO;
}
if (password.length < 6) {
UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:nil
message:@"密码不足六位！"
delegate:nil
cancelButtonTitle:@"确定"
otherButtonTitles:nil, nil];
[alertView show];
return NO;
}

return YES;
}
@end










```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


