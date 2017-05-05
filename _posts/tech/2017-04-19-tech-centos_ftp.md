---
layout: post
title: centos_ftp
category: 技术
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

centos_ftp

```javascript

在命令提示符下输入：
ftp
open
输入ftp服务器的ip地址
输入用户名和密码

如果在使用setenforce命令设置selinux状态的时候出现这个提示：setenforce: SELinux is disabled
那么说明selinux已经被彻底的关闭了

如果需要重新开启selinux，请按下面步骤：vi /etc/selinux/config
更改为：SELINUX=1
必须重启linux，不重启是没办法立刻开启selinux的
重启完以后，使用getenforce,setenforce等命令就不会报“setenforce: SELinux is disabled”了
这时，我们就可以用setenforce命令来动态的调整当前是否开启selinux。

yum install vsftpd
chkconfig vsftpd on
systemctl start vsftpd.service

systemctl restart vsftpd.service

配置防火墙
打开/etc/sysconfig/iptables文件

vi /etc/sysconfig/iptables
在REJECT行之前添加如下代码

-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 21 -j ACCEPT
保存和关闭文件，重启防火墙

service iptables start
配置vsftpd服务器
默认的配置文件是/etc/vsftpd/vsftpd.conf，你可以用文本编辑器打开。

vi /etc/vsftpd/vsftpd.conf
添加ftp用户
下面是添加ftpuser用户，设置根目录为/home/wwwroot/ftpuser,禁止此用户登录SSH的权限，并限制其访问其它目录。

１、修改/etc/vsftpd/vsftpd.conf

将底下三行

#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
改为

chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd/chroot_list
3、增加用户ftpuser，指向目录/home/wwwroot/ftpuser,禁止登录SSH权限。

useradd -d /home/wwwroot/ftpuser -g ftp -s /sbin/nologin ftpuser
4、设置用户口令

passwd ftpuser
5、编辑文件chroot_list:

vi /etc/vsftpd/chroot_list
内容为ftp用户名,每个用户占一行,如：

peter
john

6、重新启动vsftpd

service vsftpd restart
另外，如果觉得以后管理ftp用户名嫌麻烦，可以使用centos官方发布的脚本管理。地址如下：

http://wiki.centos.org/HowTos/Chroot_Vsftpd_with_non-system_users

出现的错误
1、500 OOPS: cannot change directory
解决方法：

在终端输入命令：

setsebool -P ftpd_disable_trans 1
service vsftpd restart
就ＯＫ了！
原因：这是因为服务器开启了selinux，这限制了FTP的登录。

http://www.cnblogs.com/lightnear/archive/2012/10/07/2713539.html


```

---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

