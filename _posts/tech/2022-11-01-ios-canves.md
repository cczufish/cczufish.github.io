---
layout: post
title: canvas的宽高怎么自适应?
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript
https://www.zhihu.com/question/36458228

window.addEventListener("resize", resizeCanvas, false);

function resizeCanvas() {
    w = canvas.width = window.innerWidth;
    h = canvas.height = window.innerHeight;
}

https://blog.csdn.net/m0_48940868/article/details/116503331

```



---


