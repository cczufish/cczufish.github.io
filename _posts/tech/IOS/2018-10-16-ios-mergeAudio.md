---
layout: post
title: swift 将录制的多个aac音频合并为m4a格式音频
category: 技术
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

https://www.cnblogs.com/kunH/p/7358235.html

import UIKit
import Foundation
import AVFoundation


@objc protocol RecordManagerDelegate{

func mergeAction(fileUrl:String)  //必须方法

func playDuration(duration:Int,durationString:String)

}



class RecordManager {


var recorder: AVAudioRecorder?
var player: AVAudioPlayer?
var recordId:String!
var audioFilePath:String!
weak var  delegate: RecordManagerDelegate?

//开始录音
func beginRecord() {

createFolder()

let path = "/homeworkaudio/\(recordId!)/" + getStringDate() + "record.wav"
let file_path = NSSearchPathForDirectoriesInDomains(.documentDirectory, .userDomainMask, true).first?.appending(path)
audioFilePath = file_path

let session = AVAudioSession.sharedInstance()
//设置session类型
do {
try session.setCategory(AVAudioSessionCategoryPlayAndRecord)
} catch let err{
print("设置类型失败:\(err.localizedDescription)")
}
//设置session动作
do {
try session.setActive(true)
} catch let err {
print("初始化动作失败:\(err.localizedDescription)")
}
//录音设置，注意，后面需要转换成NSNumber，如果不转换，你会发现，无法录制音频文件，我猜测是因为底层还是用OC写的原因
let recordSetting: [String: Any] = [AVSampleRateKey: NSNumber(value: 16000),//采样率
AVFormatIDKey: NSNumber(value: kAudioFormatLinearPCM),//音频格式
AVLinearPCMBitDepthKey: NSNumber(value: 16),//采样位数
AVNumberOfChannelsKey: NSNumber(value: 1),//通道数
AVEncoderAudioQualityKey: NSNumber(value: AVAudioQuality.min.rawValue)//录音质量
];
//开始录音
do {
let url = URL(fileURLWithPath: file_path!)
recorder = try AVAudioRecorder(url: url, settings: recordSetting)
recorder!.prepareToRecord()
recorder!.record()
print("开始录音")
} catch let err {
print("录音失败:\(err.localizedDescription)")
}
}

// 创建文件
func createFolder(){

let fileManager = FileManager.default

let myDirectory:String = NSHomeDirectory() + "/Documents/homeworkaudio/" + recordId

// withIntermediateDirectories为ture表示路径中间如果有不存在的文件夹都会创建
try!fileManager.createDirectory(atPath: myDirectory, withIntermediateDirectories: true, attributes: nil)

}

// 遍历文件夹
func getAllFilePath(_ dirPath: String) -> [String]? {
var filePaths = [String]()

do {
let array = try FileManager.default.contentsOfDirectory(atPath: dirPath)

for fileName in array {
var isDir: ObjCBool = true

let fullPath = "\(dirPath)/\(fileName)"

if FileManager.default.fileExists(atPath: fullPath, isDirectory: &isDir) {
if !isDir.boolValue {
filePaths.append(fullPath)
}
}
}

} catch let error as NSError {
print("get file path error: \(error)")
}

return filePaths;
}


//结束录音
func stopRecord() {
if let recorder = self.recorder {
if recorder.isRecording {
print("正在录音，马上结束它，文件保存到了：\(audioFilePath!)")
}else {
print("没有录音，但是依然结束它")
}
recorder.stop()
self.recorder = nil
}else {
print("没有初始化")
}
}

func pause()
{
self.player?.pause()
}

//播放
func play() {

let myDirectory:String = NSHomeDirectory() + "/Documents/homeworkaudio/" + recordId

let composition = AVMutableComposition()

let audioLocalUrls:Array<String>! = getAllFilePath(myDirectory)

for i in 0 ..< audioLocalUrls.count {

let compositionAudioTrack :AVMutableCompositionTrack = composition.addMutableTrack(withMediaType: AVMediaType.audio, preferredTrackID: CMPersistentTrackID())!

let asset = AVURLAsset(url: URL.init(fileURLWithPath: audioLocalUrls[i]))

let track = asset.tracks(withMediaType: AVMediaType.audio)[0]

var timeRange:CMTimeRange
timeRange = CMTimeRange(start: CMTimeMake(0, 600), duration: track.timeRange.duration)

//偶有崩溃的情况
try! compositionAudioTrack.insertTimeRange(timeRange, of: track, at: composition.duration)
}
let uuid = CFUUIDCreateString(nil, CFUUIDCreate(nil)) as String

let path = "/homeworkaudio/\(recordId!)/" + uuid + "record.wav"
let file_path = NSSearchPathForDirectoriesInDomains(.documentDirectory, .userDomainMask, true).first?.appending(path)
let mergeAudioURL = NSURL.fileURL(withPath: file_path!)

let assetExport = AVAssetExportSession(asset: composition, presetName: AVAssetExportPresetAppleM4A)
assetExport?.outputFileType = AVFileType.m4a
assetExport?.outputURL = mergeAudioURL

assetExport?.exportAsynchronously(completionHandler:
{
switch assetExport!.status
{
case AVAssetExportSessionStatus.failed:
print("failed \(String(describing: assetExport?.error))")
case AVAssetExportSessionStatus.cancelled:
print("cancelled \(String(describing: assetExport?.error))")
case AVAssetExportSessionStatus.unknown:
print("unknown\(String(describing: assetExport?.error))")
case AVAssetExportSessionStatus.waiting:
print("waiting\(String(describing: assetExport?.error))")
case AVAssetExportSessionStatus.exporting:
print("exporting\(String(describing: assetExport?.error))")
default:
print("success\(String(describing: assetExport?.error))\(file_path)")

//.............
do {

let session = AVAudioSession.sharedInstance()
//设置session类型
do {
try session.setCategory(AVAudioSessionCategoryPlayback)
} catch let err{
print("设置类型失败:\(err.localizedDescription)")
}
//设置session动作
do {
try session.setActive(true)
} catch let err {
print("初始化动作失败:\(err.localizedDescription)")
}


// let path = Bundle.main.path(forResource: "record", ofType: "wav")
self.player = try AVAudioPlayer(contentsOf: URL(fileURLWithPath: file_path!))
//   player?.volume = 0.8
print("歌曲长度：\(self.player!.duration)")

let min = Int (self.player!.duration)

//   print("\(min / 60):\(min % 60)")

self.delegate?.playDuration(duration: min, durationString: "0'\(min / 60)'\(min % 60)'")

self.player?.prepareToPlay()
self.player!.play()
} catch let err {
print("播放失败:\(err.localizedDescription)")
}

//.........

for i in 0..<audioLocalUrls.count{
let fileManager = FileManager.default
try! fileManager.removeItem(at: URL.init(fileURLWithPath: audioLocalUrls[i]))
}

}

})


}

//合并音频
func mergeAudio(){

let myDirectory:String = NSHomeDirectory() + "/Documents/homeworkaudio/" + recordId

let composition = AVMutableComposition()

let audioLocalUrls:Array<String>! = getAllFilePath(myDirectory)

if audioLocalUrls == nil || audioLocalUrls.count == 0
{
self.delegate?.mergeAction(fileUrl: "文件不存在")
return
}

for i in 0 ..< audioLocalUrls.count {

let compositionAudioTrack :AVMutableCompositionTrack = composition.addMutableTrack(withMediaType: AVMediaType.audio, preferredTrackID: CMPersistentTrackID())!

let asset = AVURLAsset(url: URL.init(fileURLWithPath: audioLocalUrls[i]))

let track = asset.tracks(withMediaType: AVMediaType.audio)[0]

var timeRange:CMTimeRange
timeRange = CMTimeRange(start: CMTimeMake(0, 600), duration: track.timeRange.duration)

try! compositionAudioTrack.insertTimeRange(timeRange, of: track, at: composition.duration)
}
let uuid = CFUUIDCreateString(nil, CFUUIDCreate(nil)) as String

let path = "/homeworkaudio/" + uuid + "record.wav"
let file_path = NSSearchPathForDirectoriesInDomains(.documentDirectory, .userDomainMask, true).first?.appending(path)
let mergeAudioURL = NSURL.fileURL(withPath: file_path!)

let assetExport = AVAssetExportSession(asset: composition, presetName: AVAssetExportPresetAppleM4A)
assetExport?.outputFileType = AVFileType.m4a
assetExport?.outputURL = mergeAudioURL

assetExport?.exportAsynchronously(completionHandler:
{
switch assetExport!.status
{
case AVAssetExportSessionStatus.failed:
print("failed \(String(describing: assetExport?.error))")
case AVAssetExportSessionStatus.cancelled:
print("cancelled \(String(describing: assetExport?.error))")
case AVAssetExportSessionStatus.unknown:
print("unknown\(String(describing: assetExport?.error))")
case AVAssetExportSessionStatus.waiting:
print("waiting\(String(describing: assetExport?.error))")
case AVAssetExportSessionStatus.exporting:
print("exporting\(String(describing: assetExport?.error))")
default:
print("success\(String(describing: assetExport?.error))")

self.delegate?.mergeAction(fileUrl: file_path!)

}

})

}

func deleteAudio()
{
if recordId == nil
{
return
}

let myDirectory:String = NSHomeDirectory() + "/Documents/homeworkaudio/" + recordId

let audioLocalUrls:Array<String>! = getAllFilePath(myDirectory)

for i in 0..<audioLocalUrls.count{
let fileManager = FileManager.default
try! fileManager.removeItem(at: URL.init(fileURLWithPath: audioLocalUrls[i]))
}


}

func getStringDate() -> String {
//获取当前时间
let now = Date()

// 创建一个日期格式器
let dformatter = DateFormatter()
dformatter.dateFormat = "yyyyMMddHHmmss"
print("当前日期时间：\(dformatter.string(from: now))")

let stringDate = dformatter.string(from: now)

return stringDate
}

}



```



---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

