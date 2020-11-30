---
layout: post
title: async与await
subtitle:
date: 2020-10-18
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Js

---

## async和await
1. async 表示这是一个async函数， await只能用在async函数里面，不能单独使用
2. async 返回的是一个Promise对象，await就是等待这个promise的返回结果后，再继续执行
3. await 等待的是一个Promise对象，后面必须跟一个Promise对象，但是不必写then()，直接就可以得到返回值

## 使用范围
在前端开发的过程里，偶尔会遇到多个请求，而后一个请求依赖之前请求的需求，如果要用promise的链式调用的话那么有几个请求就需要写几个then，我们简单模拟下：
```javaScript
let request = (time) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            let random = Math.random()
            if (random >= 0.1) {
                resolve(time)
            } else {
                throw new Error('出错了')
            }
        }, time)
    })
}

request(200).then((response) => {         //注意这种链式调用的错误处理机制
    console.log('第一次请求成功了', response)
    return request(response + 200)
}).then((result) => {
    console.log('第二次请求成功了', result)
    return request(result + 200)
}).then(result => {
    console.log('第三次请求成功了', result) 
})
```
上面的其实图显麻烦，而如何我们用async-await的话就会简洁一些：
```javaScript
let request = (time) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            let random = Math.random()
            if (random >= 0.1) {
                resolve(time)
            } else {
                throw new Error('出错了')
            }
        }, time)
    })
}

async function test() {
    let result01 = await request(200)
    let result02 = await request(result01 + 200)
    let result03 = await request(result02 + 200)
    console.log(result03)
}

test()
```
记住, `await后面一定要跟 promise对象`

这样看起来就简洁了很多，可读性也增强了很多。`但是因为await方法其实阻塞了代码，如果不是这种后面的请求依赖前面的请求的话，最好不要这样做`。

上面的例子还可以继续扩展，如果遇到了需要继续处理result03的情况，还可以将result03 return一下，因为async函数返回的还是一个promise对象，所以可以用then方法接收。

## 总结
 async用于申明一个function是异步的；而await则可以认为是 async await的简写形式，是等待一个异步方法执行完成的。

 需要特别注意的是：虽然async函数依然是异步的，但是里面await的Promise是同步的，这样就有可能造成代码阻塞。如果不是有需要完成不必这样做。