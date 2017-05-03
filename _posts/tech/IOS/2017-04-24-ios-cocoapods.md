---
layout: post
title: OS X 10.12上安装CocoaPods
category: iOS
tags: iOS,CocoaPods，os x
description:
---

OS X 10.12上安装CocoaPods


    ➜  Desktop  sudo gem install cocoapods
    Password:
    Fetching: claide-1.0.1.gem (100%)
    Successfully installed claide-1.0.1
    Fetching: nap-1.1.0.gem (100%)
    Successfully installed nap-1.1.0
    Fetching: cocoapods-core-1.2.1.gem (100%)
    Successfully installed cocoapods-core-1.2.1
    Fetching: cocoapods-deintegrate-1.0.1.gem (100%)
    Successfully installed cocoapods-deintegrate-1.0.1
    Fetching: cocoapods-downloader-1.1.3.gem (100%)
    Successfully installed cocoapods-downloader-1.1.3
    Fetching: cocoapods-plugins-1.0.0.gem (100%)
    Successfully installed cocoapods-plugins-1.0.0
    Fetching: cocoapods-search-1.0.0.gem (100%)
    Successfully installed cocoapods-search-1.0.0
    Fetching: cocoapods-stats-1.0.0.gem (100%)
    Successfully installed cocoapods-stats-1.0.0
    Fetching: cocoapods-trunk-1.2.0.gem (100%)
    Successfully installed cocoapods-trunk-1.2.0
    Fetching: cocoapods-try-1.1.0.gem (100%)
    Successfully installed cocoapods-try-1.1.0
    Fetching: colored2-3.1.2.gem (100%)
    Successfully installed colored2-3.1.2
    Fetching: fourflusher-2.0.1.gem (100%)
    Successfully installed fourflusher-2.0.1
    Fetching: gh_inspector-1.0.3.gem (100%)
    Successfully installed gh_inspector-1.0.3
    Fetching: molinillo-0.5.7.gem (100%)
    Successfully installed molinillo-0.5.7
    Fetching: ruby-macho-1.1.0.gem (100%)
    Successfully installed ruby-macho-1.1.0
    Fetching: CFPropertyList-2.3.5.gem (100%)
    Successfully installed CFPropertyList-2.3.5
    Fetching: nanaimo-0.2.3.gem (100%)
    Successfully installed nanaimo-0.2.3
    Fetching: xcodeproj-1.4.4.gem (100%)
    ERROR:  While executing gem ... (Errno::EPERM)
    Operation not permitted - /usr/bin/xcodeproj
    ➜  Desktop  gem sources -l
    *** CURRENT SOURCES ***

    https://ruby.taobao.org/
    https://gems.ruby-china.org/
    ➜  Desktop  gem sources --remove https://gems.ruby-china.org/
    https://gems.ruby-china.org/ removed from sources
    ➜  Desktop  gem sources -l                                   
    *** CURRENT SOURCES ***

    https://ruby.taobao.org/
    ➜  Desktop  sudo gem install cocoapods
    ERROR:  While executing gem ... (Errno::EPERM)
    Operation not permitted - /usr/bin/xcodeproj
    ➜  Desktop  sudo gem install -n /usr/local/bin cocoapods
    Successfully installed xcodeproj-1.4.4
    Fetching: cocoapods-1.2.1.gem (100%)
    Successfully installed cocoapods-1.2.1
    Parsing documentation for xcodeproj-1.4.4
    Installing ri documentation for xcodeproj-1.4.4
    Parsing documentation for cocoapods-1.2.1
    Installing ri documentation for cocoapods-1.2.1
    2 gems installed
    ➜  Desktop  pod --version
    1.2.1


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

