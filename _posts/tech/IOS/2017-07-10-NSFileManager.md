---
layout: post
title: NSFileManager单个文件的大小和遍历文件夹获得文件夹大小
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

NSFileManager单个文件的大小


```javascript


//单个文件的大小
- (long long) fileSizeAtPath:(NSString*) filePath{
NSFileManager* manager = [NSFileManager defaultManager];
if ([manager fileExistsAtPath:filePath]){
return [[manager attributesOfItemAtPath:filePath error:nil] fileSize]/1024;
}
return 0;
}



//遍历文件夹获得文件夹大小，返回多少M
- (float)folderSizeAtPath:(NSString*)folderPath{
NSFileManager* manager = [NSFileManager defaultManager];
if (![manager fileExistsAtPath:folderPath])
return 0;
NSEnumerator *childFilesEnumerator = [[manager subpathsAtPath:folderPath] objectEnumerator];
NSString* fileName;
long long folderSize = 0;
while ((fileName = [childFilesEnumerator nextObject]) != nil){
NSString* fileAbsolutePath = [folderPath stringByAppendingPathComponent:fileName];
folderSize += [self fileSizeAtPath:fileAbsolutePath];
}
return folderSize/(1024.0*1024.0);
}







```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


