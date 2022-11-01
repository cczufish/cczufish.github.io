---
layout: post
title: js获取手机是否横竖屏
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

https://blog.csdn.net/luyundesign/article/details/115698381

// 检测横竖屏
var orient = ''
function checkOrient() {
    if (window.orientation == 0 ){
        orient = 'portrait 0 right';
    } else if (window.orientation == 180){
        orient = 'portrait 180 left';
    } else if (window.orientation == 90 || window.orientation == -90){
        orient = 'landscape';
    }
}
// 添加事件监听
window.addEventListener('load', function () {
    checkOrient()
    alert(orient)
})
window.addEventListener("onorientationchange" in window ? "orientationchange" : "resize", function() {
    checkOrient()
    alert(orient)
})



```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


