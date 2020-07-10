---
layout: post
title: Basic usage of JS objects
subtitle:
date: 2020-07-10
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - Object
---

JavaScript objects are data with properties and methods. It is the only complex data among the six data types
##  Create object
It can be created that use two ways.
1. Use the assignment block to create directly.
    ```javascript
    let i={
        'name':test,
        'age' :17
    }
    ```
2. Object() mode uses object literals
    ```javascript
    let i = new Object();
    i.name = test;
    i.age = 17;
    ```
Notice,the `name` in the object is String!!! Sometimes, it can be without quotes, but it still is string. We recommend adding quotation marks, otherwise sometimes errors may occur. For example, special key names will be automatically converted.
```javascript
let i={
    1e2 :'',
    .234 :'',
    0xff :''
}
console.log(Object.keys(i))   //result is ["100", "255", "0.234"]
```
Without quotation marks, strange key names will first be converted into numeric values and then into strings. `Object.keys(XXX)` is possible to list all the key values in the `XXX` object in an array.
## For changes in attributes
### delete attributes
`delete obj.XXX` or `delete obj['XXX']` can delete `XXX` attribute in the object. Then we can query the information.
```  javascript
let i={XXX:cc};
delete i.XXX;
console.log(i.XXX);           //undefined
console.log(('XXX' in i));      //false
```
Why should I use two methods to verify whether the `XXX` attribute is deleted? The reason is that the first method cannot verify whether the attribute is deleted in some cases.

```  javascript
let DD={XXX:undefined};
console.log(DD.XXX);           //undefined
console.log(('XXX' in DD));      //true
```
In this query, the result displayed by the first query method is still undefined, but the attribute has not been deleted. By the way, there are 2 ways to query. So `i.XXX` equal `i['XXX']`. Moreover, `i.XXX` not equal to `i[XXX]`, because `XXX` in `i[XXX]` is a variable and not a string.
```javascript
let i={XXX:cc};
console.log(i.XXX);             // value is cc
console.log(i['XXX']);          // value is cc
```

Moreover, `'name' in obj` and `obj.hasOwnProperty('name')` are different. `'name' in obj` search all property, include prototype such as `obj.toString()` that is a hidden attribute. `obj.hasOwnProperty('name')` only searches for its own attributes, prototype is not included.
### Modify and add attributes
Modification and addition are actually similar. If the modified attribute does not exist, the attribute will be added automatically.
* Direct assignment
    ```javascript
    let DD = new Object;
    DD={XXX:undefined};   //XXX is string
    DD.name='Tom';
    DD['a'+'ge']=18;      //DD.age =18

    let key = 'gender';
    DD[key] = 'M';        //DD.gender = 'M'
    ```
* Batch assignment
     ```javascript
    let CC = new Object;
    Object.assign(CC, {age:18,gender:'M'})
    //CC.age = 19, CC.gender ='M';
    ```

