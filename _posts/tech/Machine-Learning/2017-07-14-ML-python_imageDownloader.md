---
layout: post
title:  （转）python爬虫实战——5分钟做个图片（表情包）自动下载器
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---

http://www.jianshu.com/p/19c846daccb3


用这个下载了好多表情包。。。。。。。  先下载了300个表情包。。。。。 网盘地址  http://pan.baidu.com/s/1pKTKkGz

```javascript

#_*_ coding:utf-8 _*_

import re
import requests

def downloadPic(html,keyword):
pic_url = re.findall('"objURL":"(.*?)",',html,re.S)
i = 0
print '找到关键词：'+keyword+'的图片,现在开始下载图片...'
for each in pic_url:
print '正在下载第'+str(i+1)+'张图片，图片地址：'+str(each)
try:
pic = requests.get(each,timeout=10)
except requests.exceptions.ConnectionError:
print '错误当前图片无法下载'
continue

string = 'pictures\\'+keyword+'_'+str(i)+'.jpg'

fp = open(string.decode('utf-8').encode('cp936'),'wb')
fp.write(pic.content)
fp.close()
i += 1


if __name__ == '__main__':
word = raw_input("Input key word:")
url = 'http://image.baidu.com/search/flip?tn=baiduimage&ie=utf-8&word='+word+'&ct=201326592&v=flip'
result = requests.get(url)
downloadPic(result.text,word)







```


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

