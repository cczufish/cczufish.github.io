---
layout: post
title: swift 使用UISearchBar和UITableView实现搜索功能
category: 技术
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

override func viewWillDisappear(_ animated: Bool) {
super.viewWillDisappear(animated)
searchController.isActive = false
//  searchController.searchBar.resignFirstResponder()
}



UISearchResultsUpdating,UISearchControllerDelegate

i self.automaticallyAdjustsScrollViewInsets = false;//不加的话，table会下移
self.edgesForExtendedLayout = [];//不加的话，UISearchBar返回后会上移

//创建UISearchController
searchController = UISearchController(searchResultsController: nil)
//设置代理
searchController.delegate = self
searchController.searchResultsUpdater = self

//设置UISearchController的显示属性，以下3个属性默认为YES
//搜索时，背景变暗色
searchController.dimsBackgroundDuringPresentation = false
//搜索时，背景变模糊
searchController.obscuresBackgroundDuringPresentation = false
//隐藏导航栏
searchController.hidesNavigationBarDuringPresentation = false

searchController.searchBar.frame = CGRect(x: searchController?.searchBar.frame.origin.x ?? 0.0, y: searchController?.searchBar.frame.origin.y ?? 0.0, width: searchController?.searchBar.frame.size.width ?? 0.0, height: 44.0)

// 添加 searchbar 到 headerview
tableView.tableHeaderView = searchController.searchBar


//测试UISearchController的执行过程
func willPresentSearchController(_ searchController: UISearchController) {
print("willPresentSearchController")
}

func didPresentSearchController(_ searchController: UISearchController) {
print("didPresentSearchController")
}

func willDismissSearchController(_ searchController: UISearchController) {
print("willDismissSearchController")
}

func didDismissSearchController(_ searchController: UISearchController) {
print("didDismissSearchController")
}

func presentSearchController(_ searchController: UISearchController) {
print("presentSearchController")
}


func updateSearchResults(for searchController: UISearchController) {

print("updateSearchResultsForSearchController")
let searchString = self.searchController?.searchBar.text

let preicate = NSPredicate(format:"SELF CONTAINS %@", searchString ?? "")

//过滤数据
filterData = NSMutableArray(array: nameArray.filtered(using: preicate))
//刷新表格
tableView.reloadData()
}



```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

