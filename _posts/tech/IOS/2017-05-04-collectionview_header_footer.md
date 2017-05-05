---
layout: post
title: UICollectionview添加header和footer
category: iOS
tags: iOS,UICollectionview，Header_Footer
description:
---

UICollectionview添加header和footer

```javascript

@interface CollectionHeaderReusableView : UICollectionReusableView


@property (weak, nonatomic) IBOutlet UICollectionView *personCollectView;
@property (weak, nonatomic) IBOutlet UICollectionViewFlowLayout *personCellLayout;


@interface MeViewController ()<UICollectionViewDataSource,UICollectionViewDelegate>

@end

@implementation MeViewController
static NSString * const reuseIdentifier = @"reuseIdentifier";
static NSString * const btnReuseIdentifier = @"btnReuseIdentifier";

static NSString * const reuseIdentifierHeader = @"MYHeaderCell";
static NSString * const reuseIdentifierFooter = @"MYFooterCell";

- (void)viewDidLoad {
[super viewDidLoad];

self.view.backgroundColor = mRGBToColor(0x101010);

w = WIDTH;
h = HEIGHT;
titalArray = @[@"服务记录",@"二手发布记录",@"家政服务记录",@"废品回收记录",@"团购记录",@"积分记录"];

[self.personCollectView registerClass:[CollectionViewCell class] forCellWithReuseIdentifier:reuseIdentifier];

[self.personCollectView registerNib:[UINib nibWithNibName:@"CollectionHeaderReusableView" bundle:nil] forSupplementaryViewOfKind:UICollectionElementKindSectionHeader withReuseIdentifier:reuseIdentifierHeader];

[self.personCollectView registerNib:[UINib nibWithNibName:@"CollectionFooterReusableView" bundle:nil] forSupplementaryViewOfKind:UICollectionElementKindSectionFooter withReuseIdentifier:reuseIdentifierFooter];

self.personCollectView.dataSource = self;
self.personCollectView.delegate = self;


self.navBar.backToParentBtn.hidden = YES;
self.barTitle = @"个人中心";
}

#pragma mark <UICollectionViewDataSource>

- (NSInteger)collectionView:(UICollectionView *)collectionView numberOfItemsInSection:(NSInteger)section {

return 6;
}

- (UICollectionViewCell *)collectionView:(UICollectionView *)collectionView cellForItemAtIndexPath:(NSIndexPath *)indexPath {


CollectionViewCell *cell =  [collectionView dequeueReusableCellWithReuseIdentifier:reuseIdentifier forIndexPath:indexPath];

cell.titalLabel.text = [titalArray objectAtIndex:indexPath.row];
cell.img.hidden = YES;


return cell;


}


//定义每个UICollectionView 的大小
- (CGSize)collectionView:(UICollectionView *)collectionView layout:(UICollectionViewLayout*)collectionViewLayout sizeForItemAtIndexPath:(NSIndexPath *)indexPath
{

return CGSizeMake((w-1)/2.0, 100);

}



- (void)collectionView:(UICollectionView *)collectionView didSelectItemAtIndexPath:(NSIndexPath *)indexPath
{

if (indexPath.row == 0) {

}else if (indexPath.row == 1) { //二手
[self.navigationController pushViewController:[[MyPostViewController alloc]init] animated:YES];
}

else if (indexPath.row ==2) {

MyRepairViewController * repairVC =[[MyRepairViewController alloc]init];
repairVC.feedBackClass = FeedBackClassIsJiaZheng;
[self.navigationController pushViewController:repairVC animated:YES];

}else if (indexPath.row == 3) {

[self.navigationController pushViewController:[[FeiPinController alloc]init] animated:YES];

}else if (indexPath.row == 4) {

[self.navigationController pushViewController:[[TuanGoJiController alloc]init] animated:YES];


}
else if (indexPath.row == 5) { //积分
IntegralViewController * intergralCV =[[IntegralViewController alloc]initWithNibName:@"IntegralViewController" bundle:nil];
[self.navigationController pushViewController:intergralCV animated:YES];
}

}



- (UICollectionReusableView *)collectionView:(UICollectionView *)collectionView viewForSupplementaryElementOfKind:(NSString *)kind atIndexPath:(NSIndexPath *)indexPath{

UICollectionReusableView *supplementaryView;

if ([kind isEqualToString:UICollectionElementKindSectionHeader]){
CollectionHeaderReusableView *view = (CollectionHeaderReusableView *)[collectionView dequeueReusableSupplementaryViewOfKind:UICollectionElementKindSectionHeader withReuseIdentifier:reuseIdentifierHeader forIndexPath:indexPath];
view.meVC = self;
supplementaryView = view;

}
else
if ([kind isEqualToString:UICollectionElementKindSectionFooter]){
CollectionFooterReusableView *view = (CollectionFooterReusableView *)[collectionView dequeueReusableSupplementaryViewOfKind:UICollectionElementKindSectionFooter withReuseIdentifier:reuseIdentifierFooter forIndexPath:indexPath];
view.meVC = self;

supplementaryView = view;

}

return supplementaryView;
}


- (CGSize)collectionView:(UICollectionView *)collectionView layout:(UICollectionViewLayout*)collectionViewLayout referenceSizeForHeaderInSection:(NSInteger)section{
CGFloat screenWidth = [UIScreen mainScreen].bounds.size.width;
return CGSizeMake(screenWidth, 120);
}

- (CGSize)collectionView:(UICollectionView *)collectionView layout:(UICollectionViewLayout*)collectionViewLayout referenceSizeForFooterInSection:(NSInteger)section{
CGFloat screenWidth = [UIScreen mainScreen].bounds.size.width;
return CGSizeMake(screenWidth, 80);
}


```
---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


