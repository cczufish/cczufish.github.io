---
layout: post
title: iOS圆形渐变(聚光灯效果实现）
category: iOS
tags: iOS,CocoaPods，os x
description:
---
来源 
https://www.jianshu.com/p/1d6a76a3d94b


- (instancetype)initWithFrame:(CGRect)frame {
    if (self = [super initWithFrame:frame]) {
        self.backgroundColor = [UIColor whiteColor];
    }
    return self;
}

- (void)drawRect:(CGRect)rect {
    [self draw];
}

- (void)draw {
    
    // 创建色彩空间对象
    CGColorSpaceRef rgb = CGColorSpaceCreateDeviceRGB();
    // 创建起点和终点颜色分量的数组
    CGFloat colors[] =
    {
        1, 0, 0, 1.00,//start color(r,g,b,alpha)
        255, 255, 255, 1.00,//end color
    };
    
    //形成梯形，渐变的效果
    CGGradientRef gradient = CGGradientCreateWithColorComponents
    (rgb, colors, NULL, 2);

//    NSLog(@"%lu",sizeof(colors)/(sizeof(colors[0])*4));
    
    // 起点颜色起始圆心
    CGPoint start = CGPointMake(self.frame.size.width/2, self.frame.size.height/2);
    // 终点颜色起始圆心
    CGPoint end = CGPointMake(self.frame.size.width/2, self.frame.size.height/2);
    // 起点颜色圆形半径
    CGFloat startRadius = 0.0f;
    // 终点颜色圆形半径
    CGFloat endRadius = 100;
    // 获取上下文
    CGContextRef graCtx = UIGraphicsGetCurrentContext();
    // 创建一个径向渐变
    CGContextDrawRadialGradient(graCtx, gradient, start, startRadius, end, endRadius, 0);
    
    //releas
    CGGradientRelease(gradient);
    gradient=NULL;
    CGColorSpaceRelease(rgb);
}


---




<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>
