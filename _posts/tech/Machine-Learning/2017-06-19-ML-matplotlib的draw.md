---
layout: post
title: 用matplotlib绘制精美的图表
category: Machine-Learning
tags: python,ML,pip,Machine-learning,matplotlib
description: 
---

mac下配置matplotlib绘图

http://www.shareditor.com/blogshow/?blogId=55

绘制一元函数图像y=ax+b

```javascript

s>>> import sys
>>> reload(sys)
<module 'sys' (built-in)>
>>> sys.setdefaultencoding("utf-8")
>>> import matplotlib.pyplot as plt
>>> import numpy as np
>>> plt.figure()
<matplotlib.figure.Figure object at 0x112864d90>
>>> plt.title('Single varible')
<matplotlib.text.Text object at 0x117078e90>
>>> plt.xlabel('x')
<matplotlib.text.Text object at 0x1128f5fd0>
>>> plt.ylabel('y')
<matplotlib.text.Text object at 0x11291ba50>
>>> plt.axis(0,5,0,10)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
File "/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/matplotlib/pyplot.py", line 1379, in axis
v = ax.axis(*v, **kwargs)
File "/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/matplotlib/axes.py", line 1360, in axis
if len(v) != 4:
TypeError: object of type 'int' has no len()
>>> plt.axis([0,5,0,10])
[0, 5, 0, 10]
>>> plt.grid(True)
>>> xx = np.linspace(0,5,10)
>>> plt.plot(xx,2*xx,'g--')
[<matplotlib.lines.Line2D object at 0x1170bb0d0>]
>>> plt.show()


```

![绘制一元函数图像y=ax+b](http://www.shareditor.com/uploads/media/my-context/0001/01/d1604157156a42e12a1285f071295f6aed1fd18b.png)


绘制正弦曲线y=sin(x)

```javascript

>>> import sys 
>>> reload(sys)
<module 'sys' (built-in)>
>>> sys.setdefaultencoding("utf-8")
>>> import matplotlib.pyplot as plt
>>> import numpy as np
>>> plt.figure()
<matplotlib.figure.Figure object at 0x10e3baed0>
>>> plt.xlabel('x')
<matplotlib.text.Text object at 0x10e460150>
>>> plt.ylabel('y')
<matplotlib.text.Text object at 0x10e47d0d0>
>>> plt.axis([-12,12,-1,1])
[-12, 12, -1, 1]
>>> plt.grid(True)
>>> xx = np.linspace(-12,12,1000)
>>> plt.plot(xx,np.sin(xx),'g--',label="$sin(x)$")
[<matplotlib.lines.Line2D object at 0x10e97b110>]
>>> plt.plot(xx,np.cos(xx),'r--',label="$cos(x)$")
[<matplotlib.lines.Line2D object at 0x10e97b390>]
>>> plt.legend()
<matplotlib.legend.Legend object at 0x10e97ba50>
>>> plt.show()

```

![绘制正弦曲线y=sin(x)](http://www.shareditor.com/uploads/media/my-context/0001/01/21eaa5294afd5e281cbadfda0800273cbcb07e43.png)


绘制3D图像

```javascript



```

![绘制3D图像](http://www.shareditor.com/uploads/media/my-context/0001/01/21eaa5294afd5e281cbadfda0800273cbcb07e43.png)




---



<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

