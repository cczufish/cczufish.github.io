---
layout: post
title: ios wkwebview 如何注入css
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

How do you add CSS with Javascript?


https://stackoverflow.com/questions/707565/how-do-you-add-css-with-javascript

https://stackoverflow.com/questions/707565/how-do-you-add-css-with-javascript

https://www.jianshu.com/p/f207b8ed67f6

https://www.jianshu.com/p/52c757747866


let source = """
       var styles = `.netless-whiteboard div.editor-box{border: none ;border-color: transparent;}.netless-whiteboard div.editor-box >.operation-point-touch{display: none !important;}.netless-whiteboard div.editor-box >.operation-point-touch.right-bottom.RB{display: block !important;background: url('https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=4065216088,3626560770&fm=26&gp=0.jpg') no-repeat right bottom;height: 24px !important;width: 24px !important;background-size: 100%;background-color: transparent !important;bottom: 4px;right: 4px;}.netless-whiteboard div.editor-box >.operation-point-touch.right-bottom.RB div{display:none;}.cursor-box{border: none !important;border-radius: 0;background:url('https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=4065216088,3626560770&fm=26&gp=0.jpg') no-repeat !important;}.cursor-box img, .cursor-box-tool{display: none;}`




       var styleSheet = document.createElement("style")
       styleSheet.type = "text/css"
       styleSheet.innerText = styles
       document.head.appendChild(styleSheet)

       """
       
       let userScript = WKUserScript(source: source,
                                     injectionTime: .atDocumentEnd,
                                     forMainFrameOnly: true)
       
       let userContentController = WKUserContentController()
       userContentController.addUserScript(userScript)
       let preferences = WKPreferences()
       preferences.javaScriptEnabled = true
       //        prefere
       let configuration = WKWebViewConfiguration()
       
       configuration.userContentController = userContentController
       configuration.preferences = preferences
       
       self.boardView = WhiteBoardView(frame: .zero,configuration: configuration)
       self.boardView?.navigationDelegate = self
       
       


```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

