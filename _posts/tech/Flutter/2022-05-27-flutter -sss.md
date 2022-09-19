---
layout: post
title: 将 Flutter 集成到现有应用
category: Flutter
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---


```javascript



将 Flutter 集成到现有应用

https://juejin.cn/post/7090484738774794271

集成到 iOS 应用


* 在 Xcode 的 Build Phase 以及 CocoaPods 中，添加一个自动构建并引入 Flutter 模块的 Flutter SDK 钩子。
* 将 Flutter 模块构建为通用的 iOS Framework 以便集成到您自己的构建系统中；
* FlutterEngine API 用于启动并持续地为挂载 FlutterViewController 以提供独立的 Flutter 环境；
* 支持了 Objective-C 和 Swift 为宿主的应用程序；
* Flutter 模块可以通过使用 Flutter plugins 与平台进行交互；
* 支持通过从 IDE 或命令行中使用 flutter attach 来实现 Flutter 调试与有状态的热重载。
查看 add-to-app GitHub 示例仓库 中在 iOS 和 Android 平台上引入 Flutter module 的示例项目。
Flutter 可以以 framework 框架的形式添加到你的既有 iOS 应用中。
请参阅 add_to_app 代码示例 的 iOS 目录。




flutter build ios-framework --output=./Flutter/ 

flutter build ios --build-name=1.0.3


Multiple commands produce '/Users/yushuhui/Library/Developer/Xcode/DerivedData/wargame-botevuakvmbfrugdcljxrnsfphyp/Build/Products/Debug-iphoneos/wargame.app/Frameworks/App.framework'


Flutter调用原生图片资源

https://blog.csdn.net/Ever69/article/details/117394779


https://www.jianshu.com/p/ffcdcd9a0606


https://www.jianshu.com/p/5a3ff6e2b7ef



flutter pub add ios_platform_images


flutter run --release


Unable to load contents of file list: '/Target Support Files/Pods-Runner/Pods-Runner-frameworks-Debug-input-files.xcfilelist'




ios_platform_images: ^0.2.0+4




Flutter混编导航栈管理及右滑返回问题


https://www.jianshu.com/p/e3383b8db5ec


flutter AppBar 

https://www.jianshu.com/p/42e2fbeafd95



Flutter ListView 自定义

https://cloud.tencent.com/developer/article/1510131



https://github.com/xster/flutter-test



iOS flutter 互相调用

https://www.jianshu.com/p/736d45b55b1a


设置Flutter项目iOS和android工程的默认语言

https://juejin.cn/post/6857041070694334472

给 iOS 开发者的 Flutter 指南
 https://flutter.cn/docs/get-started/flutter-for/ios-devs


https://github.com/wanggang1128/WGFlutterDemo

跨平台，flutter技术总结


 "flutter upgrade"



com.example.wargameFlutter



可以command shift k 清空缓存


flutter还有flutter attach

flutter build ios  --no-codesign


打包步骤 flutter pub get -> flutter build ios  --no-codesign


flutter build ios  --no-codesign --build-name=1.0.3


--build-name=1.0.3


iOS原生与Flutter页面交互--从如何集成到相互跳转与传值(有demo)

https://www.jianshu.com/p/abd937d0d9aa

iOS工程下集成Flutter 两者之间的通信

https://github.com/PhoenixLeeSin/PhoenixLeeSin.github.io/blob/21db078811571a40b6fe8945edecbf6e1391be85/Flutter/iOS工程下集成Flutter%20两者之间的通信.md

https://github.com/LVHAI/iOS-Flutter/blob/d64914de5715b3c5dad84e666e9cda46a0f4a46e/iOS_project/ViewController.m


【Flutter】Flutter 页面生命周期 ( 初始化期 | createState | initState | 更新期 | build | 销毁期 | dispose)

https://blog.csdn.net/shulianghan/article/details/114305518



flutter_boost

免不了flutter和原生native页面的相互跳转和通信，flutterboost就是闲鱼团队开发的一个可复用的插件

https://blog.csdn.net/sinat_17775997/article/details/110439110


https://github.com/alibaba/flutter_boost/blob/master/docs/install.md

栗子

https://github.com/alibaba/flutter_boost/blob/master/example_new_for_ios/ios/Runner/Controllers/HomeViewController.swift

https://github.com/alibaba/flutter_boost/blob/master/example_new_for_ios/lib/main.dart

新一代Flutter-Native混合解决方案。 FlutterBoost是一个Flutter插件，它可以轻松地为现有原生应用程序提供Flutter混合集成方案。FlutterBoost的理念是将Flutter像Webview那样来使用。在现有应用程序中同时管理Native页面和Flutter页面并非易事。 FlutterBoost帮你处理页面的映射和跳转，你只需关心页面的名字和参数即可（通常可以是URL）。

Flutter 模块可以通过使用 Flutter plugins 与平台进行交互


很多时候我们需要监听路由堆栈的变化，这样可以自定义路由堆栈、方便分析异常日志等。


一套高性能渲染引擎来绘制UI，这个引擎就是大名鼎鼎的Skia，Skia是一个2D绘图引擎库


Flutter容器做成浏览器的感觉。填写一个页面地址，然后由容器去管理页面的绘制。在Native侧我们只需要关心如果初始化容器，然后设置容器对应的页面标志即可。


1、修改退出账号功能
2、完善Flutter和原生混编，处理路由映射和跳转，在Native侧我们只需要关心如果初始化容器 , 外层调用方只需关心页面的名字和参数，方便集成不同的模块。
3、Flutter页面全局生命周期监听



flutter --version

Flutter: iOS 侧滑返回

https://blog.csdn.net/u013066292/article/details/122896593


flutter模块编译打包时,自动更新版本号,告别手动修改版本号


https://blog.csdn.net/weixin_38025168/article/details/119969424

Flutter获取包名、APP名称、版本号、build构建版本号

https://blog.csdn.net/sinat_17775997/article/details/106372532?spm=1001.2101.3001.6650.4&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4-106372532-blog-119969424.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4-106372532-blog-119969424.pc_relevant_default&utm_relevant_index=8


Flutter build ios产物分析

https://blog.csdn.net/Notzuonotdied/article/details/103744872/



原生开发如何学习 Flutter 

https://juejin.cn/post/7065306768699572260


基于 Flutter 和 Firebase 实现的小游戏

https://juejin.cn/post/7096687944819277837


钉钉 Flutter 跨四端方案设计与技术实践

https://juejin.cn/post/7096407473472405512



Flutter的布局原理
https://juejin.cn/post/6914155427651387399


1、Widget大概可以分为三类组合类、代理类、绘制类
2、所有我们在屏幕上看到的UI最终几乎都会通过RenderObjectWidget实现。而RenderObjectWidget中有个createRenderObject()方法生成RenderObject对象，RenderObject实际负责实际的layout()和paint()。
3、Container组件其实只是一个组合类的控件，在其中封装了多个负责绘制的原子组件。
4、layout() 职能主要是计算控件自身的尺寸和位置偏移
5、整个布局过程就是向下约束 向上传值的过程
6、盒约束中有两种：
* tight（紧约束）：当max和min值相等时，这时传递给子类的是一个确定的宽高值。
* loose（松约束）：当max和min不相等的时候，这种时候对子类的约束是一个范围,称为松约束


flutter attach



```

---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>



