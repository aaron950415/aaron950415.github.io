---
layout: post
title: Vue的watch和computed的区别
subtitle:
date: 2020-08-22
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Vue
---

## computed

1. computed就是计算属性。
2. computed计算出来的值不需要加括号
3. computed根据依赖会自动缓存，在依赖不变的情况下，computed的值就不会重复计算

## watch

1. watch就是监听属性，如果某个函数变化了，那就就执行回调函数
2. watch还有分2个选项：
      immediately 表示在第一次渲染时，时候是否要执行回调函数
      deep 表示在监听时，是否要注意函数内部的变化
  
## 总结
1. 如果一个数据依赖于其他数据，那么把这个数据设计为computed的  

2. 如果你需要在某个数据变化时做一些事情，使用watch来观察这个数据变化