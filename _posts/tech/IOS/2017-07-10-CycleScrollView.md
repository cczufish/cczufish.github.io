---
layout: post
title: 做题，图片等场景下的循环滚动的scrollview
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---

做题，图片等场景下的循环滚动的scrollview


```javascript



// 循环滚动的scrollview，传入页面的个数，第一页不让向左滚动，最后一页不让向右滚动，中间页面可以左右翻页。

#import <UIKit/UIKit.h>

@protocol CycleScrollViewDelegate;
@protocol CycleScrollViewDatasource;


@interface CycleScrollView : UIView<UIScrollViewDelegate>
{
UIScrollView *_scrollView;

id<CycleScrollViewDelegate> delegate;
id<CycleScrollViewDatasource> datasource;

NSInteger _totalPages;
NSInteger _curPage;

NSMutableArray *_curViews;
}

@property (nonatomic,readonly) UIScrollView *scrollView;
@property (nonatomic,assign) NSInteger currentPage;
@property (nonatomic,assign,setter = setDataource:) id<CycleScrollViewDatasource> datasource;
@property (nonatomic,assign,setter = setDelegate:) id<CycleScrollViewDelegate> delegate;

- (void)reloadData:(NSInteger)currentPage;

@end

@protocol XLCycleScrollViewDelegate <NSObject>

@end

@protocol XLCycleScrollViewDatasource <NSObject>

@required
- (NSInteger)numberOfPages;
- (UIView *)pageAtIndex:(NSInteger)index;

@end



#import "CycleScrollView.h"
#define LOADDATA_FLAG 300


@implementation CycleScrollView


@synthesize scrollView = _scrollView;
@synthesize currentPage = _curPage;
@synthesize datasource = _datasource;
@synthesize delegate = _delegate;


- (id)initWithFrame:(CGRect)frame
{
self = [super initWithFrame:frame];
if (self) {
// Initialization code
_scrollView = [[UIScrollView alloc] initWithFrame:self.bounds];
_scrollView.delegate = self;
_scrollView.contentSize = CGSizeMake(self.bounds.size.width * 3, self.bounds.size.height);
_scrollView.showsHorizontalScrollIndicator = NO;
_scrollView.contentOffset = CGPointMake(self.bounds.size.width, 0);
_scrollView.pagingEnabled = YES;
_scrollView.backgroundColor = RGB(237, 237, 237);

[self addSubview:_scrollView];

_curPage = 0;

}
return self;
}



- (void)setDataource:(id<XLCycleScrollViewDatasource>)dataSource
{
_datasource = dataSource;
[self reloadData:LOADDATA_FLAG];
}

- (void)reloadData:(NSInteger)currentPage
{
_totalPages = [_datasource numberOfPages];
if (_totalPages == 0) {
return;
}
[self loadData:currentPage];
}

- (void)loadData:(NSInteger)currentPage
{

//从scrollView上移除所有的subview
NSArray *subViews = [_scrollView subviews];
//    DLog(@"%@",subViews);

if([subViews count] != 0) {
[subViews makeObjectsPerformSelector:@selector(removeFromSuperview)];
}

if (currentPage == LOADDATA_FLAG) {
[self getDisplayImagesWithCurpage:_curPage];

}else{
_curPage = currentPage;
[self getDisplayImagesWithCurpage:_curPage];
}


for (int i = 0; i < 3; i++) {
UIView *v = [_curViews objectAtIndex:i];

v.frame = CGRectOffset(v.frame, v.frame.size.width * i, 0);
[_scrollView addSubview:v];
}

[_scrollView setContentOffset:CGPointMake(_scrollView.frame.size.width, 0)];
}

- (void)getDisplayImagesWithCurpage:(int)page {

int pre = [self validPageValue:_curPage-1];
int last = [self validPageValue:_curPage+1];

if (!_curViews) {
_curViews = [[NSMutableArray alloc] init];
}

[_curViews removeAllObjects];

[_curViews addObject:[_datasource pageAtIndex:pre]];
[_curViews addObject:[_datasource pageAtIndex:page]];
[_curViews addObject:[_datasource pageAtIndex:last]];
}

- (int)validPageValue:(NSInteger)value {

if(value == -1)
value = _totalPages - 1;

if(value == _totalPages)
{
value = 0;
}

return value;

}


#pragma mark - UIScrollViewDelegate
- (void)scrollViewDidScroll:(UIScrollView *)aScrollView {
int x = aScrollView.contentOffset.x;

//判断不让 循环滚动
if ((_curPage == 0) && ((x+0.001)< aScrollView.frame.size.width)) {

[aScrollView setContentOffset:CGPointMake(aScrollView.frame.size.width, 0) animated:NO];

}else if (((_curPage + 1 )== _totalPages) && ((x+0.001) > aScrollView.frame.size.width)) {

[aScrollView setContentOffset:CGPointMake(aScrollView.frame.size.width, 0) animated:NO];

}else{

//往右翻一张
if(x >= (2*self.frame.size.width)) {
_curPage = [self validPageValue:_curPage+1];
[self loadData:LOADDATA_FLAG];
}


//往左翻
if(x <= 0) {
_curPage = [self validPageValue:_curPage-1];
[self loadData:LOADDATA_FLAG];
}
}

}

- (void)scrollViewDidEndDecelerating:(UIScrollView *)aScrollView {

[_scrollView setContentOffset:CGPointMake(_scrollView.frame.size.width, 0) animated:NO];

}










```







<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


