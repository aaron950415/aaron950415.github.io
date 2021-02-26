---
layout: post
title: JSONPlaceholder建立简易数据库数据库
subtitle:
date: 2021-02-10
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JSONPlaceholder
  - Github
  - http
---

1. 在GitHub上创建你的仓库(<your-username>/<your-repo>)
2. 在仓库里创建一个`db.json`文件

    ```json
    {
      "posts": [
        {
          "id": 1,
          "title": "hello"
        }
      ],
      "profile": {
        "name": "typicode"
      }
    }
    ```
3. 访问`https://my-json-server.typicode.com/<your-username>/<your-repo>/posts/1`就能打开你的服务器
   ```json
    {
        "id": 1,
        "title": "hello"
    }
      ```

4. 在js文件中写上下面代码
    ```js
    fetch('https://jsonplaceholder.typicode.com/posts/1')
    .then((response) => response.json())
    .then((json) => console.log(json));
    ```
5. 打开网页的console栏就能看见打印出来的数据
    ```json
    {
      id: 1,
      title: '...',
      body: '...',
      userId: 1
    }
    ```