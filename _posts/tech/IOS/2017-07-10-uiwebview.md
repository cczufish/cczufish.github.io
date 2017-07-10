---
layout: post
title: UIwebview 加载图片宽度自适应屏幕
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

UIwebview 加载图片宽度自适应屏幕


```javascript

#import <UIKit/UIKit.h>

@interface MyDownWebController : UIViewController

@property (nonatomic, strong) NSString *fileUrl;
@property (weak, nonatomic) IBOutlet UIWebView *webview;
@property (weak, nonatomic) IBOutlet UILabel *titleLabel;

@end




#import "MyDownWebController.h"

@interface MyDownWebController ()

@end

@implementation MyDownWebController

- (void)viewDidLoad {
[super viewDidLoad];
// Do any additional setup after loading the view from its nib.
NSURL *url = [NSURL fileURLWithPath:self.fileUrl];
NSURLRequest *request = [NSURLRequest requestWithURL:url];
[self.webview loadRequest:request];
//    self.webview.autoresizesSubviews = YES;
self.webview.scalesPageToFit = YES;//自动对页面进行缩放以适应屏幕

}

- (void)didReceiveMemoryWarning {
[super didReceiveMemoryWarning];
// Dispose of any resources that can be recreated.
}

- (IBAction)backParentBtnTapped:(id)sender {
[self.navigationController popViewControllerAnimated:YES];
}

@end



// webview 加载图片宽度自适应屏幕
- (void)webViewDidFinishLoad:(UIWebView *)webView
{
NSString *js = @"function imgAutoFit(){ \
var imgs = document.getElementsByTagName('img'); \
for (var i = 0; i < imgs.length; ++i) { \
var img = imgs[i]; \
img.style.maxWidth = %f; \
} \
}";
js = [NSString stringWithFormat:js,DeviceScreenWidth - 20];
[webView stringByEvaluatingJavaScriptFromString:js];
[webView stringByEvaluatingJavaScriptFromString:@"imgAutoFit()"];
}











```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


