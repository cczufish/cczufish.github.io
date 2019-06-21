---
layout: post
title: 阿里云视频播放器、视频录制上传相关问题
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

阿里云iOS上传点播SDK
https://help.aliyun.com/document_detail/94437.html?spm=a2c4g.11186623.6.838.584f192bISVlnp

阿里云播放器sdk https://help.aliyun.com/document_detail/94428.html?spm=a2c4g.11186623.6.1000.584f192bMYY6X4

[iOS]关于视频方向的若干问题 、MP4视频文件中的Rotation元数据
https://blog.csdn.net/chengkaizone/article/details/51295022

How to fix video orientation  in iOS
https://stackoverflow.com/questions/16118559/how-to-fix-video-orientation-issue-in-ios


reason: image not found的解决方案
https://blog.csdn.net/wang631106979/article/details/55258478

iOS平台相册视频方向问题 #250
https://github.com/banchichen/TZImagePickerController/issues/250

AVAssetExportSession progress KVO
https://blog.csdn.net/jeffasd/article/details/51939497

 iphone x 录制的视频 通过VODUpload sdk上传到阿里云后不能播放,vid播放
 您好， 这边查出来iphone X XR拍摄出来的视屏格式是H265/HEVC， 直接拍摄出来上传没有转码， 而我们的播放器目前是不支持HEVC/H.265解码的
 
 
 视频导出的时候 h264格式 保存成mp4 
 MOV/MP4视频文件中的Rotation元数据iOS上内置相机应用录制的mov/mp4视频可能产生一个Rotation元数据,表示录制视频时摄像头旋转到了多少角度。其值一般为这四个:0、90、180或270。类似于图片文件的Exif信息中的Orientation元数据。Rotation元数据用于播放器确定渲染视频的方向,但是的播放器会对其视而不见，有的人倒着拍摄视频 播放的时候 无法确定视频的方向。
 
 sdk中 videoRotation参数取到的值一直是0，导致 -(void) setRenderRotate:(RenderRotate)rotate; 这个方法失效


通过VODUpload sdk上传到阿里云的视频，通过vid播放的时候提示4003
func vodPlayer(_ vodPlayer: AliyunVodPlayer!, playBack errorModel: AliyunPlayerVideoErrorModel!) {

查看您这边使用的私有加密的资源，请您这边在您的视频点播绑定了您自己的域名后在使用vid的方式播放加密资源测试。
绑定域名参考：https://help.aliyun.com/document_detail/86074.html?spm=a2c4g.11186623.6.577.1b4f68f0Zo8yTa  

需要您绑定域名后播放测试，现在该URL对应的ts文件是没有带签名的，因此对应的ts访问是会报403的。  
好的，绑定后记住要cname解析后再测试。  



 
 

```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

