---
layout: post
title: Alcatraz | The Package manager for Xcode
category: iOS
tags: iOS, Alcatraz，os x
description:
---

![](https://imgsa.baidu.com/baike/c0%3Dbaike150%2C5%2C5%2C150%2C50/sign=2a37efef044f78f0940692a118586130/29381f30e924b89978db088369061d950b7bf6a2.jpg)

恶魔岛（Alcatraz Island，英语俗称The Rock）是位于美国加州旧金山湾内的一座小岛，面积为0.0763平方公里，四面峭壁深水，联外交通不易，因而被美国政府选为监狱建地，曾设有恶魔岛联邦监狱，关押过不少知名的重刑犯，于1963年废止，现与金门大桥同为旧金山湾的著名观光景点。  


以上纯属题外话，哈哈哈！


Alcatraz | The Package manager for Xcode  (http://alcatraz.io)

install:

curl -fsSL https://raw.githubusercontent.com/supermarin/Alcatraz/deploy/Scripts/install.sh | sh

Alcatraz successfully installed!!1!🍻  Please restart your Xcode (8.3.2).

Uninstall

rm -rf ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins/Alcatraz.xcplugin

rm -rf ~/Library/Application\ Support/Alcatraz


当然了 ，我安装了 ，打开Xcode发现没启动,然后搜了一下在终端输入下面命令

```javascript

sudo gem install update_xcode_plugins

Fetching: colorize-0.8.1.gem (100%)
Successfully installed colorize-0.8.1
Fetching: tins-1.13.2.gem (100%)
Successfully installed tins-1.13.2
Fetching: term-ansicolor-1.6.0.gem (100%)
Successfully installed term-ansicolor-1.6.0
Fetching: inquirer-0.2.1.gem (100%)
Successfully installed inquirer-0.2.1
Fetching: update_xcode_plugins-0.4.0.gem (100%)
Successfully installed update_xcode_plugins-0.4.0
Parsing documentation for colorize-0.8.1
Installing ri documentation for colorize-0.8.1
Parsing documentation for tins-1.13.2
Installing ri documentation for tins-1.13.2
Parsing documentation for term-ansicolor-1.6.0
Installing ri documentation for term-ansicolor-1.6.0
Parsing documentation for inquirer-0.2.1
Installing ri documentation for inquirer-0.2.1
Parsing documentation for update_xcode_plugins-0.4.0
unable to convert "\xCA" from ASCII-8BIT to UTF-8 for lib/bin/unsign, skipping
Installing ri documentation for update_xcode_plugins-0.4.0
5 gems installed


update_xcode_plugins

Found:
- Xcode (8.3.2) [DFFB3951-EB0A-4C09-9DAC-5F2D28CC839C]: /Applications/Xcode.app

Plugins:
- Alcatraz (1.2.0)

Updating...
Added DFFB3951-EB0A-4C09-9DAC-5F2D28CC839C to Alcatraz (1.2.0)

Finished! 🎉

It seems that you have Xcode 8+ installed!
Some plugins might not work on recent versions of Xcode because of library validation.
See https://github.com/alcatraz/Alcatraz/issues/475

Run `update_xcode_plugins --unsign` to fix this.





```






<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>


