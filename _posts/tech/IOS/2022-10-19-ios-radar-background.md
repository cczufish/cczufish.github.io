---
layout: post
title:  ios端Charts雷达图添加背景颜色
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript


思路找到雷达图加载的那几个点绘制的方法，在前面加轨迹绘制，用的是这个组件 //  https://github.com/danielgindi/Charts

RadarChartRenderer      drawWeb

point---p1---(207.0, 175.0)
point---p2---(206.99999999999997, 38.09812499999998)
point---p1---(207.0, 175.0)
point---p2---(325.56050157572173, 106.54906249999993)
point---p1---(207.0, 175.0)
point---p2---(325.5605015757218, 243.4509374999999)
point---p1---(207.0, 175.0)
point---p2---(207.00000000000003, 311.901875)
point---p1---(207.0, 175.0)
point---p2---(88.43949842427821, 243.45093749999998)
point---p1---(207.0, 175.0)
point---p2---(88.43949842427828, 106.5490624999999)



            var radarPoints = [CGPoint]()
            
            for i in stride(from: 0, to: maxEntryCount, by: xIncrements) {
                let p = center.moving(distance: CGFloat(chart.yRange) * factor,
                                      atAngle: sliceangle * CGFloat(i) + rotationangle)
                radarPoints.append(p)
            }
            
            context.setStrokeColor(UIColor.white.cgColor)
            context.setLineWidth(1)
            context.beginPath()

            for (i,p) in radarPoints.enumerated() {
                if i == 0 {
                    context.move(to: p)
                }else{
                    context.addLine(to: p)
                }
            }
            context.addLine(to: radarPoints[0])
            context.closePath()
            context.setFillColor(UIColor.white.cgColor)
            context.fillPath()


```



---
