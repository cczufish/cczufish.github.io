---
layout: post
title:  swift - UIlabel 字体渐变色 
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript


https://blog.csdn.net/qqwyuli/article/details/123106989


     ///颜色渐变
    func textLabel(){
        let label = UILabel()
        self.view.addSubview(label)
        label.font = UIFont.systemFont(ofSize: 30)
        label.frame = CGRect(x: 100, y: 300, width: 200, height: 50)
        let text = "文字添加投影"
        
        ///添加阴影
        let shadow = NSShadow()
        shadow.shadowBlurRadius = 6
        shadow.shadowOffset = CGSize(width: -3, height: 5)
        shadow.shadowColor = UIColor.orange
        let attr = NSMutableAttributedString(string: text)
        attr.addAttributes([NSAttributedString.Key.shadow : shadow], range: NSMakeRange(0, attr.length))
        label.attributedText = attr
        
        ///字体渐变色
        label.textColor = UIColor(patternImage: getGradientImage(size: label.bounds.size))
    }
    
    ///生成渐变颜色图片
    func getGradientImage(size:CGSize) -> UIImage{
        UIGraphicsBeginImageContextWithOptions(size, false, UIScreen.main.scale)
        guard let context = UIGraphicsGetCurrentContext() else{return UIImage()}
        let colorSpace = CGColorSpaceCreateDeviceRGB()
        ///设置渐变颜色
        let gradientRef = CGGradient(colorsSpace: colorSpace, colors: [UIColor.black.cgColor,UIColor.white.cgColor] as CFArray, locations: nil)!
        let startPoint = CGPoint(x: size.width / 2, y: 0)
        let endPoint = CGPoint(x: size.width / 2, y: size.height)
        context.drawLinearGradient(gradientRef, start: startPoint, end: endPoint, options: CGGradientDrawingOptions(arrayLiteral: .drawsBeforeStartLocation,.drawsAfterEndLocation))
        let gradientImage = UIGraphicsGetImageFromCurrentImageContext()
        UIGraphicsEndImageContext()
        return gradientImage ?? UIImage()
    }





```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

