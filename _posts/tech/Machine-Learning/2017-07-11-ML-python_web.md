---
layout: post
title:  Crossin的编程教室 ---  Python 实战1
category: Machine-Learning
tags: python,ML,Numpy,Machine-learning,KNN
description: 
---

http://res.crossincode.com/wechat/someweb.html


```javascript

sudo easy_install web.py
Searching for web.py
Reading https://pypi.python.org/simple/web.py/
Best match: web.py 0.40.dev0
Downloading https://pypi.python.org/packages/47/15/c011b80de6c2df69be46d6d79d063496dc901a53820e493de35e891fc904/web.py-0.40.dev0.tar.gz#md5=fb08cd2e36efde893987a75dc652f9e3
Processing web.py-0.40.dev0.tar.gz
Writing /tmp/easy_install-aVRQXO/web.py-0.40.dev0/setup.cfg
Running web.py-0.40.dev0/setup.py -q bdist_egg --dist-dir /tmp/easy_install-aVRQXO/web.py-0.40.dev0/egg-dist-tmp-QWmtkQ
/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/dist.py:285: UserWarning: Normalizing '0.40-dev0' to '0.40.dev0'
normalized_version,
zip_safe flag not set; analyzing archive contents...
web.application: module references __file__
web.debugerror: module references __file__
creating /Library/Python/2.7/site-packages/web.py-0.40.dev0-py2.7.egg
Extracting web.py-0.40.dev0-py2.7.egg to /Library/Python/2.7/site-packages
Adding web.py 0.40.dev0 to easy-install.pth file

Installed /Library/Python/2.7/site-packages/web.py-0.40.dev0-py2.7.egg
Processing dependencies for web.py
Finished processing dependencies for web.py


python
Python 2.7.10 (default, Feb  7 2017, 00:08:15) 
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.34)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import web


import web

urls = ('/','index')

class index:
def GET(self):
return "Hello World!"


if __name__ == "__main__":
app = web.application(urls,globals())
app.run()


python code.py
http://0.0.0.0:8080/
127.0.0.1:52904 - - [11/Jul/2017 10:17:31] "HTTP/1.1 GET /" - 200 OK
127.0.0.1:52905 - - [11/Jul/2017 10:17:31] "HTTP/1.1 GET /favicon.ico" - 404 Not Found



 #python Address already in use 端口已经被占用的解决方法


ps -fA | grep python
501  1221   886   0 10:17上午 ttys000    0:00.44 python code.py
501  1288   886   0 10:33上午 ttys000    0:00.00 grep python


kill 1221

ps -fA | grep python
501  1292   886   0 10:34上午 ttys000    0:00.00 grep python



import web

urls = ('/','index')

movies = [
{
'title':'Forrest Gump',
'year':1994,
},
{
'title':'Titanic',
'year':1997,
}
]

class index:
def GET(self):
page = ''
for m in movies:
page += '%s (%d)\n' % (m['title'], m['year'])
return page


if __name__ == "__main__":
app = web.application(urls,globals())
app.run()


http://0.0.0.0:8080


Forrest Gump (1994)
Titanic (1997)


import web

urls = ('/','index')

render = web.template.render('templates/')

class index:
def GET(self):
return render.index()


if __name__ == "__main__":
app = web.application(urls,globals())
app.run()


<h1>Crossin's Movie Site</h1>


Crossin's Movie Site



import web

render = web.template.render('templates/')

urls = (
'/', 'index'
)

movies = [
{
'title': 'Forrest Gump',
'year': 1994,
},
{
'title': 'Titanic',
'year': 1997,
},
]

class index:
def GET(self):
return render.index(movies)

if __name__ == "__main__":
app = web.application(urls, globals())
app.run()



$def with (movies)
<h1>Crossin's Movie Site</h1>
$for movie in movies:
<li>
$movie['title'],$movie['year']
</li>


Crossin's Movie Site

Forrest Gump,1994
Titanic,1997


import web

db = web.database(dbn='sqlite',db='MovieSite.db')


render = web.template.render('templates/')

urls = (
'/', 'index'
)

class index:
def GET(self):
movies = db.select('movie')
return render.index(movies)

if __name__ == "__main__":
app = web.application(urls, globals())
app.run()




$def with (movies)
<h1>Crossin's Movie Site</h1>
$for movie in movies:
<li>
$movie['title'],$movie['year'],$movie['country'],$movie['abstract']
</li>

sqlite3 MovieSite.db

create table movie(title,year,country,abstract);

insert into movie values('aganzhengzhuan',1994,'meiguo','Life is like box of chocolates.');

insert into movie values('xiaoshenke',1994,'meiguo','Hope is a good thing.');





Crossin's Movie Site

aganzhengzhuan,1994,meiguo,Life is like box of chocolates.
xiaoshenke,1994,meiguo,Hope is a good thing.




import web

db = web.database(dbn='sqlite',db='MovieSite.db')


render = web.template.render('templates/')

urls = (
'/', 'index',
'/movie/(\d+)', 'movie',
)




class index:
def GET(self):
movies = db.select('movie')
return render.index(movies)

class movie:
def GET(self, movie_id):
movie_id = int(movie_id)
movie = db.select('movie', where='id=$movie_id', vars=locals())[0]
return render.movie(movie)


if __name__ == "__main__":
app = web.application(urls, globals())
app.run()



$def with (movie)
<h4><a href="/">返回首页</a></h4>
<h1>$movie.title</h1>
<hr>	
<p>年代：$movie.year</p>
<p>国家：$movie.country</p>
<p>$movie.abstract</p>


$def with (movies)
<h4>欢迎来到</h4>
<h1>Crossin's Movie Site</h1>
<hr>
<p>影片列表：</p>
$for movie in movies:
<li>
<a href="movie/$movie['id']">$movie['title']</a>
</li>





欢迎来到

Crossin's Movie Site

影片列表：

aganzhengzhuan
ag22222anzhengzhuan



搜搜


import web

db = web.database(dbn='sqlite',db='MovieSite.db')


render = web.template.render('templates/')

urls = (
'/', 'index',
'/movie/(\d+)', 'movie',
)




class index:
def GET(self):
movies = db.select('movie')
return render.index(movies)

def POST(self):
data = web.input()
condition = r'title like "%' + data.title + r'%"'
movies = db.select('movie', where=condition)
return render.index(movies)

class movie:
def GET(self, movie_id):
movie_id = int(movie_id)
movie = db.select('movie', where='id=$movie_id', vars=locals())[0]
return render.movie(movie)


if __name__ == "__main__":
app = web.application(urls, globals())
app.run()





$def with (movies)
<h4>欢迎来到</h4>
<h1>Crossin's Movie Site</h1>
<hr>
<p>影片列表：</p>

<form action="/" method="post">
<input type="text" name="title" />
<input type="submit" value="搜索" />
</form>


$for movie in movies:
<li>
<a href="movie/$movie['id']">$movie['title']</a>
</li>













```


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

