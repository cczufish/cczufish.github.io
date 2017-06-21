---
layout: post
title: 机器学习之识别简单验证码
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---

https://www.iswin.org/2016/10/15/Simple-CAPTCHA-Recognition-with-Machine-Learning/

http://www.cnblogs.com/dudumiaomiao/p/6600495.html


```javascript

sudo pip install requests
Password:
The directory '/Users/jingruijiaoyu/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/jingruijiaoyu/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting requests
Downloading requests-2.18.1-py2.py3-none-any.whl (88kB)
100% |████████████████████████████████| 92kB 32kB/s 
Collecting urllib3<1.22,>=1.21.1 (from requests)
Downloading urllib3-1.21.1-py2.py3-none-any.whl (131kB)
100% |████████████████████████████████| 133kB 31kB/s 
Collecting idna<2.6,>=2.5 (from requests)
Downloading idna-2.5-py2.py3-none-any.whl (55kB)
100% |████████████████████████████████| 61kB 35kB/s 
Requirement already satisfied: certifi>=2017.4.17 in /Library/Python/2.7/site-packages/certifi-2017.4.17-py2.7.egg (from requests)
Collecting chardet<3.1.0,>=3.0.2 (from requests)
Downloading chardet-3.0.4-py2.py3-none-any.whl (133kB)
100% |████████████████████████████████| 143kB 18kB/s 
Installing collected packages: urllib3, idna, chardet, requests
Successfully installed chardet-3.0.4 idna-2.5 requests-2.18.1 urllib3-1.21.1


```

图片采集

```javascript

>>> import time
>>> import requests
>>> def downloads_pic(pic_name):
...     url = 'http://smart.gzeis.edu.cn:8081/Content/AuthCode.aspx'
...     res = requests.get(url,stream=True)
...     with open('/Users/jrjy/Desktop/pic/%s.jpg'%(pic_name),'wb') as f:
... ...         for chunk in res.iter_content(chunk_size=1024):
...                     if chunk:
...                             f.write(chunk)
...                             f.flush()
...             f.close()
... 
>>> 
>>> if __name__ == '__main__':
...     for i in range(300):
...             pic_name = int(time.time()*1000000))
File "<stdin>", line 3
pic_name = int(time.time()*1000000))
^
SyntaxError: invalid syntax
>>>             pic_name = int(time.time()*1000000)
File "<stdin>", line 1
pic_name = int(time.time()*1000000)
^
IndentationError: unexpected indent
>>> if __name__ == '__main__':
...     for i in range(300):
...             pic_name = int(time.time()*1000000)
...             downloads_pic(pic_name)


```



![图片采集](https://www.iswin.org/attach/machineLearn-pics_sava.png)

图片预处理以及图片裁剪

```javascript

sudo pip install image
Password:
The directory '/Users/jingruijiaoyu/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/jingruijiaoyu/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting image
Downloading image-1.5.5.tar.gz
Collecting pillow (from image)
Downloading Pillow-4.1.1-cp27-cp27m-macosx_10_6_intel.macosx_10_9_intel.macosx_10_9_x86_64.macosx_10_10_intel.macosx_10_10_x86_64.whl (3.5MB)
100% |████████████████████████████████| 3.5MB 7.8kB/s 
Collecting django (from image)
Downloading Django-1.11.2-py2.py3-none-any.whl (6.9MB)
100% |████████████████████████████████| 7.0MB 21kB/s 
Collecting olefile (from pillow->image)
Downloading olefile-0.44.zip (74kB)
100% |████████████████████████████████| 81kB 28kB/s 
Requirement already satisfied: pytz in /System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python (from django->image)
Installing collected packages: olefile, pillow, django, image
Running setup.py install for olefile ... done
Running setup.py install for image ... done
Successfully installed django-1.11.2 image-1.5.5 olefile-0.44 pillow-4.1.1


```

```javascript

>>> import os
>>> import os.path
>>> from PIL import Image
>>> from PIL import ImageFilter
>>> from PIL import ImageEnhance
>>> import time
>>> def setment(im):
...     s = 2   
...     w = 14
...     h = 20
...     t = 0
...     im_new = []
...     for i in range(4):
...             im1 = im.crop((s+w*i,t,s+w*(i+1),h))
...             im_new.append(im1)
...     return im_new
...     
>>> def imgTransfer(f_name):
...     im = Image.open(f_name)
...     im = im.filter(ImageFilter.MedianFilter())
...     enhancer = ImageEnhance.Contrast(im)
...     im = enhancer.enhance(1)
...     im = im.convert('L')
...     return im
... 
>>> def cutPictures(img):
...     im = imgTransfer(img):
File "<stdin>", line 2
im = imgTransfer(img):
^
SyntaxError: invalid syntax
>>> def cutPictures(img):
...     im = imgTransfer(img)
...     pics = segment(im)
...     for pic in pics:
...             pic.save('/Users/jrjy/Desktop/test/%s.jpg'%(int(time.time()*1000000)),'jpeg')
... 
>>> rootdir = u'/Users/jrjy/Desktop/pic'
>>> for parent,dirnames,filenames in os.walk(rootdir):
...     for filename in filenames:
...             print "filename is :"+filename
...             print "parent is :"+parent
...             print "the full name is:"+os.path.join(parent,filename)
...             cutPictures(os.path.join(parent,filename))
... 
filename is :1498026748366736.jpg
parent is :/Users/jrjy/Desktop/pic
the full name is:/Users/jrjy/Desktop/pic/1498026748366736.jpg
Traceback (most recent call last):
File "<stdin>", line 6, in <module>
File "<stdin>", line 3, in cutPictures
NameError: global name 'segment' is not defined
>>> def cutPictures(img):
...     im = imgTransfer(img)
...     pics = setment(im)
...      for pic in pics:
File "<stdin>", line 4
for pic in pics:
^
IndentationError: unexpected indent
>>>     
>>> def cutPictures(img):
...     im = imgTransfer(img)
...     pics = setment(im)
...     for pic in pics:
...             pic.save('/Users/jrjy/Desktop/test/%s.jpg'%(int(time.time()*1000000)),'jpeg')
... 
>>> rootdir = u'/Users/jrjy/Desktop/pic'
>>> for parent,dirnames,filenames in os.walk(rootdir):
...     for filename in filenames:
...             cutPictures(os.path.join(parent,filename))

```

到这一步跟预期不一样。。。。。。。。test文件夹下 处理后的不是数字。。。。大多数是空白 肯定是哪里做错了。。。。


'''javascript


# -*- coding: utf-8 -*-
import os
import os.path
from PIL import Image
from PIL import ImageFilter
from PIL import ImageEnhance
import time
def segment(im):

s=6   #首次第一个点的横坐标

w=16  #宽度

h=20  #第二个点的纵坐标

t=0   #第一个点的纵坐标

im_new=[]#在一张图片裁剪四个区域

#for i in range(4):

#       im1=im.crop((s+w*i,t,s+w*(i+1),h))  #crop函数得到局部区域

#       im_new.append(im1)

im1=im.crop((6,0,6+17,20))

im_new.append(im1)

im1=im.crop((23,0,23+16,20))

im_new.append(im1)

im1=im.crop((39,0,39+16,20))

im_new.append(im1)

im1=im.crop((55,0,55+18,20))

im_new.append(im1)

return im_new


def binarizing(im,threshold):

pixdata=im.load()

w,h=im.size

for j in range(h):

for i in range(w):

if pixdata[i,j]<threshold:

pixdata[i,j]=0

else:

pixdata[i,j]=255

return im



def denoising(im):

pixdata=im.load()

w,h=im.size

for j in range(1,h-1):

for i in range(1,w-1):

count=0

if pixdata[i,j-1]>245:

count=count+1

if pixdata[i,j+1]>245:

count=count+1

if pixdata[i+1,j]>245:

count=count+1

if pixdata[i-1,j]>245:

count=count+1

if count>2:

pixdata[i,j]=255

return im






def imgTransfer(f_name):

im=Image.open(f_name)  #打开图片

im=im.filter(ImageFilter.MedianFilter(1))  #对于输入图像的每个像素点，该滤波器从（size，size）的区域中拷贝中值对应的像素值存储到输出图像中

#enhancer=ImageEnhance.Contrast(im)

#im=enhancer.enhance(1)

im=ImageEnhance.Contrast(im).enhance(1.5)#enhance()的参数factor决定着图像的对比度情况。从0.1到0.5，再到0.8，2.0，图像的对比度依次增大.0.0为纯灰色图像;1.0为保持原始

im=im.convert('L')   #灰度图转换

im=denoising(im)     #图片去噪

im=binarizing(im,200)  #图片二值化

#im=nse.removeNoisy(im)

#im.save('/User/iswin/Downloads/vim/test.clear.jpg','jpeg')

#im.show()

return im





def cutPictures(img):

im=imgTransfer(img)#####图片预处理,二值化,图片增强

pics=segment(im) #######用crop函数裁剪

for pic in pics:

pic.save('/Users/jrjy/Desktop/test/%s.jpg'%(int(time.time()*1000000)),'jpeg')



rootdir=u'/Users/jrjy/Desktop/pic'



for parent,dirnames,filenames in os.walk(rootdir):



for dirname in dirnames:

print "dirname is:"+dirname

print "parent is:"+parent



for filename in filenames:

print "filename is:"+filename

print "parent is:"+parent

print "the full name is:"+os.path.join(parent,filename)

cutPictures(os.path.join(parent,filename))





```


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

