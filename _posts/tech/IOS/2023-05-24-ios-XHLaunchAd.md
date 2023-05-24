---
layout: post
title:  ios 解决 XHLaunchAd 视频启动页 视频播放完边缩放边裁剪的问题 
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

 -(void)xhLaunchAd:(XHLaunchAd *)launchAd videoDownLoadFinish:(NSURL *)pathURL{
    
    NSLog(@"video下载/加载完成 path = %@",pathURL.absoluteString);
    
    // 视频文件路径
  //  NSString *path = [[NSBundle mainBundle] pathForResource:@"video" ofType:@"mp4"];

    // 创建 AVAsset
    AVAsset *asset = [AVAsset assetWithURL:pathURL];

    // 创建 AVAssetImageGenerator
    AVAssetImageGenerator *imageGenerator = [AVAssetImageGenerator assetImageGeneratorWithAsset:asset];
    imageGenerator.appliesPreferredTrackTransform = YES;

    // 获取视频最后一帧的时间
    CMTime lastFrameTime = CMTimeMakeWithSeconds(CMTimeGetSeconds(asset.duration) - 1.0, asset.duration.timescale);

    // 获取视频最后一帧的 CGImage
    CGImageRef image = NULL;
    NSError *error = nil;
    image = [imageGenerator copyCGImageAtTime:lastFrameTime actualTime:nil error:&error];

    if (error) {
        NSLog(@"Error generating thumbnail: %@", error.localizedDescription);
    }

    // 将 CGImage 转换为 UIImage
    if (image) {
        UIImage *uiImage = [UIImage imageWithCGImage:image];
        // 将图片保存到沙盒中
            NSString *documentsDirectory = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES)[0];
            NSString *filePath = [documentsDirectory stringByAppendingPathComponent:@"lastFrame.jpg"];
            NSURL *fileURL = [NSURL fileURLWithPath:filePath];
            NSData *imageData = UIImageJPEGRepresentation(uiImage, 1.0);
            [imageData writeToURL:fileURL atomically:YES];
        // 在这里可以将 uiImage 进行保存或者展示
        CGImageRelease(image);
    }

    
}





-(void)startSkipDispathTimer{
    XHLaunchAdConfiguration * configuration = [self commonConfiguration];
    DISPATCH_SOURCE_CANCEL_SAFE(_waitDataTimer);
    if(!configuration.skipButtonType) configuration.skipButtonType = SkipTypeTimeText;//默认
    __block NSInteger duration = 5;//默认
    if(configuration.duration) duration = configuration.duration;
    if(configuration.skipButtonType == SkipTypeRoundProgressTime || configuration.skipButtonType == SkipTypeRoundProgressText){
        [_skipButton startRoundDispathTimerWithDuration:duration];
    }
    NSTimeInterval period = 1.0;
    _skipTimer = dispatch_source_create(DISPATCH_SOURCE_TYPE_TIMER, 0, 0, dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0));
    dispatch_source_set_timer(_skipTimer, dispatch_walltime(NULL, 0), period * NSEC_PER_SEC, 0);
    dispatch_source_set_event_handler(_skipTimer, ^{
        dispatch_async(dispatch_get_main_queue(), ^{
            if ([self.delegate respondsToSelector:@selector(xhLaunchAd:customSkipView:duration:)]) {
                [self.delegate xhLaunchAd:self customSkipView:configuration.customSkipView duration:duration];
            }
            if(!configuration.customSkipView){
                [_skipButton setTitleWithSkipType:configuration.skipButtonType duration:duration];
            }
            
            if(duration==0){
                DISPATCH_SOURCE_CANCEL_SAFE(_skipTimer);
                NSLog(@"adVideoView frame: %@", NSStringFromCGRect(self.adVideoView.frame));
                self.adVideoView.clipsToBounds = NO;
                self.adVideoView.autoresizingMask = UIViewAutoresizingNone;
                
                self.window.alpha = 1;
                
                CGFloat type = 3;
                
                //  CGFloat targetWidth = CGRectGetWidth([UIScreen mainScreen].bounds) - 44;
                
                // 获取屏幕截图
                // 将图片保存到沙盒中
                NSString *documentsDirectory = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES)[0];
                NSString *filePath = [documentsDirectory stringByAppendingPathComponent:@"lastFrame.jpg"];
                NSURL *fileURL = [NSURL fileURLWithPath:filePath];
                //                    NSData *imageData = UIImageJPEGRepresentation(uiImage, 1.0);
                //                    [imageData writeToURL:fileURL atomically:YES];
                
                // 从沙盒中读取图片
                NSData *data = [NSData dataWithContentsOfURL:fileURL];
                UIImage *image = [UIImage imageWithData:data];
                UIImageView *imgView = [[UIImageView alloc] initWithFrame:self.window.bounds];
                
                [imgView setImage:image];
                imgView.contentMode = UIViewContentModeScaleAspectFill;
                imgView.backgroundColor = [UIColor redColor];
                imgView.clipsToBounds = YES;
                
                [self.window addSubview:imgView];
                self.adVideoView.alpha = 0; //type == 3 设置
                
                
                
                [UIView animateWithDuration:3 delay:0 options: UIViewAnimationOptionTransitionFlipFromBottom animations:^{
                    
                    if (type == 1) { // 可以缩放
                        self.adVideoView.clipsToBounds = YES;
                        
                        CGFloat scale = (CGRectGetWidth([UIScreen mainScreen].bounds) - 44) / CGRectGetWidth(self.window.frame);
                        CGFloat yscale = (CGRectGetWidth([UIScreen mainScreen].bounds) - 44) / CGRectGetHeight(self.window.frame);
                        
                        self.window.transform = CGAffineTransformMakeScale(scale, yscale);
                        CGFloat newX = CGRectGetWidth([UIScreen mainScreen].bounds)/2;
                        CGFloat navBarHeight = [UIApplication sharedApplication].statusBarFrame.size.height+44.0;
                        CGFloat newY =  navBarHeight + 10 + (CGRectGetWidth([UIScreen mainScreen].bounds) - 44) / 2;
                        
                        self.window.center = CGPointMake(newX, newY);
                    }else if( type == 2) { // 可以裁剪
                        CGFloat navBarHeight = [UIApplication sharedApplication].statusBarFrame.size.height + 44.0;
                        CGFloat targetWidth = CGRectGetWidth([UIScreen mainScreen].bounds) - 44;
                        CGFloat targetHeight = targetWidth;
                        CGFloat targetScale = targetWidth / CGRectGetWidth(self.window.frame);
                        
                        CGRect targetBounds = self.adVideoView.bounds;
                        targetBounds.size.width = targetWidth / targetScale;
                        targetBounds.size.height = targetHeight / targetScale;
                        self.adVideoView.bounds = targetBounds;
                        
                        CGRect targetFrame = self.adVideoView.frame;
                        targetFrame.size.width = targetWidth;
                        targetFrame.size.height = targetHeight;
                        targetFrame.origin.x = (CGRectGetWidth([UIScreen mainScreen].bounds) - targetWidth) / 2;
                        targetFrame.origin.y = navBarHeight + 10;
                        self.adVideoView.frame = targetFrame;
                    }else if( type == 3) { // 可以边缩放边裁剪
                        CGFloat navBarHeight = [UIApplication sharedApplication].statusBarFrame.size.height + 44.0;
                        CGFloat targetWidth = CGRectGetWidth([UIScreen mainScreen].bounds) - 44;
                        CGFloat targetHeight = targetWidth;
                        imgView.contentMode = UIViewContentModeScaleAspectFill;
                        [imgView setFrame:CGRectMake((CGRectGetWidth([UIScreen mainScreen].bounds) - targetWidth) / 2, navBarHeight + 10, targetWidth, targetHeight)];
                    }
                } completion:^(BOOL finished) {
                    // 动画结束后移除广告视图
                    //                    self.window.alpha = 0;
                    //                    [self removeAndAnimate];
                }];
                
                
            }
            duration--;
        });
    });
    dispatch_resume(_skipTimer);
}



```



---
