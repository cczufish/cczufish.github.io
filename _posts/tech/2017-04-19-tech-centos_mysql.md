---
layout: post
title: centos_mysql
category: 技术
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

centos_mysql

```javascript

MySQL-devel-5.5.45-1.linux2.6.x86_64.rpm
MySQL-client-5.5.45-1.linux2.6.x86_64.rpm
MySQL-server-5.5.45-1.linux2.6.x86_64.rpm

http://cdn.mysql.com/Downloads/MySQL-5.5/MySQL-server-5.5.45-1.linux2.6.x86_64.rpm

http://cdn.mysql.com/Downloads/MySQL-5.5/MySQL-client-5.5.45-1.linux2.6.x86_64.rpm

http://cdn.mysql.com/Downloads/MySQL-5.5/MySQL-devel-5.5.45-1.linux2.6.x86_64.rpm

/usr/local/mysql    安装文件

rpm -ivh MySQL-client-5.5.45-1.linux2.6.x86_64.rpm MySQL-server-5.5.45-1.linux2.6.x86_64.rpm MySQL-devel-5.5.45-1.linux2.6.x86_64.rpm

which mysql

mysql --version

https://ask.fedoraproject.org/en/question/43459/how-to-start-mysql-mysql-isnt-starting/
yum install mariadb mariadb-server
systemctl start mariadb.service
systemctl enable mariadb.service
/usr/bin/mysql_secure_installation

/etc/init.d/mysql status

/usr/bin/mysql /usr/lib64/mysql /usr/include/mysql /usr/share/mysql /usr/share/man/man1/mysql.1.gz

mysql -u root -p
show databases;
create database mytest;
use mytest;
create table students(
-> id int unsigned not null auto_increment primary key,
-> name char(8) not null,
-> sex char(4) not null);
show tables;
insert into students values(1,"ysh","femeal");

mysql怎么查看端口号
show variables ；

远程访问

mysql不允许远程用户访问主机服务器 1130 
安装完之后成 使用 mysql admin连接报错 
ERROR 1130: Host ***.***.***.*** is not allowed to connect to this MySQL server 
以下百度查到的，试过可以 
说明所连接的用户帐号没有远程连接的权限，只能在本机(localhost)登录。 
需更改 mysql 数据库里的 user表里的 host项 
把localhost改称% 
具体步骤：登陆到mysql 
首先 use mysql； 
按照别人提供的方式update的时候，出现错误。 
mysql> update user set host='%' where user = 'root'; 
ERROR 1062 (23000): Duplicate entry '%-root' for key 'PRIMARY' 
然后查看了下数据库的host信息如下： 
mysql> select host from user where user = 'root'; 
+-----------------------+ 
| host | 
+-----------------------+ 
| % | 
| 127.0.0.1 | 
| localhost.localdomain | 
+-----------------------+ 
3 rows in set (0.00 sec) 
host已经有了%这个值，所以直接运行命令： 
mysql>flush privileges; 
再用mysql administrator连接...成功！！！


删除这两个服务(去掉后缀)
rpm –e MySQL-client-5.6.19-1.linux_glibc2.5.x86_64
rpm -e MySQL-server-5.6.19-1.linux_glibc2.5.x86_64
查看残留的目录：
whereis mysql

然后删除mysql目录：
rm –rf /usr/lib64/mysql

删除相关文件：
rm –rf /usr/my.cnf
rm -rf /root/.mysql_sercret



CentOS 7的yum源中貌似没有正常安装mysql时的mysql-sever文件，需要去官网上下载
# wget http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm
# rpm -ivh mysql-community-release-el7-5.noarch.rpm
# yum install mysql-community-server
成功安装之后重启mysql服务
# service mysqld restart
初次安装mysql是root账户是没有密码的
设置密码的方法
# mysql -uroot
mysql> set password for ‘root’@‘localhost’ = password('mypasswd');
mysql> exit


mysql中文乱码

登录进mysql看看是个什么情况。

mysql -u root -p

5.看下mysql的编码，发现不全是utf8，有Latin的，这是中文乱码的根源。

show variables like 'character%';

6.关闭mysql服务，准备开始修改my.cnf文件

service mysqld stop
vi /etc/my.cnf

7.看了网络上很多版本的my.cnf的修改方式，我索性就全给改成了utf8，我的my.cnf文件是这样的。

[mysqld]
character_set_server=utf8      #这个是我添加的
init_connect='SET NAMES utf8'
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock
user=mysql
symbolic-links=0

[mysqld_safe]
default-character-set = utf8    #这个是我添加的
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

[client]
default-character-set = utf8      #这个是我添加的

[mysql.server]
default-character-set = utf8      #这个是我添加的

[mysql]
default-character-set = utf8      #这个是我添加的


8.修改了my.cnf文件之后一定要重启mysql服务，这是必须的。

service mysqld restart


9.再进去mysql查看编码会发都变成了utf8，除了character_set_filesystem 是binary 。这个不用我解释是为什么了。



Mac安装MySQL初始密码设置  http://blog.csdn.net/arlenliugj/article/details/50700249

step1：
苹果->系统偏好设置->最下边点mysql 在弹出页面中 关闭mysql服务（点击stop mysql server）

step2：
进入终端输入：cd /usr/local/mysql/bin/
回车后 登录管理员权限 sudo su
回车后输入以下命令来禁止mysql验证功能 ./mysqld_safe --skip-grant-tables &
回车后mysql会自动重启（偏好设置中mysql的状态会变成running）

step3.
输入命令 ./mysql
回车后，输入命令 FLUSH PRIVILEGES;
回车后，输入命令 SET PASSWORD FOR 'root'@'localhost' = PASSWORD('你的新密码');
至此，密码修改完成，可以成功登陆。




mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.01 sec)


mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| columns_priv              |
| db                        |
| engine_cost               |
| event                     |
| func                      |
| general_log               |
| gtid_executed             |
| help_category             |
| help_keyword              |
| help_relation             |
| help_topic                |
| innodb_index_stats        |
| innodb_table_stats        |
| ndb_binlog_index          |
| plugin                    |
| proc                      |
| procs_priv                |
| proxies_priv              |
| server_cost               |
| servers                   |
| slave_master_info         |
| slave_relay_log_info      |
| slave_worker_info         |
| slow_log                  |
| tables_priv               |
| time_zone                 |
| time_zone_leap_second     |
| time_zone_name            |
| time_zone_transition      |
| time_zone_transition_type |
| user                      |
+---------------------------+
31 rows in set (0.00 sec)



 

```

---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

