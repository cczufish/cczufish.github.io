---
layout: post
title: iOS面试题
category: iOS
tags: iOS,面试
description:
---

题目来自http://www.cocoachina.com/bbs/read.php?tid-1718238.html，答案是自己作答。

1，下面代码在按钮点击后，在ARC下会发生什么，MRC下呢？为什么？

ARC下：

    @interface ViewController ()
    @property(nonatomic, assign) void(^block)();

    @end

    @implementation ViewController

    - (void)viewDidLoad {
    [super viewDidLoad];

    int value = 10;
    void(^blockC)() = ^{
    NSLog(@"just a block === %d", value);
    };

    NSLog(@"%@", blockC);
    _block = blockC;
    }

    - (IBAction)action:(id)sender {
    NSLog(@"%@", _block);
    }
