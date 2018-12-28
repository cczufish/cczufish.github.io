---
layout: post
title: go  鸡尾酒排序Cocktail sort
category: Go
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

https://www.cnblogs.com/manji/p/4903990.html

```javascript

package main

import "fmt"

/*

经典排序算法 - 鸡尾酒排序Cocktail sort

鸡尾酒排序基于冒泡排序,双向循环

还是看例子吧,给定待排数组[2 3 4 5 1]

第一趟过去时的每一步

第一步迭代,2 < 3不换

[2 3 4 5 1]



第二步迭代,3 < 4不换

[2 3 4 5 1]



第三步迭代,4 < 5不换

[2 3 4 5 1]



第四步迭代,5 > 1交换

[2 3 4 1 5]



第一趟回来时的第一步,鸡尾酒一次到头后就回返回来,再到头后再过去,来回比,一个来回能排两个数字

第五步迭代,1 < 5不交换

[2 3 4 1 5]



第六步迭代,1 < 4交换

[2 3 1 4 5]



第七步迭代,1 < 3交换

[2 1 3 4 5]



第八步迭代,2 > 1交换

[1 2 3 4 5]



排序完毕,顺序输出结果即可得[ 1 2 3 4 5]



如何判断排序结束了?

假如一趟来回没有交换任何数字,则表示该数组已经有序了,可以设置了个变量表示有没有交换过



*/
func main() {
var array = [] int {2,3,4,5,1}
fmt.Println(array)
CocktailSort(array)
fmt.Println(array)
}


func CocktailSort(array []int){
swapCount := 1
for swapCount > 0 {
swapCount = 0
for itemIndex := 0;itemIndex < len(array)-1;itemIndex++{
if array[itemIndex] > array[itemIndex + 1]{
array[itemIndex],array[itemIndex+1] = array[itemIndex+1],array[itemIndex]
swapCount += 1
}
}
for itemIndex := len(array) - 1;itemIndex > 0;itemIndex--{
if array[itemIndex] < array[itemIndex - 1]{
array[itemIndex],array[itemIndex-1] = array[itemIndex-1],array[itemIndex]
swapCount += 1
}
}
}
}





```

---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

