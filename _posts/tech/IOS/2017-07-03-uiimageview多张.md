---
layout: post
title: UImageView播放多张图片停留最后一张
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

UImageView播放多张图片停留最后一张

```javascript

- (void)updateTopFrame:(int)hgnum andjbnum:(int)jbnum andzsnum:(int)zsnum andhxnum:(int)hxnum
{

for (UIImageView *img in tV.subviews) {
[img removeFromSuperview];
}



// 66*82 74*62 57*54
tV.hidden = NO;

float twidth = jbnum*33+zsnum*37+hxnum*29+(jbnum+zsnum+hxnum-1)*10;

[tV setFrame:CGRectMake((UIScreenWidth-twidth)/2, 20, twidth, 41)];

float jbx = 0;
float zsx = 0;
float hxx = 0;


for (int i = 0; i < jbnum; i ++) {
UIImageView *jbImagev = [[UIImageView alloc] initWithFrame:CGRectMake(i*33+10*i, 0, 33, 41)];
jbImagev.image = [UIImage imageNamed:@"奖杯"];
[tV addSubview:jbImagev];

jbx = jbnum*33+jbnum*10;
}

for (int i = 0; i < zsnum; i ++) {

int value = arc4random() % zsnum;

NSArray *tArr = [NSArray arrayWithObjects:@"红宝石",@"黄宝石",@"蓝宝石",@"绿宝石",@"紫宝石", nil];

UIImageView *jbImagev = [[UIImageView alloc] initWithFrame:CGRectMake(i*37+10*i + jbx, 5, 37, 31)];
jbImagev.image = [UIImage imageNamed:tArr[value]];
[tV addSubview:jbImagev];

zsx = zsnum*37+zsnum*10 + jbx;

}

for (int i = 0; i < hxnum; i ++)
{
if (zsx>0) {
hxx = i*29+10*i + zsx;
}else{
hxx = i*29+10*i + jbx;
}


UIImageView *jbImagev = [[UIImageView alloc] initWithFrame:CGRectMake(hxx, 7, 29, 27)];


NSArray *imgs = @[[UIImage imageNamed:@"星星测试 2_00001"],
[UIImage imageNamed:@"星星测试 2_00002"],
[UIImage imageNamed:@"星星测试 2_00003"],
[UIImage imageNamed:@"星星测试 2_00004"],
[UIImage imageNamed:@"星星测试 2_00005"],
[UIImage imageNamed:@"星星测试 2_00006"],
[UIImage imageNamed:@"星星测试 2_00007"],
[UIImage imageNamed:@"星星测试 2_00008"],
[UIImage imageNamed:@"星星测试 2_00009"],
[UIImage imageNamed:@"星星测试 2_00010"],
[UIImage imageNamed:@"星星测试 2_00011"],
[UIImage imageNamed:@"星星测试 2_00012"],
[UIImage imageNamed:@"星星测试 2_00013"],
[UIImage imageNamed:@"星星测试 2_00014"],
[UIImage imageNamed:@"星星测试 2_00015"]];



[jbImagev setImage:[UIImage imageNamed:@"星星2"]];

if (i == hxnum-1)
{
//imageView的动画图片是数组images
jbImagev.animationImages = imgs;
//按照原始比例缩放图片，保持纵横比
jbImagev.contentMode = UIViewContentModeScaleAspectFit;
//切换动作的时间3秒，来控制图像显示的速度有多快，
jbImagev.animationDuration = 0.3;
//动画的重复次数，想让它无限循环就赋成0
jbImagev.animationRepeatCount = 1;
//开始动画
[jbImagev startAnimating];

}


[tV addSubview:jbImagev];



}


}


```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


