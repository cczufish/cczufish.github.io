---
layout: post
title: Mac安装TensorFlow
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---


```javascript

sudo easy_install pip
Password:
Searching for pip
Best match: pip 9.0.1
Adding pip 9.0.1 to easy-install.pth file
Installing pip script to /usr/local/bin
Installing pip3.5 script to /usr/local/bin
Installing pip3 script to /usr/local/bin

Using /Library/Python/2.7/site-packages
Processing dependencies for pip
Finished processing dependencies for pip


sudo easy_install --upgrade six
Searching for six
Reading https://pypi.python.org/simple/six/
Best match: six 1.10.0
Downloading https://pypi.python.org/packages/b3/b2/238e2590826bfdd113244a40d9d3eb26918bd798fc187e2360a8367068db/six-1.10.0.tar.gz#md5=34eed507548117b2ab523ab14b2f8b55
Processing six-1.10.0.tar.gz
Writing /tmp/easy_install-WRUy7K/six-1.10.0/setup.cfg
Running six-1.10.0/setup.py -q bdist_egg --dist-dir /tmp/easy_install-WRUy7K/six-1.10.0/egg-dist-tmp-ZVghdE
no previously-included directories found matching 'documentation/_build'
zip_safe flag not set; analyzing archive contents...
six: module references __path__
creating /Library/Python/2.7/site-packages/six-1.10.0-py2.7.egg
Extracting six-1.10.0-py2.7.egg to /Library/Python/2.7/site-packages
Removing six 1.9.0 from easy-install.pth file
Adding six 1.10.0 to easy-install.pth file

Installed /Library/Python/2.7/site-packages/six-1.10.0-py2.7.egg
Processing dependencies for six
Finished processing dependencies for six




```

https://www.tensorflow.org  // 翻墙访问

https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.2.0-py2-none-any.whl

https://pypi.python.org/pypi/Werkzeug#downloads

https://pypi.python.org/pypi/html5lib#downloads

https://pypi.python.org/pypi/webencodings#downloads

https://pypi.python.org/pypi/bleach

```javascript

sudo pip install Werkzeug-0.12.2-py2.py3-none-any.whl
Password:
The directory '/Users/jrjy/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/jingruijiaoyu/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Processing ./Werkzeug-0.12.2-py2.py3-none-any.whl
Installing collected packages: Werkzeug
Successfully installed Werkzeug-0.12.2

```

特么的安装了一下午还没成功 万恶的。。。。。



```javascript

sudo pip install /Users/jrjy/Downloads/tensorflow-1.2.1-py2-none-any.whl
Password:
The directory '/Users/jrjy/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/jrjy/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Processing /Users/jingruijiaoyu/Downloads/tensorflow-1.2.1-py2-none-any.whl
Requirement already satisfied: bleach==1.5.0 in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Requirement already satisfied: werkzeug>=0.11.10 in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Requirement already satisfied: html5lib==0.9999999 in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Collecting markdown>=2.6.8 (from tensorflow==1.2.1)
Downloading Markdown-2.6.8.tar.gz (307kB)
100% |████████████████████████████████| 317kB 374kB/s 
Requirement already satisfied: six>=1.10.0 in /Library/Python/2.7/site-packages/six-1.10.0-py2.7.egg (from tensorflow==1.2.1)
Requirement already satisfied: backports.weakref==1.0rc1 in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Requirement already satisfied: wheel in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Collecting numpy>=1.11.0 (from tensorflow==1.2.1)
Downloading numpy-1.13.1-cp27-cp27m-macosx_10_6_intel.macosx_10_9_intel.macosx_10_9_x86_64.macosx_10_10_intel.macosx_10_10_x86_64.whl (4.6MB)
100% |████████████████████████████████| 4.6MB 161kB/s 
Collecting mock>=2.0.0 (from tensorflow==1.2.1)
Downloading mock-2.0.0-py2.py3-none-any.whl (56kB)
100% |████████████████████████████████| 61kB 576kB/s 
Collecting protobuf>=3.2.0 (from tensorflow==1.2.1)
Downloading protobuf-3.3.0.tar.gz (271kB)
100% |████████████████████████████████| 276kB 481kB/s 
Collecting funcsigs>=1; python_version < "3.3" (from mock>=2.0.0->tensorflow==1.2.1)
Downloading funcsigs-1.0.2-py2.py3-none-any.whl
Collecting pbr>=0.11 (from mock>=2.0.0->tensorflow==1.2.1)
Downloading pbr-3.1.1-py2.py3-none-any.whl (99kB)
100% |████████████████████████████████| 102kB 419kB/s 
Requirement already satisfied: setuptools in /System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python (from protobuf>=3.2.0->tensorflow==1.2.1)
Installing collected packages: markdown, numpy, funcsigs, pbr, mock, protobuf, tensorflow
Found existing installation: Markdown 2.2.0
Uninstalling Markdown-2.2.0:
Successfully uninstalled Markdown-2.2.0
Running setup.py install for markdown ... done
Found existing installation: numpy 1.8.0rc1
DEPRECATION: Uninstalling a distutils installed project (numpy) has been deprecated and will be removed in a future version. This is due to the fact that uninstalling a distutils project will only partially uninstall the project.
Uninstalling numpy-1.8.0rc1:
Exception:
Traceback (most recent call last):
File "/Library/Python/2.7/site-packages/pip/basecommand.py", line 215, in main
status = self.run(options, args)
File "/Library/Python/2.7/site-packages/pip/commands/install.py", line 342, in run
prefix=options.prefix_path,
File "/Library/Python/2.7/site-packages/pip/req/req_set.py", line 778, in install
requirement.uninstall(auto_confirm=True)
File "/Library/Python/2.7/site-packages/pip/req/req_install.py", line 754, in uninstall
paths_to_remove.remove(auto_confirm)
File "/Library/Python/2.7/site-packages/pip/req/req_uninstall.py", line 115, in remove
renames(path, new_path)
File "/Library/Python/2.7/site-packages/pip/utils/__init__.py", line 267, in renames
shutil.move(old, new)
File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/shutil.py", line 302, in move
copy2(src, real_dst)
File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/shutil.py", line 131, in copy2
copystat(src, dst)
File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/shutil.py", line 103, in copystat
os.chflags(dst, st.st_flags)
OSError: [Errno 1] Operation not permitted: '/tmp/pip-E9quwd-uninstall/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/numpy-1.8.0rc1-py2.7.egg-info'



```

拖了这么久安装成功了， 关机，开机按住command+R，终端输入 csrutil disable 回车

Successfully disabled System Integrity Protection. Please restart the machine for the changes to take effect.




```javascript

sudo pip install /Users/jrjy/Downloads/tensorflow-1.2.1-py2-none-any.whl
Password:
The directory '/Users/jrjy/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/jrjy/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Processing /Users/jrjy/Downloads/tensorflow-1.2.1-py2-none-any.whl
Requirement already satisfied: bleach==1.5.0 in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Requirement already satisfied: werkzeug>=0.11.10 in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Requirement already satisfied: html5lib==0.9999999 in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Requirement already satisfied: markdown>=2.6.8 in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Requirement already satisfied: six>=1.10.0 in /Library/Python/2.7/site-packages/six-1.10.0-py2.7.egg (from tensorflow==1.2.1)
Requirement already satisfied: backports.weakref==1.0rc1 in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Requirement already satisfied: wheel in /Library/Python/2.7/site-packages (from tensorflow==1.2.1)
Collecting numpy>=1.11.0 (from tensorflow==1.2.1)
Downloading numpy-1.13.1-cp27-cp27m-macosx_10_6_intel.macosx_10_9_intel.macosx_10_9_x86_64.macosx_10_10_intel.macosx_10_10_x86_64.whl (4.6MB)
100% |████████████████████████████████| 4.6MB 133kB/s 
Collecting mock>=2.0.0 (from tensorflow==1.2.1)
Downloading mock-2.0.0-py2.py3-none-any.whl (56kB)
100% |████████████████████████████████| 61kB 1.6MB/s 
Collecting protobuf>=3.2.0 (from tensorflow==1.2.1)
Downloading protobuf-3.3.0.tar.gz (271kB)
100% |████████████████████████████████| 276kB 1.1MB/s 
Collecting funcsigs>=1; python_version < "3.3" (from mock>=2.0.0->tensorflow==1.2.1)
Downloading funcsigs-1.0.2-py2.py3-none-any.whl
Collecting pbr>=0.11 (from mock>=2.0.0->tensorflow==1.2.1)
Downloading pbr-3.1.1-py2.py3-none-any.whl (99kB)
100% |████████████████████████████████| 102kB 834kB/s 
Requirement already satisfied: setuptools in /System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python (from protobuf>=3.2.0->tensorflow==1.2.1)
Installing collected packages: numpy, funcsigs, pbr, mock, protobuf, tensorflow
Found existing installation: numpy 1.8.0rc1
DEPRECATION: Uninstalling a distutils installed project (numpy) has been deprecated and will be removed in a future version. This is due to the fact that uninstalling a distutils project will only partially uninstall the project.
Uninstalling numpy-1.8.0rc1:
Successfully uninstalled numpy-1.8.0rc1
Running setup.py install for protobuf ... done
Successfully installed funcsigs-1.0.2 mock-2.0.0 numpy-1.13.1 pbr-3.1.1 protobuf-3.3.0 tensorflow-1.2.1






python
Python 2.7.10 (default, Feb  7 2017, 00:08:15) 
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.34)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import tensorflow as tf
>>> hello = tf.constant('hello ,tensorflow!')
>>> sess = tf.Session()
2017-07-17 15:45:23.868993: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.2 instructions, but these are available on your machine and could speed up CPU computations.
2017-07-17 15:45:23.869031: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX instructions, but these are available on your machine and could speed up CPU computations.
2017-07-17 15:45:23.869043: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX2 instructions, but these are available on your machine and could speed up CPU computations.
2017-07-17 15:45:23.869054: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use FMA instructions, but these are available on your machine and could speed up CPU computations.
>>> print (sess.run(hello))
hello ,tensorflow!
>>> a = tf.constant(10)
>>> b = tf.constant(20)
>>> print(sess.run(a+b))
30
>>> 







```





<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

