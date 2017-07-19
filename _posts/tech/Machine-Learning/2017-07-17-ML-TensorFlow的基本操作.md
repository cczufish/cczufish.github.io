---
layout: post
title: Tensorflow基本操作
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---

今天报名了「深度学习30天系统实训」

提前学习一下 Tensorflow基本操作 学习教程： http://blog.csdn.net/Jerr__y/article/category/6747409 所有的都来自这里


http://studyai.com/course/detail/0c77152aeb2040e590d2dbf939f5589c

http://www.jianshu.com/p/6766fbcd43b9


```javascript


>>> import tensorflow as tf
>>> import numpy as np
>>> x_data = np.float32(np.random.rand(2, 100)) 
>>> y_data = np.dot([0.100, 0.200], x_data) + 0.300
>>> b = tf.Variable(tf.zeros([1]))
>>> W = tf.Variable(tf.random_uniform([1, 2], -1.0, 1.0))
>>> y = tf.matmul(W, x_data) + b
>>> loss = tf.reduce_mean(tf.square(y - y_data))
>>> optimizer = tf.train.GradientDescentOptimizer(0.5)
>>> train = optimizer.minimize(loss)
>>> init = tf.initialize_all_variables()
WARNING:tensorflow:From /Library/Python/2.7/site-packages/tensorflow/python/util/tf_should_use.py:170: initialize_all_variables (from tensorflow.python.ops.variables) is deprecated and will be removed after 2017-03-02.
Instructions for updating:
Use `tf.global_variables_initializer` instead.
>>> init = tf.global_variables_initializer
ERROR:tensorflow:==================================
Object was never used (type <class 'tensorflow.python.framework.ops.Operation'>):
<tf.Operation 'init' type=NoOp>
If you want to mark it as used call its "mark_used()" method.
It was originally created here:
['File "<stdin>", line 1, in <module>', 'File "/Library/Python/2.7/site-packages/tensorflow/python/util/tf_should_use.py", line 170, in wrapped\n    return _add_should_use_warning(fn(*args, **kwargs))', 'File "/Library/Python/2.7/site-packages/tensorflow/python/util/tf_should_use.py", line 139, in _add_should_use_warning\n    wrapped = TFShouldUseWarningWrapper(x)', 'File "/Library/Python/2.7/site-packages/tensorflow/python/util/tf_should_use.py", line 96, in __init__\n    stack = [s.strip() for s in traceback.format_stack()]']
==================================
>>> init = tf.global_variables_initializer()
>>> sess = tf.Session()
2017-07-18 10:08:40.966794: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.2 instructions, but these are available on your machine and could speed up CPU computations.
2017-07-18 10:08:40.966838: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX instructions, but these are available on your machine and could speed up CPU computations.
2017-07-18 10:08:40.966857: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX2 instructions, but these are available on your machine and could speed up CPU computations.
2017-07-18 10:08:40.966874: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use FMA instructions, but these are available on your machine and could speed up CPU computations.
>>> sess.run(init)
>>> for step in xrange(0, 201):
...     sess.run(train)
...     if step % 20 == 0:
...              print step, sess.run(W), sess.run(b)
... 
0 [[-0.25882745  0.97372049]] [ 0.14455333]
20 [[ 0.09755064  0.36616167]] [ 0.20678769]
40 [[ 0.11758351  0.24765594]] [ 0.26306593]
60 [[ 0.10898402  0.21596259]] [ 0.28590286]
80 [[ 0.10367611  0.20573501]] [ 0.29468513]
100 [[ 0.10141738  0.20211673]] [ 0.29800454]
120 [[ 0.10053618  0.20078887]] [ 0.29925191]
140 [[ 0.10020155  0.200295  ]] [ 0.29971966]
160 [[ 0.1000756   0.20011044]] [ 0.29989496]
180 [[ 0.10002834  0.20004135]] [ 0.29996064]
200 [[ 0.10001063  0.2000155 ]] [ 0.29998526]
>>> 




>>> import tensorflow as tf
>>> matrix1 = tf.constant([[3.,3.]])
>>> matrix2 = tf.constant([[2.],[2.]])
>>> product = tf.matmul(matrix1,matrix2)
>>> product
<tf.Tensor 'MatMul_1:0' shape=(1, 1) dtype=float32>
>>> matrix1 
<tf.Tensor 'Const_1:0' shape=(1, 2) dtype=float32>
>>> matrix2
<tf.Tensor 'Const_2:0' shape=(2, 1) dtype=float32>
>>> sess = tf.Session()
>>> result = sess.run(product)
>>> print result
[[ 12.]]
>>> sess.close()





```





<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

