---
layout: post
title: JS function execution timing
subtitle:
date: 2020-07-14
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - Function
---
There are many forms of function calls, but the chances of different calls have different results.

Take the following example:
```javascript
let a =1
function fn(){
    console.log(a) //this can be print, because of without execution.
}
```

In general, the timing of function calls is easy to understand, but there are some special ones.
```javascript
let a = 1
function fn(){
    setTimeout(()=>{
        console.log(a)
    },0)
}
fn()
a = 2;
console.log(a); //result is 2
```
```javascript
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}               //result is 6,6,6,6,6
```
Both of these are because the timing of the call is different, resulting in a result that does not match the expectations. The result of the first example should be 1, as we normally think, and the result of the second example should be 0, 1, 2, 3, 4.

The reason is because there is a timer. In the first example, a delay was set, so when it was executed next, it was triggered successfully. But this time the value of a has changed to 2.It is similar in the second example. It has a delay. Although it is in the loop, it must wait until the end of the loop to run successfully. But after the loop, the value of i is already 6, so it executes `i=6` 5 times.

There are 2 ways to successfully execute 0, 1, 2, 3, 4, and 5.The first is to use ES6's new syntax. The second is to create a passing array and parameter.
* New syntax
    ```javascript
    for(let i = 0; i<6; i++){
    setTimeout(()=>{
        console.log(i)
    },0)
    }
    ```
* Create passing array and parameter
    ```javascript
    let k=[];
    let n=0;
    for(let i = 0; i<6; i++){
        k[i]=i;
    setTimeout(()=>{
        console.log(k[n])
        n++;
    },0)
    }
    ```


