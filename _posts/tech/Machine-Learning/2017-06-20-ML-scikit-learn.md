---
layout: post
title: scikit-learn求解多项式回归问题
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---

http://www.shareditor.com/blogshow/?blogId=56

用线性回归住房价格样本

```javascript

>>> import sys
>>> reload(sys)
<module 'sys' (built-in)>
>>> sys.setdefaultencoding("utf-8")
>>> import matplotlib.pyplot as plt
>>> import numpy as np
>>> plt.figure()
<matplotlib.figure.Figure object at 0x106565e90>
>>> plt.xlabel('x')
<matplotlib.text.Text object at 0x106e1a110>
>>> plt.ylabel('y')
<matplotlib.text.Text object at 0x106e37090>
>>> plt.axis(30,400,100,400)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
File "/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/matplotlib/pyplot.py", line 1379, in axis
v = ax.axis(*v, **kwargs)
File "/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/matplotlib/axes.py", line 1360, in axis
if len(v) != 4:
TypeError: object of type 'int' has no len()
>>> plt.axis([30,400,100,400])
[30, 400, 100, 400]
>>> plt.grid(True)
>>> 
>>> xx = [[50],[100],[150],[200],[250],[300]]
>>> yy = [[150],[200],[250],[280],[310],[330]]
>>> plt.plot(xx,yy,'k.')
[<matplotlib.lines.Line2D object at 0x10adab150>]
>>> plt.show()


```

![用线性回归住房价格样本图像](http://www.shareditor.com/uploads/media/my-context/0001/01/06bb15f689c21e7b1bbd25d6832cd4ab6f963947.png)


用二次回归住房价格样本

```javascript

>>> import sys
>>> reload(sys)
<module 'sys' (built-in)>
>>> sys.setdefaultencoding("utf-8")
>>> import matplotlib.pyplot as plt
>>> import numpy as np
>>> from sklearn.linear_model import LinearRegression
>>> from sklearn.preprocessing import PolynomialFeatures
>>> 
>>> plt.figure()
<matplotlib.figure.Figure object at 0x101aeeed0>
>>> plt.title('single variable')
<matplotlib.text.Text object at 0x107cdbcd0>
>>> plt.xlabel('x')
<matplotlib.text.Text object at 0x103caae90>
>>> plt.ylabel('y')
<matplotlib.text.Text object at 0x107cb4e10>
>>> plt.axis([30,400,100,400])
[30, 400, 100, 400]
>>> plt.grid(True)
>>> 
>>> x = [[50],[100],[150],[200],[250],[300]]
>>> y = [[150],[200],[250],[280],[310],[330]]
>>> x_test = [[250],[300]]
>>> y_test = [[310],[330]]
>>> plt.plot(x,y,'k.')
[<matplotlib.lines.Line2D object at 0x107d18e90>]
>>> 
>>> model = LinearRegression()
>>> model.fit(x,y)
LinearRegression(copy_X=True, fit_intercept=True, n_jobs=1, normalize=False)
>>> x2 = [[30],[400]]
>>> y2 = model.predict[x2]
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: 'instancemethod' object has no attribute '__getitem__'
>>> y2 = model.predict(x2)
>>> plt.plot(x2,y2,'g--')
[<matplotlib.lines.Line2D object at 0x10185ea10>]
>>> xx = np.linspace(30,400,100)
>>> quadratic_featurizer = PolynomialFeatures(degree=2)
>>> X_train_quadratic = quadratic_featurizer.fit_transform(x)
>>> xx_quadratic = quadratic_featurizer.transform(xx.reshape(xx.shape[0],1))
>>> regressor_quadratic = LinearRegression()
>>> regressor_quadratic.fit(x_train_quadratic,y)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
NameError: name 'x_train_quadratic' is not defined
>>> regressor_quadratic.fit(X_train_quadratic,y)
LinearRegression(copy_X=True, fit_intercept=True, n_jobs=1, normalize=False)
>>> plt.plot(xx,regressor_quadratic.predict(xx_quadratic),'r-')
[<matplotlib.lines.Line2D object at 0x107d2be90>]
>>> print 'yiyuanxianxinghuigui r-squared' ,model.score(x_test,y_test)
yiyuanxianxinghuigui r-squared 0.0755555555556
>>> X_test_quadratic = quadratic_feturizer.transform(x_test)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
NameError: name 'quadratic_feturizer' is not defined
>>> X_test_quadratic = quadratic_featurizer.transform(x_test)
>>> print 'er ci hui gui r-squraed',regressor_quadratic.score(X_test_quadratic,y_test)
er ci hui gui r-squraed 0.999336734694
>>> plt.show(0
... 
... 
... ;
File "<stdin>", line 4
;
^
SyntaxError: invalid syntax
>>> plt.show()


```

![用二次回归住房价格样本图像](http://www.shareditor.com/uploads/media/my-context/0001/01/f6f64375ff641a2d17ce3332d0e4f211fdc0be39.png)



<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

