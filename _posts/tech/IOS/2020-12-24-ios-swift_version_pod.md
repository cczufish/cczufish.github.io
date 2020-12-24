---
layout: post
title: swift 5.0 升级 ，指定pod库设置SWIFT_VERSION和IPHONEOS_DEPLOYMENT_TARGET
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

post_install do |installer|

    installer.pods_project.targets.each do |target|

      

      if ['JXPhotoBrowser'].include? target.name

            target.build_configurations.each do |config|

              config.build_settings['SWIFT_VERSION'] = '4.0'

              config.build_settings['ONLY_ACTIVE_ARCH'] = 'NO'

              config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '10.0'

            end

      else

            target.build_configurations.each do |config|

              config.build_settings['SWIFT_VERSION'] = '5.0'

              config.build_settings['ONLY_ACTIVE_ARCH'] = 'NO'

              config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '10.0'

            end

      end

    end

end



```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

