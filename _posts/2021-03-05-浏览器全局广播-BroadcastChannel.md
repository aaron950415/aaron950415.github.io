---
layout: post
title: 浏览器全局广播-BroadcastChannel
subtitle:
date: 2021-02-26
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Js

---

# BroadcastChannel

有时候，我们需要在两个浏览器的标签页间进行通讯，又或者需要在浏览器内通信。这时候浏览器就有提供一个API可以供我们使用。

本人是为了设计firebase的后台推送，苦恼sw.js与标签页的通信，经过查找终于发现这个。现在与大家分享。

`BroadcastChannel` 的使用方式简单，只需要在发送端新建一个广播频道，并且编辑内容发送，进行浏览器广播。然后在接收端创建同一频道，这样就可以接收到发送端发送的消息。不过还需要添加一个事件监听。当收到消息的时候触发事件。 具体代码如下：

```javascript
    //发送端
    const channel = new BroadcastChannel('firebase-messaging-sw');
    channel.postMessage({title: 'Hello from SW',body:payload});
```

```javascript
    //接收端
    const channel = new BroadcastChannel("firebase-messaging-sw");
    channel.addEventListener("message", (event) => {
        //当接受到消息后触发事件
    });
```