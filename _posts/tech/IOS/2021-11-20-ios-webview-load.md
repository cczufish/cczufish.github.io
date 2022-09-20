---
layout: post
title: 解决WebView 加载慢
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

一个加载网页的过程中，native、网络、后端处理、CPU都会参与，各自都有必要的工作和依赖关系；让他们相互并行处理而不是相互阻塞才可以让网页加载更快：
* WebView初始化慢，可以在初始化同时先请求数据，让后端和网络不要闲着。
* 
* 后端处理慢，可以让服务器分trunk输出，在后端计算的同时前端也加载网络静态资源。
* 
* 脚本执行慢，就让脚本在最后运行，不阻塞页面解析。
* 
* 同时，合理的预加载、预缓存可以让加载速度的瓶颈更小。
* 
* WebView初始化慢，就随时初始化好一个WebView待用。
* 
* DNS和链接慢，想办法复用客户端使用的域名和链接。
* 
* 脚本执行慢，可以把框架代码拆分出来，在请求页面之前就执行好。


window.location.href


```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

