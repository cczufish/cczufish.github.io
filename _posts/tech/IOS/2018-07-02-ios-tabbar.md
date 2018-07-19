---
layout: post
title: swift_tabbar图片，字体颜色，选中 未选中
category: iOS
tags: iOS, Alcatraz，os x,CGContextRef
description:
---


```javascript

//创建tabBar
func CreatTabBar()  {


let  homeVC  =  HomeViewController()
let colorselect = UIColor(red: 24/255.0, green: 4/255.0, blue: 56/255.0,alpha:1)
let colorNormal = UIColor(red: 143/255.0, green: 143/255.0, blue: 143/255.0,alpha:1)


let MainNav = BaseNavigationController.init(rootViewController: homeVC)
MainNav.tabBarItem.image = UIImage(named:"陪伴-选中 copy 4")
MainNav.tabBarItem.title = "陪伴"
MainNav.tabBarItem.selectedImage = UIImage(named:"home")
MainNav.tabBarItem.setTitleTextAttributes([NSAttributedStringKey.foregroundColor : colorNormal], for: .normal)
MainNav.tabBarItem.setTitleTextAttributes([NSAttributedStringKey.foregroundColor : colorselect], for: .selected)


let  ClassVC  = NTESSessionListViewController()
let ClassNav = BaseNavigationController(rootViewController:ClassVC)
ClassNav.tabBarItem.title = "家校沟通"
ClassNav.tabBarItem.image = UIImage(named:"陪伴-选中 copy 5")
ClassNav.tabBarItem.selectedImage = UIImage(named:"陪伴-选中 copy")
ClassNav.tabBarItem.setTitleTextAttributes([NSAttributedStringKey.foregroundColor : colorNormal], for: .normal)
ClassNav.tabBarItem.setTitleTextAttributes([NSAttributedStringKey.foregroundColor : colorselect], for: .selected)




let  CartVC  = CourseViewController()
let CartNav = BaseNavigationController.init(rootViewController:CartVC)
CartNav.tabBarItem.title = "课程"
CartNav.tabBarItem.image = UIImage(named:"陪伴-选中 copy 6")
CartNav.tabBarItem.selectedImage = UIImage(named:"陪伴-选中 copy 2")

CartNav.tabBarItem.setTitleTextAttributes([NSAttributedStringKey.foregroundColor : colorNormal], for: .normal)
CartNav.tabBarItem.setTitleTextAttributes([NSAttributedStringKey.foregroundColor : colorselect], for: .selected)



let  MyVC  = MyViewController()
let MyNav = BaseNavigationController(rootViewController:MyVC)
MyNav.tabBarItem.title = "我的"
MyNav.tabBarItem.image = UIImage(named:"陪伴-选中 copy 7")
MyNav.tabBarItem.selectedImage = UIImage(named:"陪伴-选中 copy 3")

MyNav.tabBarItem.setTitleTextAttributes([NSAttributedStringKey.foregroundColor : colorNormal], for: .normal)
MyNav.tabBarItem.setTitleTextAttributes([NSAttributedStringKey.foregroundColor : colorselect], for: .selected)



// 添加工具栏
items = [MainNav,ClassNav,CartNav,MyNav]
self.viewControllers = items as? [UIViewController]

//tabBar 底部工具栏背景颜色 (以下两个都行)
//        self.tabBar.barTintColor = UIColor.white
self.tabBar.backgroundColor = UIColor.white // color:rgba(24,4,56,1);


}


```









<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


