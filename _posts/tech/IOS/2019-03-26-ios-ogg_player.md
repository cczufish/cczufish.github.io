---
layout: post
title: ios 播放ogg格式音频，以及AudioQueue播放速率问题
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

ios 端播放ogg audio


https://github.com/cczufish/oggplayer_swift


AudioQueue播放速度、速率问题

https://github.com/Jerry0523/AudioQueueServiceDemo/blob/675fe707c2c93702036b776ee2aa8b3de27a4a6b/JWAudioHelper/AudioPlayerOutput.cpp

https://github.com/wuwulailai/myplayer/blob/1439b2b16d3c63afad93606b07696716fff3eb5d/ios/IJKMediaPlayer/IJKMediaPlayer/ijkmedia/ijksdl/ios/IJKSDLAudioQueueController.m

https://developer.apple.com/library/archive/documentation/MusicAudio/Conceptual/AudioQueueProgrammingGuide/AQPlayback/PlayingAudio.html

http://msching.github.io/blog/2014/08/02/audio-in-ios-5/


https://developer.apple.com/documentation/audiotoolbox/1552626-audio_queue_parameters/kaudioqueueparam_playrate?language=objc


        UInt32 enabled = 1;
        AudioQueueSetProperty(mQueue, kAudioQueueProperty_EnableTimePitch, &enabled, 4);
        UInt32 timePitchAlgorithm = kAudioQueueTimePitchAlgorithm_Spectral; // supports rate and pitch
        AudioQueueSetProperty(mQueue, kAudioQueueProperty_TimePitchAlgorithm, &timePitchAlgorithm, sizeof(timePitchAlgorithm));


        AudioQueueSetParameter(mQueue, kAudioQueueParam_PlayRate, rate);
        UInt32 propValue = 1;
        AudioQueueSetProperty(mQueue, kAudioQueueProperty_EnableTimePitch, &propValue, sizeof(propValue));






```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

