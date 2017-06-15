---
layout: post
title: mac下配置matplotlib绘图和pip
category: Machine-Learning
tags: python,ML,pip,Machine-learning,matplotlib
description: 
---

mac下配置matplotlib绘图



[mac下配置matplotlib绘图](http://blog.csdn.net/gaixm/article/details/50299865)



```javascript

sudo curl -O https://bootstrap.pypa.io/get-pip.py

sudo python get-pip.py

sudo pip install matplotlib


python2.7 -c 'import matplotlib; print matplotlib.__version__, matplotlib.__file__'
1.3.1 /System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/matplotlib/__init__.pyc
jingruijiaoyudeMacBook-Air:~ jingruijiaoyu$ python /Users/jingruijiaoyu/Desktop/matplotlib.py 



Python 2.7.10 (default, Feb  7 2017, 00:08:15) 
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.34)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy as np
>>> import matplotlib.pyplot as plt 
>>> n = 5
>>> menMeans = (20,35,30,35,27)
>>> menStd = (2,3,4,1,2)
>>> ind = np.arange(N)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
NameError: name 'N' is not defined
>>> ind = np.arange(n)
>>> width = 0.35
>>> fig,ax = plt.subplots()
>>> rects1 = ax.bar(ind,menMeans,width,color='r',yerr=menStd)
>>> womenMeans = (25,32,34,20,25)
>>> womenStd = (3,5,2,3,3)
>>> rects = ax.bar(ind+width,womenMeans,width,color='y',yerr=womenStd)
>>> ax.set_ylabel('Scores')
<matplotlib.text.Text object at 0x108ff51d0>
>>> ax.set_title('Scores by group and gender')
<matplotlib.text.Text object at 0x10bae3bd0>
>>> ax.set_xticks(ind+windth)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
NameError: name 'windth' is not defined
>>> ax.set_xticks(ind+width)
[<matplotlib.axis.XTick object at 0x108f418d0>, <matplotlib.axis.XTick object at 0x108fe9b90>, <matplotlib.axis.XTick object at 0x10c35ad10>, <matplotlib.axis.XTick object at 0x10c363450>, <matplotlib.axis.XTick object at 0x10c363b90>]
>>> ax.set_xticklabels('G1','G2','G3','G4','G5')
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: set_xticklabels() takes at most 4 arguments (6 given)
>>> ax.set_xticklabels(('G1','G2','G3','G4','G5'))
[<matplotlib.text.Text object at 0x10bacf710>, <matplotlib.text.Text object at 0x10bada5d0>, <matplotlib.text.Text object at 0x10c3632d0>, <matplotlib.text.Text object at 0x10c363a10>, <matplotlib.text.Text object at 0x10c36f190>]
>>> ax.legend((rects[0],rects2[0]),('Men','Women'))
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
NameError: name 'rects2' is not defined
>>> ax.legend( (rects1[0],rects2[0]), ('Men','Women'))
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
NameError: name 'rects2' is not defined
>>> ax.legend( (rects1[0],rects[0]), ('Men','Women'))
<matplotlib.legend.Legend object at 0x10c35a750>
>>> def autolabel(rectss):
...     for rect in rectss:
...             height = rect.get_height()
...             ax.text(rect.get(x)+rect.get_width()/2,1.05*height,'%d'%int(height),ha='center',va='bottom')
... 
>>> autolabel(rects1)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
File "<stdin>", line 4, in autolabel
AttributeError: 'Rectangle' object has no attribute 'get'
>>> def autolabel(rectss):
...     for rect in rectss:
...             height = rect.get_height()
...             ax.text(rect.get_x()+rect.get_width()/2,1.05*height,'%d'%int(height),ha='center',va='bottom')
... 
>>> autolabel(rects1)
>>> autolabel(rects)
>>> plt.show()




```

![mac下配置matplotlib绘图](http://oolkmbv7h.bkt.clouddn.com/A5331081-B7E2-4958-8C12-4860641B73FC.png)





---



<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

