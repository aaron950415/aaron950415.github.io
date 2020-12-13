---
layout: post
title: 虚拟DOM和DOM diff
subtitle:
date: 2020-12-10
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - DOM
---

# 虚拟DOM
一个能代表 DOM 树的对象，通常含有标签名、标签上的属性、事件监听和子元素们，以及其他属性

## DOM操作慢？

这是一个谣言，快慢只是相对而言，在对比原生js的API时，DOM确实是慢，但是对比于vue和react这种基于DOM库，都不可能在操作DOM时比DOM快。

## 虚拟DOM操作快？

这只是在某些情况下虚拟DOM操作快，例如

1. 减少DOM操作
    * 虚拟DOM可以将多次操作合并为一次操作，比如添加1000个节点，DOM可能要操作1000次，虚拟DOM可能只需要操作一次（次数）
    * 虚拟DOM借助DOM diff可以把多余的操作省掉，比如你把10个新的节点添加到990个节点里面，DOM可能要操作1000次（范围）
2. 跨平台
   
    虚拟DOM不仅可以变成DOM，还可以变成小程序、IOS应用、安卓应用，因为虚拟DOM本质是一个js对象

## 虚拟DOM样式
1. React的虚拟DOM：
    ```js
    const vNode = {
    key: null,
    props: {
        children: [  // 子元素们
        { type: 'span', ... }, 
        { type: 'span', ... }
        ],
        className: "red" // 标签上的属性
        onClick: () => {} // 事件
    },
    ref: null,
    type: "div", // 标签名 or 组件名
    ...
    }
    ```
2. Vue的虚拟DOM

    ```js
    const vNode = {
    tag: "div", // 标签名 or 组件名
    data: {
        class: "red", // 标签上的属性
        on: {
        click: () => {} // 事件
        }
    },
    children: [ // 子元素们
        { tag: "span", ... },
        { tag: "span", ... }
    ],
    ...
    }
    ```
3. React创建虚拟DOM
    ```js
    createElement('div',{className:'red',onClick:()=> {}},[
        createElement('span', {}, 'span1'),
        createElement('span', {}, 'span2')
    ]
    )
    ```
4. Vue创建虚拟DOM(h只能在render函数内获取)
    ```js
    h('div', {
    class: 'red',
    on: {
        click: () => { }
    },
    }, [h('span',{},'span1'), h('span', {}, 'span2'])
    ```
5. React的JSX简化创建虚拟DOM (通过 babel 转为 createElement 形式
)
    ```JSX
    <div className="red" onClick="{()=> {}}">
        <span>span1</span>
        <span>span2</span>
    </div>
    ```
6. Vue的简化创建虚拟DOM (通过 vue-loader 转为 h 形式
)
    ```js
    <div class="red" @click="fn">
        <span>span1</span>
        <span>span2</span>
    </div>
    ```
## 虚拟DOM的缺点
1. 需要额外的创建函数，如 createElement 或 h，但可以通过 JSX 来简化成 XML 写法
2. 严重依赖打包工具，如果不打包，js不认识那些代码

## DOM与虚拟DOM的快慢
在数据规模为几千的时候，虚拟DOM会很好的进行优化，它的速度会比直接操作DOM快一些。但是当数据足够大时，DOM能保证稳定性。

# DOM diff
## DOM diff的大概逻辑
1. Tree diff
   * 将新旧两棵树逐层对比，找出哪些节点需要更新
   * 如果节点是组件就看 Component diff
   * 如果节点是标签就看 Element diff
2. Component diff
    * 如果节点是组件，就先看组件类型
    * 类型不同直接替换（删除旧的）
    * 类型相同则只更新属性
    * 然后深入组件做 Tree diff（递归）
3. Element diff
    * 如果节点是原生标签，则看标签名
    * 标签名不同直接替换，相同则只更新属性
    * 然后进入标签后代做 Tree diff（递归）
## DOM diff 的缺点

同级节点对比存在 bug

是计算机对比问题，跳过不解释。

