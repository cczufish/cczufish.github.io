---
layout: post
title: UIView旋转90度后发现不能拖动的问题
category: iOS
tags: iOS, Alcatraz，os x
description:
---

UIView旋转90度后发现不能拖动的问题，没旋转之前可以正常拖动 ， 旋转后不能正常拖动，把transform复原后就可以拖动

```javascript

- (void)viewDidLoad {
[super viewDidLoad];
// Do any additional setup after loading the view, typically from a nib.

UIView *v = [[UIView alloc] initWithFrame:CGRectMake(100, 90, 80, 80)];
v.backgroundColor = [UIColor redColor];
v.tag = 100;
[self.view addSubview:v];
NSLog(@"v---%@",v);

v.transform = CGAffineTransformMakeRotation(90 *M_PI / 180.0);
NSLog(@"v1---%@",v);

// NSLog(@"v2---%@",v);

}



/**
*  触摸事件开始（手指触摸到屏幕）
*/
- (void)touchesBegan:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event {
//  NSLog(@"%s", __func__);

// 1.获取UITouch对象
UITouch *touch = [touches anyObject];

UIView *view = [touch view];


if (view.tag != 100) {
return;
}
view.transform = CGAffineTransformIdentity;


}

/**
*  触摸移动时调用（手指在屏幕上移动）
*/
- (void)touchesMoved:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event {

// 1.获取UITouch对象
UITouch *touch = [touches anyObject];

UIView *view = [touch view];


if (view.tag != 100) {
return;
}

// 2.获取当前手指点的位置
CGPoint currentPoint = [touch locationInView: [UIApplication sharedApplication].keyWindow];

// 3.获取上一个手指点的位置
CGPoint previouPoint = [touch previousLocationInView: [UIApplication sharedApplication].keyWindow];

// 4.算出2次移动的偏移量
CGFloat offsetX = currentPoint.x - previouPoint.x;
CGFloat offsetY = currentPoint.y - previouPoint.y;

// 5.移动UIView视图的位置
view.transform = CGAffineTransformTranslate(view.transform, offsetX, offsetY);


}

/**
*  触摸完成时调用（手指抬起）
*/
- (void)touchesEnded:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event {



}

/**
*  触摸取消时调用（有电话接入）
*/
- (void)touchesCancelled:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event {
//  NSLog(@"%s", __func__);
}




2017-05-20 18:13:08.023 Test[7071:467736] v---<UIView: 0x7f909ff0a480; frame = (100 90; 80 80); tag = 100; layer = <CALayer: 0x60000003e440>>
2017-05-20 18:13:08.024 Test[7071:467736] v1---<UIView: 0x7f909ff0a480; frame = (100 90; 80 80); transform = [6.123233995736766e-17, 1, -1, 6.123233995736766e-17, 0, 0]; tag = 100; layer = <CALayer: 0x60000003e440>>
2017-05-20 18:13:10.943 Test[7071:467736] v2---<UIView: 0x7f909ff0a480; frame = (100 90; 80 80); tag = 100; layer = <CALayer: 0x60000003e440>>




```






<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


