---
layout: post
title: AFNetworking的简单使用-AFHTTPSessionManager文件下载
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

AFNetworking的简单使用-AFHTTPSessionManager文件下载


```javascript


@interface DownloadItem : JSONModel

@property (strong, nonatomic) NSString *urlString;
@property (strong, nonatomic) NSString *saveName;
@property (strong, nonatomic) NSString *saveDir;
@end

#import "DownloadItem.h"

@implementation DownloadItem

@end




#import <Foundation/Foundation.h>
#import "DownloadItem.h"

typedef void(^DownloadProgressBlock)(double progress,long int totalUnit,long int completeUnit);
typedef void(^DownloadSuccessBlock)(id responseObject,NSString *path);
typedef void(^DownloadErrorBlock)(NSError *error);
typedef void(^DownloadLengthBlock)(int length, NSError *error);

@interface DownloadManage : NSObject

+ (DownloadManage *)defaultDownloadManage;

- (void)downLoadFile:(DownloadItem *)aItem progress:(DownloadProgressBlock)progressBlock success:(DownloadSuccessBlock)successBlock error:(DownloadErrorBlock)errorBlock;

-(void)totalDownloadWithUrlString:(NSString *)aUrlString downloadLength:(DownloadLengthBlock)downloadLengthBlock;

@end


#import "DownloadManage.h"


@interface DownloadManage() {
AFHTTPSessionManager *manager;
}
@end


@implementation DownloadManage

static DownloadManage *download = nil;
+ (DownloadManage *)defaultDownloadManage {
if(download == nil) {
download = [[DownloadManage alloc] init];
}
return download;
}

- (id)init {
self = [super init];
if(self) {
manager = [[AFHTTPSessionManager alloc] init];
manager.responseSerializer = [AFHTTPResponseSerializer serializer];

}
return self;
}


- (void)downLoadFile:(DownloadItem *)aItem progress:(DownloadProgressBlock)progressBlock success:(DownloadSuccessBlock)successBlock error:(DownloadErrorBlock)errorBlock
{
BOOL isDir = NO;
NSFileManager *fileManager = [NSFileManager defaultManager];
BOOL existed = [fileManager fileExistsAtPath:aItem.saveDir isDirectory:&isDir];

if (!(isDir == YES && existed == YES)) {
[fileManager createDirectoryAtPath:aItem.saveDir withIntermediateDirectories:YES attributes:nil error:nil];
}

NSURLSessionDownloadTask *task = [manager downloadTaskWithRequest:[NSURLRequest requestWithURL:[NSURL URLWithString:aItem.urlString]] progress:^(NSProgress *_Nonnull downloadProgress){

NSLog(@"%lld",downloadProgress.totalUnitCount);
NSLog(@"%lld",downloadProgress.completedUnitCount);


double percentDone =(double) downloadProgress.completedUnitCount / (double)downloadProgress.totalUnitCount;

NSLog(@"downloadProgress = %.4f",percentDone);


progressBlock(percentDone,(long int)downloadProgress.totalUnitCount,(long int)downloadProgress.completedUnitCount);

}destination:^NSURL *_Nonnull(NSURL *_Nonnull targetPath,NSURLResponse * _Nonnull reponse){
return [NSURL fileURLWithPath:[aItem.saveDir stringByAppendingPathComponent:aItem.saveName]];

}completionHandler:^(NSURLResponse * _Nonnull response, NSURL * _Nullable filePath, NSError * _Nullable error) {
if(!error)
{
successBlock(response,(NSString *)filePath);

}else{
errorBlock(error);
}
}];
[task resume];
}

-(void)totalDownloadWithUrlString:(NSString *)aUrlString downloadLength:(DownloadLengthBlock)downloadLengthBlock
{
NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:aUrlString]];
[request setHTTPMethod:@"HEAD"];
[[manager dataTaskWithRequest:request completionHandler:^(NSURLResponse * _Nonnull response, id  _Nullable responseObject, NSError * _Nullable error) {
long long int n = response.expectedContentLength;
int length  = (int)(n / 1024 / 1024);
downloadLengthBlock(length, error);
}] resume];


}


- (void)cancelQueue
{
[manager.operationQueue cancelAllOperations];
}

- (void)cancelRequest
{
[manager.operationQueue cancelAllOperations];
}













```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


