---
layout: post
title:  ios 原生加载obj 3d模型
category: iOS
tags: centos,ftp,Apache,GPL,LGPL,MIT
description: 
---

```javascript

import UIKit
import SceneKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        let scnView = SCNView(frame: self.view.bounds);
        let bundle = Bundle.main
        let path = bundle.path(forResource: "3dshow", ofType: "obj")
        let url = NSURL(fileURLWithPath: path!)

        let scene = SCNScene(named: "3dshow.obj")

              let cameraNode = SCNNode()
              cameraNode.camera = SCNCamera()
              // 3: Place camera
              cameraNode.position = SCNVector3(x: 0, y: 12, z: 45)
              // 4: Set camera on scene
              scene?.rootNode.addChildNode(cameraNode)
              // 5: Adding light to scene
              let lightNode = SCNNode()
              lightNode.light = SCNLight()
              lightNode.light?.type = .omni
              lightNode.position = SCNVector3(x: 0, y: 10, z: 40)
              scene?.rootNode.addChildNode(lightNode)
              // 6: Creating and adding ambien light to scene
              let ambientLightNode = SCNNode()
              ambientLightNode.light = SCNLight()
              ambientLightNode.light?.type = .ambient
              ambientLightNode.light?.color = UIColor.darkGray
              scene?.rootNode.addChildNode(ambientLightNode)
              // Allow user to manipulate camera
        scnView.allowsCameraControl = true
              // Show FPS logs and timming
              // sceneView.showsStatistics = true
              
              // Set background color
        scnView.backgroundColor = UIColor.black
        
        
        scnView.scene = scene

        self.view.addSubview(scnView);
    }

}



```



---
