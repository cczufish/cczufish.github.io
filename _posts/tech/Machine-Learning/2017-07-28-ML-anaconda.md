---
layout: post
title: anaconda基本操作
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---

之前报名了「深度学习30天系统实训」，昨天开始第一节课，拿着ipad连接手机热点在地铁上听完了！希望在后面的课程中坚持下去每一节课！

清华大学开源软件镜像站 我从这里下载的mac版本的anaconda https://mirrors.tuna.tsinghua.edu.cn

安装完后python 3.6，老师建议安装python3.5

http://image-net.org 

https://baike.baidu.com/item/李飞飞/7448630?fr=aladdin


ImageNet is an image database organized according to the WordNet hierarchy (currently only the nouns), in which each node of the hierarchy is depicted by hundreds and thousands of images. Currently we have an average of over five hundred images per node. We hope ImageNet will become a useful resource for researchers, educators, students and all of you who share our passion for pictures. 



图像分类：计算机视觉核心任务

图像在计算机中长什么样呢？

图片是通过像素拼接而成的，我们常说的分辨率指的就是图像像素的数量，比如分辨率为1024*768的一张图片就是在长度上的像素点数为1024个，高度768个。
每个像素点在计算机中存储的信息是他的RGB数值,将这些RGB（红、绿、蓝，组成图像的三原色，范围是从0~225）以二进制方式存在硬盘中。
读取时是通过扫描这些RGB数值，根据图片格式的不同，使用不同的扫描方式将这些像素重现在显示器画面上。
再简单点说就是用像素拼出来的图片
影像就是若干静态图片的集合，通过快速播放达到连续效果的，典型例子就是GIF格式的动画，当图片的连续播放速度超过每秒25张以上，肉眼就分不出是高速切换的效果了，也就是连续的画面。

欧氏距离

欧几里得度量（euclidean metric）（也称欧氏距离）是一个通常采用的距离定义，指在m维空间中两个点之间的真实距离，或者向量的自然长度（即该点到原点的距离）。在二维和三维空间中的欧氏距离就是两点之间的实际距离。


二维空间的公式
0ρ = sqrt( (x1-x2)^2+(y1-y2)^2 )　|x| = √( x2 + y2 )
三维空间的公式
0ρ = √( (x1-x2)^2+(y1-y2)^2+(z1-z2)^2 )　|x| = √( x2 + y2 + z2 )
n维空间的公式
n维欧氏空间是一个点集,它的每个点 X 或向量 x 可以表示为 (x[1]，x[2]，…，x[n]) ，其中 x[i](i = 1，2，…，n) 是实数，称为 X 的第i个坐标。
两个点 A = (a[1]，a[2]，…，a[n]) 和 B = (b[1]，b[2]，…，b[n]) 之间的距离 ρ(A，B) 定义为下面的公式：
ρ(A，B) =√ [ ∑( a[i] - b[i] )^2 ] (i = 1，2，…，n)
向量 x = (x[1]，x[2]，…，x[n]) 的自然长度 |x| 定义为下面的公式：
|x| = √( x[1]^2 + x[2]^2 + … + x[n]^2 )


曼哈顿距离 Manhattan Distance

曼哈顿距离是由十九世纪的赫尔曼·闵可夫斯基所创的词汇 ，是一种使用在几何度量空间的几何学用语，用以标明两个点在标准坐标系上的绝对轴距总和。出租车几何或曼哈顿距离（Manhattan Distance）是由十九世纪的赫尔曼·闵可夫斯基所创词汇 ，是种使用在几何度量空间的几何学用语，用以标明两个点在标准坐标系上的绝对轴距总和。

曼哈顿距离——两点在南北方向上的距离加上在东西方向上的距离，即d（i，j）=|xi-xj|+|yi-yj|。对于一个具有正南正北、正东正西方向规则布局的城镇街道，从一点到达另一点的距离正是在南北方向上旅行的距离加上在东西方向上旅行的距离因此曼哈顿距离又称为出租车距离，曼哈顿距离不是距离不变量，当坐标轴变动时，点间的距离就会不同。

非负性：d(i,j)≥0 距离是一个非负的数值
同一性：d(i,i)= 0 对象到自身的距离为0
对称性：d(i,j)= d(j,i)距离是一个对称函数
三角不等式：d(i,j)≤d(i,k)+d(k,j)从对象i到对象j的直接距离不会大于途经的任何其他对象k的距离


loss函数





```javascript

python --version
Python 3.6.1 :: Anaconda 4.4.0 (x86_64)


conda install python=3.5
Fetching package metadata ...
CondaHTTPError: HTTP None None for url <https://repo.continuum.io/pkgs/free/osx-64/repodata.json.bz2>
Elapsed: None

An HTTP error occurred when trying to retrieve this URL.
HTTP errors are often intermittent, and a simple retry will get you on your way.
ConnectionError(ReadTimeoutError("HTTPSConnectionPool(host='repo.continuum.io', port=443): Read timed out.",),)





```





<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

