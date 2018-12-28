---
layout: post
title: go  梳排序(Comb sort) 
category: Go
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

https://www.cnblogs.com/manji/p/4903990.html

```javascript

package main

import "fmt"

/*

梳排序还是基于冒泡排序,与冒泡不同的是,梳排序比较的是固定距离处的数的比较和交换,类似希尔那样

这个固定距离是待排数组长度除以1.3得到近似值,下次则以上次得到的近似值再除以1.3,直到距离小至3时,以1递减

不太好描述,还是看例子吧

假设待数组[8 4 3 7 6 5 2 1]

待排数组长度为8,而8÷1.3=6,则比较8和2,4和1,并做交换

[8 4 3 7 6 5 2 1]

[8 4 3 7 6 5 2 1]

交换后的结果为

[2 1 3 7 6 5 8 4]

第二次循环,更新间距为6÷1.3=4,比较2和6,1和5,3和8,7和4

[2 1 3 7 6 5 8 4]

[2 1 3 7 6 5 8 4]

[2 1 3 7 6 5 8 4]

[2 1 3 7 6 5 8 4]

只有7和4需要交换,交换后的结果为

[2 1 3 4 6 5 8 7]

第三次循环,更新距离为3,没有交换

第四次循环,更新距离为2,没有交换

第五次循环,更新距离为1,三处交换

[2 1 3 4 6 5 8 7]

[2 1 3 4 6 5 8 7]

[2 1 3 4 6 5 8 7]

三处交换后的结果为[1 2 3 4 5 6 7 8]

交换后排序结束,顺序输出即可得到[1 2 3 4 5 6 7 8]


*/
func main() {
var array = [] int {2,3,4,5,1}
fmt.Println(array)
CombSort(array)
fmt.Println(array)
}

func CombSort(array []int) {
gapValue := len(array)
swapCount := 1
for gapValue > 1 && swapCount != 0 {
if gapValue != 1{
gapValue = int(float64(gapValue)/float64(1.3))
}
swapCount = 0
firstItem := 0
secondItem := gapValue
for secondItem != len(array) {
if array[firstItem] > array[secondItem]{
array[firstItem],array[secondItem] = array[secondItem],array[firstItem]
swapCount += 1
}
firstItem += 1
secondItem += 1
}
}
}



```

---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

