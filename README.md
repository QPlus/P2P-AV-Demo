# P2P-AV-Demo
此Demo 演示如何使用亲加P2P SDK实现一对一音视频交互的应用。

## 亲加P2P模块介绍与使用
亲加通讯云的P2P SDK主要包括两个模块，分别是基础模块（RTCCore）, P2P(RTCP2P)模块，其介绍如下：  

* RTCCore  
基础模块，需要首先被调用。会验证AppKey，RoomID 等信息。验证通过后，才能调用其他模块。  

* RTCP2P  
P2P 功能模块，通过此模块所提供的接口和事件可以实现一套完整的P2P 通讯应用。  

## P2P 接口使用流程
1. 初始化  
包括两部分的初始化：
    * RTCCore 初始化  
    重要的函数主要是registerApp和authRoomSession。确定初始化成功后，就还可以开始后续的调用了  
    
    * RTCP2P 初始化
    主要是Init 和Login 两个函数。Login 的回调函数中会返回登陆是否成功的信息。  
    * 设置远端和本地视频显示区域  
    调用setRendererView 函数设置远端和本地视频显示窗口  
    * 监听事件  
    通过事件监听来获取各类交互协议。具体请查看接口文档中的“事件”部分
       
2. 获取用户列表  
通过queryUserList 函数可以获取用户列表，从而选择某个用户进行视频交互  

3. 邀请视频互动  
调用inviteUser 函数邀请某一个用户进行视频互动  

4. 被邀请方确定是否接受邀请  
被邀请方会接收到inviteCall事件，此时可以弹出对话框询问用户是否接受邀请。接受邀请调用acceptInvitation 函数，否则调用denyInvitation函数  

5. 建立连接 OR 结束互动  
当收到acceptCall事件后，就会开始建立连接，连接成功后会收到connected事件。如果希望结束互动可以调用endPeerConnection函数  

### 流程图如下： 

![流程图](https://github.com/QPlus/P2P-AV-Demo/raw/master/MDImages/p2p.png)

### QQ 交流群： 202871487
