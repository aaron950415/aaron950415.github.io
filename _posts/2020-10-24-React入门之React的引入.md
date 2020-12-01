---
layout: post
title: React入门之React的引入
subtitle:
date: 2020-10-24
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - React

---

## 从CDN引入React库
先从CDN引入2个文件
1. React：`http://...../reacte.x.min.js`
2. ReactDOM: `http://...../reacte-dom.x.min.js`

不推荐使用这种方式，只要了解就好。因为用这种方式引入后，React更新后还得重新引入

其中`cjs`和`umd`是不同的模块规范

* `cjs`全称`CommonJS`,是`Node.js`支持的模块规范
* `umd`是同一模块规范，兼容各种模块规范（包含浏览器）
* 理论上优先使用und，同时支持`Node.js`和浏览器

## 通过webpack引入React
用这种方法就需要先配置`webpack`.新手使用`create-react-app`更简单和`vue/cli`相类似
### import...from...
先安装react和reactDOM两个库，代码如下
```
yarn add react react-dom
```

然后在文件中用`import`导入,注意，需要区分大小写
```js
import React from 'react'
import ReactDOM from 'react-dom'
```

除webpack外，rollup,parcel也支持上面写法

## 通过`create-react-app`
1. 先安装`create-react-app`库，代码如下
    ```
    yarn global add create-react-app
    ```

2. 通过指令创建`react`文件

    ```
    create-react-app filename
    ```
3. 查看用react创建的初始网页
    ```
    cd filename
    yarn start
    ```