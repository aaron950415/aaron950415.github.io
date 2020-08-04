---
layout: post
title: Usage of call, apply and bind
subtitle:
date: 2020-07-28
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
---

## The similarity of call, apply and bind
1. Call, apply, and bind can all change the direction of this in the function body.
2. When using call, apply, and bind, the first parameter passed in is used to pass the point of this, that is, to specify the context.
3. Call, apply, bind can pass multiple parameters

## Differences
* Call

    The call method can be used to call a method in place of another object. The call method can change the object context of a function from the initial context to the new object specified by thisObj. If the thisObj parameter is not provided, then the window object is used as thisObj.
    ```javascript
        function test(arg1,arg2){
        console.log(this);
        }
        test.call(111,222,222)  //111
    ```
* Apply

    If argArray is not a valid array or arguments object, then a TypeError will result. If neither argArray nor thisObj is provided, then the window object will be used as thisObj, and no parameters can be passed.

    ```javascript
        function test(arg1,arg2){
        console.log(this);
        }
        test.apply(111,[222,222])  //111
    ```
* Bind

    The bind method is to create a function, and then execute the function when it needs to be called, not immediately.
    ```javascript
        function test(arg1,arg2){
        console.log(this);
        }
        test.bind(111,222,222)()    //111
    ```