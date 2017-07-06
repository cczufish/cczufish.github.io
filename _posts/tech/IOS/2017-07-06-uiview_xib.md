---
layout: post
title: UIView+xib
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

避免uibutton连续点击,多次触发响应事件

https://github.com/Raymon-lau/UIButton-touch

```javascript



#import <UIKit/UIKit.h>

@protocol SelectQuestionViewDelegate <NSObject>

- (void)didSelelctStart:(int)number andAnswerString:(NSString *)str;

@end


@interface SelectQuestionView : UIView
@property (weak, nonatomic) IBOutlet UIButton *aBtn;
@property (weak, nonatomic) IBOutlet UIButton *bBtn;
@property (weak, nonatomic) IBOutlet UIButton *cBtn;
@property (weak, nonatomic) IBOutlet UIButton *dBtn;
@property (weak, nonatomic) IBOutlet UITextField *textField;
@property (weak, nonatomic) IBOutlet UIButton *startBtn;
@property (assign,nonatomic) BOOL aPressed;
@property (assign,nonatomic) BOOL bPressed;
@property (assign,nonatomic) BOOL cPressed;
@property (assign,nonatomic) BOOL dPressed;
@property (nonatomic, weak) id<SelectQuestionViewDelegate> delegate;
@property (weak, nonatomic) IBOutlet UIButton *closeBtn;


- (IBAction)closeBtnPressed:(id)sender;
- (IBAction)aBtnPressed:(id)sender;
- (IBAction)bBtnPressed:(id)sender;
- (IBAction)cBtnPressed:(id)sender;
- (IBAction)dBtnPressed:(id)sender;
- (IBAction)startBtnPressed:(id)sender;

+(SelectQuestionView *)instanceView;

@end



#import "SelectQuestionView.h"
#import <QuartzCore/QuartzCore.h>

@implementation SelectQuestionView

+(SelectQuestionView *)instanceView
{
NSArray* nibView =  [[NSBundle mainBundle] loadNibNamed:@"SelectQuestionView" owner:nil options:nil];
return [nibView objectAtIndex:0];
}


-(id)initWithCoder:(NSCoder *)aDecoder
{
self = [super initWithCoder:aDecoder];
if(self)
{


}
return self;
}


- (void)layoutSubviews
{
[super layoutSubviews];

//设置边框及边框颜色

self.textField.layer.borderWidth = 1;

self.textField.layer.borderColor =[[UIColor lightGrayColor] CGColor];
}

- (IBAction)aBtnPressed:(id)sender {

_aPressed = !_aPressed;
if (_aPressed)
{
[self.aBtn setBackgroundImage:[UIImage imageNamed:@"A_icon_pre"] forState:UIControlStateNormal];

}else{
[self.aBtn setBackgroundImage:[UIImage imageNamed:@"A_icon_nor"] forState:UIControlStateNormal];

}

}

- (IBAction)bBtnPressed:(id)sender {
_bPressed = !_bPressed;
if (_bPressed)
{
[self.bBtn setBackgroundImage:[UIImage imageNamed:@"B_icon_pre"] forState:UIControlStateNormal];

}else{
[self.bBtn setBackgroundImage:[UIImage imageNamed:@"B_icon_nor"] forState:UIControlStateNormal];

}
}

- (IBAction)cBtnPressed:(id)sender {
_cPressed = !_cPressed;
if (_cPressed)
{
[self.cBtn setBackgroundImage:[UIImage imageNamed:@"C_icon_pre"] forState:UIControlStateNormal];

}else{
[self.cBtn setBackgroundImage:[UIImage imageNamed:@"C_icon_nor"] forState:UIControlStateNormal];

}
}

- (IBAction)dBtnPressed:(id)sender {
_dPressed = !_dPressed;
if (_dPressed)
{
[self.dBtn setBackgroundImage:[UIImage imageNamed:@"D_icon_pre"] forState:UIControlStateNormal];

}else{
[self.dBtn setBackgroundImage:[UIImage imageNamed:@"D_icon_nor"] forState:UIControlStateNormal];

}
}

- (IBAction)startBtnPressed:(id)sender {

NSString *answerStr = @"";
if (_aPressed) {
answerStr = @"A";
}

if (_bPressed) {

answerStr = [answerStr stringByAppendingString:@"B"];
}

if (_cPressed) {
answerStr = [answerStr stringByAppendingString:@"C"];
}

if (_dPressed) {
answerStr = [answerStr stringByAppendingString:@"D"];
}



[_delegate didSelelctStart:[self.textField.text intValue]*60 andAnswerString:answerStr];

}


- (IBAction)closeBtnPressed:(id)sender {
[self removeFromSuperview];
}




@end


selectQuestionView = [SelectQuestionView instanceView];
selectQuestionView.frame = self.drawView.frame;
selectQuestionView.delegate = self;
[self.view addSubview:selectQuestionView];





```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


