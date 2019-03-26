---
layout: post
title: 分享最近几次审核被拒的情况、第三方支付、论坛app
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

我们做的教育的app、有一个家校圈，类似于论坛、微博的功能，一直没问题、最近审核被拒。同时新版本增加了微信、支付宝、银联支付功能。

2019年3月10日 上午5:04
发件人 Apple
1. 2 Safety: User Generated Content
2. 1 Performance: App Completeness
Guideline 1.2 - Safety - User Generated Content


Your app enables the display of user-generated content but does not have the proper precautions in place.

Next Steps

To resolve this issue, please revise your app to implement all of the following precautions:

- Require that users agree to terms (EULA) and these terms must make it clear that there is no tolerance for objectionable content or abusive users
- A method for filtering objectionable content
- A mechanism for users to flag objectionable content
- A mechanism for users to block abusive users
- The developer must act on objectionable content reports within 24 hours by removing the content and ejecting the user who provided the offending content



Guideline 2.1 - Performance - App Completeness


Your app or its metadata does not appear to include final content. Specifically, your app includes placeholder content in 家校圈 and 课程详情-教学目标.

Next Steps

To resolve this issue, please review your app and metadata to ensure that all of its content is final.



Guideline 2.1 - Information Needed


We have started the review of your app, but we are not able to continue because we need additional information about your app.

Next Steps

To help us proceed with the review of your app, please review the following questions and provide as much detailed information as you can.￼

- Does your app access any paid content or services?
- What are the paid content or services, and what are the costs?
- Do individual customers pay for the content or services?
- If no, does a company or organization pay for the content or services? 
- Where do they pay, and what's the payment method?
- If users create an account to use your app, are there fees involved?
- How do users obtain an account?

Once you reply to this message in Resolution Center with the requested information, we can proceed with your review.



Please see attached screenshots for details.


然后我们就回复了苹果2次


2019年3月12日 下午5:36

Dear Apple Review Team:

Thank you for reviewing our app. Accouding to you mentioned, we add Privacy Policy(https://xxx.com/privacyPolicy.html) to requiring users to abide by.
At the same time, we offer the reporting function. Users can report inappropriate content at any time.


- Does your app access any paid content or services?
Yes, users can pay for school curriculum of Rise Training School.

- What are the paid content or services, and what are the costs?
Our company is a English training school. users can pay for school curriculum of Rise Training School.

- Do individual customers pay for the content or services?
Yes, parents pay for their kids courses.

- If no, does a company or organization pay for the content or services? 
NO.

- Where do they pay, and what's the payment method?
Users can purchase course in our school, but we offer online payment. Users pay on our APP, （Me->My order）
Payment method：Alipay，Wechat & UnionPay

- If users create an account to use your app, are there fees involved?
Our app is a free app; Users can use all functions. Everyone can sign up. 

- How do users obtain an account?
Everyone can sign up. We provide sign-up function for new users.



苹果审核团队您好：

对于审核反馈问题，我们需要做电话沟通：

1 Require that users agree to terms (EULA) and these terms must make it clear that there is no tolerance for objectionable content or abusive users

我们的app目前在安装完成就会弹出重要提醒，里面包括了隐私协议和一些提醒，用户只有同意了这个协议才能继续使用，我们已经在协议里明确规定不允许发不当的言论，不能发布令人反感的内容。

是否还需要在首次进入家校圈再次弹窗提示用户，直到用户同意才能继续。

2 Blocking mechanism (黑名单／屏蔽) for users to block potential abusive users 

我们的app不是社交app，家校圈是家长和学校老师沟通的一个平台，家长在工作之余了解孩子在校区学习的过程。用我们app的家长都是我们的客户，不会存在滥用ugc的情况。家校圈的内容是我们自己的员工在企业应用内发布的，家长可以评论。我们已经在app明确增加了举报的功能。我们会有两位运维人员在每天的早上9:00到晚上6:00处理举报内容。在接到用户的举报投诉后，我们的运维人员会及时核实举报内容并在24小时内做相应的处理。

是否还需要增加黑名单/屏蔽的功能。


第一次回复 支付功能通过了。第二次回复后增加了举报、屏蔽、隐私协议又一次通过了 棒棒棒 沟通的重要性。


https://developer.apple.com/contact/app-store/?topic=1.2.0

https://developer.apple.com/contact/app-store/?topic=expedite

另外苹果提供了一个加速审核的通道、我们也可以使用。每个账户每年有2到3次的机会。很多淘宝上帮忙加速审核的时候都是走这个通道。加急理由，苹果给出三个选项"bug修复"，"重大节日","其他"。

写加急理由的时候要注意理由要充分。要解释这个bug的严重性，必须修复。描述清楚复现的细节。



```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

