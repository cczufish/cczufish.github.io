---
layout: post
title: scikit-learn求解多元线性回归问题
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---

http://www.shareditor.com/blogshow/?blogId=54


```javascript

>>> from numpy.linalg import inv
>>> from numpy import dot,transpose
>>> x = [[1,1,1],[1,1,2],[1,2,1]]
>>> y = [[6],[9],[8]]
>>> print dot(inv(dot(transpose(x),x),dot(transpose(x),y)))
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: inv() takes exactly 1 argument (2 given)
>>> print dot(inv(dot(transpose(x),x)),dot(transpose(x),y))
[[ 1.]
[ 2.]
[ 3.]]
>>> from numpy.linalg import lstsq
>>> print lstsq(x,y)[0]
[[ 1.]
[ 2.]
[ 3.]]
>>> from sklearn.linear_model import LinearRegression
x>>> x = [[1,1,1],[1,1,2],[1,2,1]]
>>> y = [[6,[9],[8]]
... 
... 
... 
... ;
File "<stdin>", line 5
;
^
SyntaxError: invalid syntax
>>> y - [[6],[9],[8]]
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for -: 'list' and 'list'
>>> y = [[6],[9],[8]]
>>> model = LinearRegression()
>>> model.fit(x,y)
LinearRegression(copy_X=True, fit_intercept=True, n_jobs=1, normalize=False)
>>> x2 = [[1,3,5]]
>>> y2 = model.predict(x2)
>>> print y2
[[ 22.]]

```

设计二元一次方程：y=1+2x1+3x2

取样本为(1,1,1),(1,1,2),(1,2,1)，计算得y=(6,9,8)

注意：这里面常数项1相当于1*x0，只不过这里的x0永远取1


所以我们的

X = [[1,1,1],[1,1,2],[1,2,1]]

y = [[6],[9],[8]]

刚好y=1+2x1+3x2=1+2*3+3*5=22




<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

