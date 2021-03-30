---
layout: post
title: Angular之firebase的cloud messaging使用
subtitle:
date: 2021-02-26
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Angular
  - Firebase
  - Cloud messaging
  - Typescript
---

## Cloud Messaging
Firebase Cloud Messaging (FCM) 是一种跨平台消息传递解决方案，开发者可以使用它免费且可靠地传递消息和通知。

使用 FCM，可以通知客户端应用存在可以同步的新电子邮件或其他数据。 您可以发送通知来重新吸引用户和促进用户留存。 对于即时通讯等用例，一条消息可以将最大 4KB 的负载传送至客户端应用

### 连接准备
1. 用Google账号登录 [firebase](https://firebase.google.com/) 并且创建一个项目。 
2. 在创建的项目中添加应用，可以得到`Firebase SDK snippet`.
   
   [官方提供的操作步骤](https://firebase.google.com/docs/web/setup?authuser=0)

   注意，只需要进行到第二步注册应用就足够了。
3. 查看`Firebase SDK snippet`。在控制台里打开所创建的项目，左上方的设置图标，点击项目设置。在常规选项卡里的您的应用中看到`Firebase SDK snippet`区域，点击CDN选项，下方会得到一个`firebaseConfig`对象。 这是我们所需要的

### Angular中配置firebase
1. 正常的创建一个项目
2. 安装firebase包

    ```
    npm i firebase
    ```
3. 配置`environment`，在`environment.ts`里面将`firebaseConfig`添加

    ```typescript
    export const environment = {
    production: false,
    configFirebase: {
        apiKey: 'AIzaSyDxTG8U1Kmhl_y76CPgmG2p1egeoExYC58',
        authDomain: 'cloudmsg-a9d4c.firebaseapp.com',
        databaseURL: 'https://cloudmsg-a9d4c-default-rtdb.firebaseio.com',
        projectId: 'cloudmsg-a9d4c',
        storageBucket: 'cloudmsg-a9d4c.appspot.com',
        messagingSenderId: '653396225568',
        appId: '1:653396225568:web:694abe431f3d3ed1601645',
    },
    };
    ```
4. 在src目录下创建`firebase-messaging-sw.js`文件并且配置文件。(使用刚才得到的`firebaseConfig`)

    ```typescript
    importScripts('https://www.gstatic.com/firebasejs/8.2.9/firebase-app.js')
    importScripts('https://www.gstatic.com/firebasejs/8.2.9/firebase-messaging.js')

    firebase.initializeApp({
        apiKey: "AIzaSyDxTG8U1Kmhl_y76CPgmG2p1egeoExYC58",
        authDomain: "cloudmsg-a9d4c.firebaseapp.com",
        databaseURL: "https://cloudmsg-a9d4c-default-rtdb.firebaseio.com",
        projectId: "cloudmsg-a9d4c",
        storageBucket: "cloudmsg-a9d4c.appspot.com",
        messagingSenderId: "653396225568",
        appId: "1:653396225568:web:694abe431f3d3ed1601645"
    })
    const messaging =firebase.messaging();
    ```
5. 将`firebase-messaging-sw.js`的路径引入`angular.json`的`assets`中,如下：

    ```typescript
          "architect": {
        "build": {
          "builder": "@angular-devkit/build-angular:browser",
          "options": {
            "outputPath": "dist/my-app",
            "index": "src/index.html",
            "main": "src/main.ts",
            "polyfills": "src/polyfills.ts",
            "tsConfig": "tsconfig.app.json",
            "aot": true,
            "assets": [
              "src/favicon.ico",
              "src/assets",
              "src/firebase-messaging-sw.js" //z在这里
            ],
    ```
6. 使用`angular`代码可以快速在services文档下创建一个service
   
        ng g s service/push-notification
	
7. `push-notification.service.ts`里面内容如下

    ```typescript
    import { Injectable } from '@angular/core';
    import firebase from 'firebase';
    import { observable, Observable } from 'rxjs';
    import { environment } from 'src/environments/environment';
    @Injectable({
    providedIn: 'root'
    })
    export class PushNotificationService {
    messagingFirebase: firebase.messaging.Messaging;
    constructor() {
        firebase.initializeApp(environment.configFirebase)
        this.messagingFirebase=firebase.messaging()
    }
    requestPermission=()=>{
        return new Promise(async (resolve,reject)=>{
            const permsis=await Notification.requestPermission();
            if(permsis === "granted"){
            console.log('用户曾经同意授权');
            const  tokenFirebase=this.messagingFirebase.getToken();
            resolve(tokenFirebase)
            }else{
            reject(new Error("no token get"))
            }
        })
    }

    private messagingObservable= new  Observable(observable=>{
        this.messagingFirebase.onMessage(payload=>{
        observable.next(payload)
        })
    })

    receiveMessage(){
        return this.messagingObservable
    }
    }
    ```
8. 在`app.module.ts`里的`providers`加入service的class，`PushNotificationService`
    ```
    providers: [PushNotificationService]
    ```
9. 配置`app.component.ts`,代码如下：

    ```typescript
    import { Component } from '@angular/core';
    import { PushNotificationService } from './services/push-notification.service';

    @Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
    styleUrls: ['./app.component.scss']
    })
    export class AppComponent {
    title = 'my-app';
    messageReceived=""
    constructor(private notification: PushNotificationService){
        notification.requestPermission().then(token=>{
        console.log(token)
        })
    }
    ngOnInit():void{
    this.notification.receiveMessage().subscribe(payload=>{
    console.log(payload)

    })
    }
    }
    ```
10. angular快捷启动网页,让浏览器允许通知。这时候就可以在console栏里看见FCM的注册令牌。
    ```
        ng s -o
    ```

    如果提示错误
    `firebaseError: Messaging: We are unable to register the default service worker`等。可以把网址的`localhost:4200`改成`127.0.0.1:4200`，就能成功。
 1.  从firebase发送推送消息给浏览器。
    
        * 打开firebase网站开启你的项目
        * 在吸引(crecimiento)选择栏中选择`cloud messaging`
        * 在顶栏出点击`Send your first message`按钮
        * 写入标题、通知文字，然后点击发送测试消息
        * 将刚才从网页的console栏中得到的FCM注册令牌字符串写入
        * 点击左侧加号图标然后点击测试就可以成功发送消息
11. 在firebase发送消息后，不仅仅左面会有弹窗显示，在angular网页里的console栏中也会打印出发送的数据，可以以此为依据证明上面步骤是否成功
