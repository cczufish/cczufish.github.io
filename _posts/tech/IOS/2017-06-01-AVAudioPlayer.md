---
layout: post
title: AVAudioPlayer播放mp3音频
category: iOS
tags: iOS, Alcatraz，os x,AVAudioPlayer
description:
---

AVAudioPlayer播放mp3音频


```javascript

#import <AVFoundation/AVFoundation.h>

@interface ViewController (){
AVAudioPlayer *player;
}

@end

@implementation ViewController

- (void)viewDidLoad {
[super viewDidLoad];
//    设置当前view背景色

[self myBtnAction];

}


-(void)myBtnAction {
//    获取项目中的音频文件
NSString *filepath = [[NSBundle mainBundle]pathForResource:@"rqhhs" ofType:@"mp3"];
//    把获取的音频文件转化为nsdata类型
NSData *data = [[NSData data]initWithContentsOfFile:filepath];

//    初始化一个音频播放器
player = [[AVAudioPlayer alloc]initWithData:data error:nil];

//    如果音频播放器处于播放状态，点击后就暂停播放，如果处于未播放状态，就开始播放
if (player.playing) {
[player pause];
}else{
[player play];

}
}



使用AVFoundation框架的AVPlayer进行播放会一直打印AQDefaultDevice (173): skipping input stream 0 0 0x0,这不是工程的问题，只需要在Xcode中设置一下就可以了。
解决办法:
1.选择 Product -->Scheme-->Edit Scheme
2.选择 Arguments
3.在Environment Variables添加一个环境变量 OS_ACTIVITY_MODE 设置值为"disable"



```









<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


