---
layout: post
title: 帮助 WKWebView 管理 cookie
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

帮助 WKWebView 管理 cookie

https://github.com/GaoGuohao/GGWkCookie

WKWebView管理cookie是很麻烦事，经常出现 App自定义cookie的值丢失 或 更新不及时 的情况。 通过长期踩坑，总结出WKWebview管理cookie的一种方案。

原理： WKWebview支持的插入脚本的方式，在每次页面渲染前，通过插入的Js脚本检测Cookie是否存在，如不存在，将cookie重新种入的思路。

注意：因为考虑避免子域名和根域名cookie重复出现，该方法所有的Cookie值将种在 根域名上。

```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


