---
layout: post
title: Scikit-learn
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---

https://www.leiphone.com/news/201701/ZJMTak4Y8ch3Nwd0.html
Scikit-learn项目最早由数据科学家 David Cournapeau 在 2007 年发起，需要NumPy和SciPy等其他包的支持，是Python语言中专门针对机器学习应用而发展起来的一款开源框架。

和其他众多的开源项目一样，Scikit-learn目前主要由社区成员自发进行维护。可能是由于维护成本的限制，Scikit-learn相比其他项目要显得更为保守。这主要体现在两个方面：一是Scikit-learn从来不做除机器学习领域之外的其他扩展，二是Scikit-learn从来不采用未经广泛验证的算法。

本文将简单介绍Scikit-learn框架的六大功能，安装和运行Scikit-learn的大概步骤，同时为后续各更深入地学习Scikit-learn提供参考。原文来自infoworld网站的特约撰稿人Martin Heller，他曾在1986-2010年间做过长达20多年的数据库、通用软件和网页开发，具有丰富的开发经验。

Scikit-learn的六大功能

Scikit-learn的基本功能主要被分为六大部分：分类，回归，聚类，数据降维，模型选择和数据预处理。

分类是指识别给定对象的所属类别，属于监督学习的范畴，最常见的应用场景包括垃圾邮件检测和图像识别等。目前Scikit-learn已经实现的算法包括：支持向量机（SVM），最近邻，逻辑回归，随机森林，决策树以及多层感知器（MLP）神经网络等等。

需要指出的是，由于Scikit-learn本身不支持深度学习，也不支持GPU加速，因此这里对于MLP的实现并不适合于处理大规模问题。有相关需求的读者可以查看同样对Python有良好支持的Keras和Theano等框架。

回归是指预测与给定对象相关联的连续值属性，最常见的应用场景包括预测药物反应和预测股票价格等。目前Scikit-learn已经实现的算法包括：支持向量回归（SVR），脊回归，Lasso回归，弹性网络（Elastic Net），最小角回归（LARS ），贝叶斯回归，以及各种不同的鲁棒回归算法等。可以看到，这里实现的回归算法几乎涵盖了所有开发者的需求范围，而且更重要的是，Scikit-learn还针对每种算法都提供了简单明了的用例参考。

聚类是指自动识别具有相似属性的给定对象，并将其分组为集合，属于无监督学习的范畴，最常见的应用场景包括顾客细分和试验结果分组。目前Scikit-learn已经实现的算法包括：K-均值聚类，谱聚类，均值偏移，分层聚类，DBSCAN聚类等。

数据降维是指使用主成分分析（PCA）、非负矩阵分解（NMF）或特征选择等降维技术来减少要考虑的随机变量的个数，其主要应用场景包括可视化处理和效率提升。

模型选择是指对于给定参数和模型的比较、验证和选择，其主要目的是通过参数调整来提升精度。目前Scikit-learn实现的模块包括：格点搜索，交叉验证和各种针对预测误差评估的度量函数。

数据预处理是指数据的特征提取和归一化，是机器学习过程中的第一个也是最重要的一个环节。这里归一化是指将输入数据转换为具有零均值和单位权方差的新变量，但因为大多数时候都做不到精确等于零，因此会设置一个可接受的范围，一般都要求落在0-1之间。而特征提取是指将文本或图像数据转换为可用于机器学习的数字变量。

需要特别注意的是，这里的特征提取与上文在数据降维中提到的特征选择非常不同。特征选择是指通过去除不变、协变或其他统计上不重要的特征量来改进机器学习的一种方法。

总结来说，Scikit-learn实现了一整套用于数据降维，模型选择，特征提取和归一化的完整算法/模块，虽然缺少按步骤操作的参考教程，但Scikit-learn针对每个算法和模块都提供了丰富的参考样例和详细的说明文档。

安装和运行Scikit-learn

如前所述，Scikit-learn需要NumPy和SciPy等其他包的支持，因此在安装Scikit-learn之前需要提前安装一些支持包，具体列表和教程可以查看Scikit-learn的官方文档： http://scikit-learn.org/stable/install.html ，以下仅列出Python、NumPy和SciPy等三个必备包的安装说明。

Python：https://www.python.org/about/gettingstarted/

NumPy：http://www.numpy.org/

SciPy：http://www.scipy.org/install.html

假定已经完整安装了所有支持包，那么利用安装Scikit-learn只需要简单的一条简单的pip命令（也可以用conda命令，详见官方文档）：

$ sudo pip install -U scikit-learn



```javascript

sudo pip install -U scikit-learn
Password:
The directory '/Users/jingruijiaoyu/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/jingruijiaoyu/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting scikit-learn
Downloading scikit_learn-0.18.1-cp27-cp27m-macosx_10_6_intel.macosx_10_9_intel.macosx_10_9_x86_64.macosx_10_10_intel.macosx_10_10_x86_64.whl (7.5MB)
100% |████████████████████████████████| 7.5MB 47kB/s 
Installing collected packages: scikit-learn
Successfully installed scikit-learn-0.18.1

```

scikit-learn主要模块和基本使用方法

http://www.cnblogs.com/harvey888/p/5606158.html

```javascript

>>> import numpy as np 
>>> import urllib
>>> url = "http://archive.ics.uci.edu/ml/machine-learning-databases/pima-indians-diabetes/pima-indians-diabetes.data"
>>> raw_data = urllib.urlopen(url)
>>> dataset = np.loadtxt(raw_data,delimiter=",")
>>> X = dataset[:,0:7]
>>> y = dataset[:,8]
>>> from sklearn import preprocessing
>>> scaled_X = preprocessing.scale(X)
>>> normalized_X = preprocessing.normalize(X)
>>> standardized_X = preprocessing.scale(X))
File "<stdin>", line 1
standardized_X = preprocessing.scale(X))
^
SyntaxError: invalid syntax
>>> standardized_X = preprocessing.scale(X)
>>> from sklearn import metrics 
>>> from sklearn.ensemble import ExtraTreesClassifier
>>> model = ExtraTreesClassifier()
>>> model.fit(X,y)
ExtraTreesClassifier(bootstrap=False, class_weight=None, criterion='gini',
max_depth=None, max_features='auto', max_leaf_nodes=None,
min_impurity_split=1e-07, min_samples_leaf=1,
min_samples_split=2, min_weight_fraction_leaf=0.0,
n_estimators=10, n_jobs=1, oob_score=False, random_state=None,
verbose=0, warm_start=False)
>>> print(model.feature_importances)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
AttributeError: 'ExtraTreesClassifier' object has no attribute 'feature_importances'
>>> print(model.feature_importances_)
[ 0.1318342   0.26854907  0.12795734  0.08771382  0.08287976  0.15588338
0.14518245]
>>> from sklearn import metrics
>>> from sklearn.linear_model import LogisticRegression
>>> model = LogisticRegression()
>>> model.fit(X,y)
LogisticRegression(C=1.0, class_weight=None, dual=False, fit_intercept=True,
intercept_scaling=1, max_iter=100, multi_class='ovr', n_jobs=1,
penalty='l2', random_state=None, solver='liblinear', tol=0.0001,
verbose=0, warm_start=False)
>>> print('MODEL')
MODEL
>>> print(model)
LogisticRegression(C=1.0, class_weight=None, dual=False, fit_intercept=True,
intercept_scaling=1, max_iter=100, multi_class='ovr', n_jobs=1,
penalty='l2', random_state=None, solver='liblinear', tol=0.0001,
verbose=0, warm_start=False)
>>> expected = y
>>> predicted = model.predict(X)
>>> print('RESULT')
RESULT
>>> print(metrics.classificaction_report(expected,predicted))
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'classificaction_report'
>>> print(metrics.classification_report(expected,predicted))
precision    recall  f1-score   support

0.0       0.79      0.89      0.84       500
1.0       0.74      0.55      0.63       268

avg / total       0.77      0.77      0.77       768

>>> print('CONFUSION MATRIX')
CONFUSION MATRIX
>>> print(metrics.confusion_matrix(expected,predicted))
[[447  53]
[120 148]]
>>> from sklearn import metrics
>>> from sklearn.naive_bayes import GaussianNB
>>> model = GaussianNB()
>>> model.fit(X,y)
GaussianNB(priors=None)
>>> print('MODEL')
MODEL
>>> print(model)
GaussianNB(priors=None)
>>> expected = y
>>> print('RESULT')
RESULT
>>> print(metrics.classification_report(expected,predicted))
precision    recall  f1-score   support

0.0       0.79      0.89      0.84       500
1.0       0.74      0.55      0.63       268

avg / total       0.77      0.77      0.77       768

>>> print('CONFUSION MATRIX')
CONFUSION MATRIX
>>> print(metrics.confusion_matrix(expected,predicted))
[[447  53]
[120 148]]
>>> 


```
---

逻辑回归

http://www.tuicool.com/articles/auQFju


朴素贝叶斯

决策树

支持向量机





<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

