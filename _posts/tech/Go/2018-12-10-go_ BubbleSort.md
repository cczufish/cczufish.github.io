---
layout: post
title: go  冒泡排序（BubbleSort)
category: Go
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

https://www.cnblogs.com/manji/p/4903990.html

```javascript

package main

import "fmt"

/*

冒泡排序（Bubble Sort），是一种计算机科学领域的较简单的排序算法。
它重复地走访过要排序的元素列，依次比较两个相邻的元素，如果他们的顺序（如从大到小、首字母从A到Z）错误就把他们交换过来。走访元素的工作是重复地进行直到没有相邻元素需要交换，也就是说该元素已经排序完成。
*/

func main() {

var num = []int{3,5,12,0,4}
fmt.Println(num)
BubbleSort(num)
fmt.Println(num)
}

func BubbleSort(array []int){
swapCount := 1
for swapCount > 0{
swapCount = 0
for itemIndex := 0;itemIndex < len(array)-1;itemIndex ++ {
if array[itemIndex] > array[itemIndex + 1]{
array[itemIndex],array[itemIndex+1]  = array[itemIndex + 1],array[itemIndex]
swapCount += 1
}
}
}
}


GOROOT=/usr/local/go #gosetup
GOPATH=/Users/yushuhui/go #gosetup
/usr/local/go/bin/go build -i -o /private/var/folders/b6/zldllx_15jd7f3542c8q5s300000gn/T/___go_build_BubbleSort_go /Users/yushuhui/go/src/awesomeProject1/BubbleSort.go #gosetup
/private/var/folders/b6/zldllx_15jd7f3542c8q5s300000gn/T/___go_build_BubbleSort_go #gosetup
[3 5 12 0 4]
[0 3 4 5 12]

Process finished with exit code 0







```

---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

