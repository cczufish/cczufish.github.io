---
layout: post
title: centos_jdk
category: 技术
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

centos_jdk

```javascript

wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/7u79-b15/jdk-7u79-linux-x64.tar.gz"
tar -zxvf  jdk-7u79-linux-x64.tar.gz
vi /etc/profile

JAVA_HOME=/usr/local/src/jdk1.7.0

PATH=$PATH:$JAVA_HOME/bin

CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

export JAVA_HOME PATH CLASSPATH

. /etc/profile

java -version


```

---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

