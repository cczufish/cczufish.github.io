---
layout: post
title: go  json to struct
category: Go
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---


```javascript

package main

import (
"encoding/json"
"fmt"
)

/*
{"name":"张三","Age":18,"HIgh":true,"class":{"Name":"1班","Grade":3}}

*/

type Stu struct {
Name  string `json:"name"`
Age   int
HIgh  bool
sex   string
Class *Class `json:"class"`
}

type Class struct {
Name  string
Grade int
}

func main() {
//实例化一个数据结构，用于生成json字符串
stu := Stu{
Name: "张三",
Age:  18,
HIgh: true,
sex:  "男",
}

//指针变量
cla := new(Class)
cla.Name = "1班"
cla.Grade = 3
stu.Class=cla

//Marshal失败时err!=nil
jsonStu, err := json.Marshal(stu)
if err != nil {
fmt.Println("生成json字符串错误")
}

//jsonStu是[]byte类型，转化成string类型便于查看
fmt.Println(string(jsonStu))
}


```

---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

