---
layout: post
title: WKWebview、JS交互数据传值、Cookies的注入与清除
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

https://blog.csdn.net/weixin_33919950/article/details/86805042

通过window变量传值
通过第二步我们已经能正确的让JS拿到我们iOS里面的信息，但是我们发现不能及时地拿到返回值会有很大的限制，比如有这种情况，JS需要直接拿到返回值进行其他操作：
//JS代码
var info = getUserInfoString()
if info....
这就GG了，因为JS调用这个方法的时候，我们没办法直接给它返回。
我们再次曲线救国。
我们可以在调用这个方法之前，比如网页加载完毕，网页收到相应等情况下，提前准备好数据，然后写入到window里！把infoString写入window的方法：

let infoStr = getUserInfoJsonStr()
let jsStr =  "window.GLOBAL_USERINFO=\(infoStr)"
webView.evaluateJavaScript(jsStr, completionHandler: nil)
执行完毕后，window就有了一个GLOBAL_USERINFO变量，随时可取。不过网页开发者不必知道这个东西，无需为了iOS而特殊处理，仍让他调用getUserInfoString方法即可。
然后我们改写这个方法，让它能直接返回infoStr：

getUserInfoString: function () {
window.webkit.messageHandlers.OOFJS.postMessage({
fun: 'getUserInfoString',
arg: {
}
})
return window.GLOBAL_USERINFO;
},
这个方法是直接返回了我们提前写入的变量window.GLOBAL_USERINFO。
--------------------- 
作者：weixin_33919950 
来源：CSDN 
原文：https://blog.csdn.net/weixin_33919950/article/details/86805042 
版权声明：本文为博主原创文章，转载请附上博文链接！

 
 

```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

