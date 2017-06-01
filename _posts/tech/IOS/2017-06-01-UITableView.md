---
layout: post
title: UITableView相关方法
category: iOS
tags: iOS, Alcatraz，os x,Calendar,UITableView
description:
---

UITableView相关方法


```javascript

<UITableViewDelegate,UITableViewDataSource>

- (void)initUI
{


UITableView *tableView = [[UITableView alloc] initWithFrame:CGRectMake(0, 0, 320, 460)     style:UITableViewStylePlain];
tableView.delegate = self; //代理
tableView.dataSource = self;
[self.view addSubview:tableView];

//分割线颜色
tableView.separatorColor = [UIColor redColor];
//分割线类型
tableView.separatorStyle = UITableViewCellSeparatorStyleNone;
//行高
//背景颜色
tableView.backgroundColor = [UIColor orangeColor];
//_tableView.backgroundColor = [UIColor colorWithPatternImage:[UIImage imageNamed:@"2_4.jpg"]];
//背景图片
UIImageView* imageView = [[UIImageView alloc] initWithFrame:CGRectMake(0, 0, 320, 460)];
imageView.image = [UIImage imageNamed:@"2_4.jpg"];
tableView.backgroundView = imageView;

}




#pragma mark - Table view data source

- (NSInteger)numberOfSectionsInTableView:(UITableView *)tableView {
return 1;
}

- (NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section {
return 3;
}

- (CGFloat)tableView:(UITableView *)tableView heightForRowAtIndexPath:(NSIndexPath *)indexPath
{
return 240;
}

- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
//    声明静态字符串型对象，用来标记重用单元格
static NSString *TableSampleIdentifier = @"menu";
//    用TableSampleIdentifier表示需要重用的单元
CalendarCell *cell = [tableView dequeueReusableCellWithIdentifier:TableSampleIdentifier];
//    如果如果没有多余单元，则需要创建新的单元
if (cell == nil) {
cell = [[CalendarCell alloc] initWithStyle:UITableViewCellStyleDefault reuseIdentifier:TableSampleIdentifier];
}


return cell;
}

- (void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath
{

}



```






<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


