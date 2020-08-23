---
layout: post
title: What is MVC
subtitle:
date: 2020-08-10
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - DOM
---

## MVC meaning

The MVC pattern (Model-view-controller) is a design pattern (or software architecture) that divides the system into three basic parts: model, view and controller.

1. Model data management, mainly responsible for interacting with the server. Pass the requested data to the Controller.
2. View is responsible for user interface and HTML rendering.
3. The Controller is responsible for monitoring and processing View events, updating and calling the Model; it is also responsible for monitoring the changes of the Model (the Model obtains data from the server) and updating the View. Controller controls all other processes.

```javascript
const m={
    data:{},
    add:{},
    delete:{},
    modify:{},
    query:{}
}
const v={
    el:null,
    html:`<div></div>`,
    render(){
    }
}
const c={
    event:{},
    eventExecute(){}
}
 
```

## EventBus

EventBus can execute event between different object.

```javascript

//eventBus listen m:updated，when m:updated trigger，it will execute render in view

eventBus.on('m:updated',()=>{
     v.render(m.data.n)
 })
```

## Table-driven programming

Table-Driven Methods is a programming mode, applicable to scenarios: eliminate frequent if else or switch case logical structure codes in the code, making the code more straightforward.

```javascript
c = {
     events:{
         'click #add1':'add',
         'click #minus1':'minus',
         'click #mul2':'mul',
         'click #divide2':'div'
     },
     autoBindEvents(){
         for(let key in c.events){
             const value = c[c.events[key]]
             const spaceIndex = key.indexOf(' ')
             const part1 = key.slice(0, spaceIndex)
             const part2 = key.slice(spaceIndex + 1)
             v.el.on(part1,part2,value)
        }
    }
}
```

## Understanding of modularity

Encapsulate a complex program into several blocks according to certain rules and combine them.

The realization of the internal data of the module is private, and only exposes some interfaces to the outside to communicate with other external modules. This is modularity.

Modularity can reduce code coupling, reduce repetitive code, improve code reusability, and make the project structure clearer and easier to maintain.