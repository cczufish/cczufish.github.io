---
layout: post
title: scikit-learn的一元线性回归
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---

http://www.shareditor.com/blogshow/?blogId=53

预测

```javascript

>>> import numpy as np
>>> from sklearn.linear_model import LinearRegression
>>> x = [[1],[2],[3],[4],[5],[6]]
>>> y = [[1],[2.1],[2.9],[4.2],[5.1],[5.8]]
>>> model = LinearRegression()
>>> model.fit(x,y)
LinearRegression(copy_X=True, fit_intercept=True, n_jobs=1, normalize=False)
>>> predicted = model.predict([13])[0]
/Library/Python/2.7/site-packages/sklearn/utils/validation.py:395: DeprecationWarning: Passing 1d arrays as data is deprecated in 0.17 and will raise ValueError in 0.19. Reshape your data either using X.reshape(-1, 1) if your data has a single feature or X.reshape(1, -1) if it contains a single sample.
DeprecationWarning)
>>> print predicted
[ 12.82666667]

```

画图


```javascript

>>> import matplotlib.pyplot as plt
>>> from matplotlib.font_manager import FontProperties
>>> font = FontProperties()
>>> plt.figure()
<matplotlib.figure.Figure object at 0x1125fed50>
>>> plt.title('this is title')
<matplotlib.text.Text object at 0x1152f6e90>
>>> plt.xlabel('x label')
<matplotlib.text.Text object at 0x112690fd0>
>>> plt.ylabel('y label')
<matplotlib.text.Text object at 0x1126b9a50>
>>> plt.axis([0,25,0,25])
[0, 25, 0, 25]
>>> plt.grid(true)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
NameError: name 'true' is not defined
>>> plt.grid(True)
>>> x = [[1],[2],[3],[4],[5],[6]]
>>> y = [[1],[2.1],[2.9],[4.2],[5.1],[5.8]]
>>> plt.plot(x,y,'k.')
[<matplotlib.lines.Line2D object at 0x1153380d0>]
>>> plt.show()

```

![画一元线性图像](http://www.shareditor.com/uploads/media/my-context/0001/01/9e3f34d0ea66961155a1514a31d0f193707fa5d9.png)
---

预测和作图两部分结合


```javascript

>>> import numpy as np
>>> from sklearn.linear_model import LinearRegression
>>> import matplotlib.pyplot as plt
>>> from matplotlib.font_manager import FontProperties
>>> 
>>> x = [[1],[2],[3],[4],[5],[6]]
>>> y = [[1],[2.1],[2.9],[4.2],[5.1],[5.8]]
>>> model = LinearRegression()
>>> model.fit(x,y)
LinearRegression(copy_X=True, fit_intercept=True, n_jobs=1, normalize=False)
>>> x2 = [[0],[2.5],[5.3],[9.1]]
>>> y2 = model.predict(x2)
>>> plt.figure()
<matplotlib.figure.Figure object at 0x101874a50>
>>> plt.title('linear sample')
<matplotlib.text.Text object at 0x10611bb50>
>>> plt.xlabel('x')
<matplotlib.text.Text object at 0x103509f50>
>>> plt.ylabel('y')
<matplotlib.text.Text object at 0x103532ed0>
>>> plt.axis([0,10,0,10])
[0, 10, 0, 10]
>>> plt.grid(True)
>>> plt.plot(x,y,'k.')
[<matplotlib.lines.Line2D object at 0x106c60e90>]
>>> plt.plot(x2,y2,'g--')
[<matplotlib.lines.Line2D object at 0x106c60ed0>]
>>> plt.show()

```
![画一元线性图像](http://www.shareditor.com/uploads/media/my-context/0001/01/5817c1dfb64abacc3811b88ec69931bdd8ff85fc.png)




<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

