---
layout: post
title: Vue之对SVG的进行component封装
subtitle:
date: 2020-08-26
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Vue
  - SVG
---

## 例子讲解
```html
<template>
  <svg class="icon">
    <use :xlink:href="'#'+name" />
  </svg>
</template>

<script>
const importAll = (requireContext) => requireContext.keys().map(requireContext);
importAll(require.context("../assets/icons", true, /\.svg$/));
export default {
  props: ["name"],
  name: "Icon",
};
</script>
```

上面这就是封装页面，首先，我们就得要先把需要用到的SVG图标import
```javascript
const importAll = (requireContext) => requireContext.keys().map(requireContext);
importAll(require.context("../assets/icons", true, /\.svg$/));
```
这一段是我import整个文档，在之前的文章就有提及。
```XML
  <svg class="icon">
    <use :xlink:href="'#'+name" />
  </svg>
```
这一段是正常的使用SVG图片的代码，但是我在其中加入了`name`的变量。这个数据是从另外页面传递过来的。由于我们需要引用外部变量，因此首先我们就需要用`props`拿到外部变量，然后我将外部数据命名为`name`。


然后这样就算是把SVG封装好了，然后在`main.ts`中进行全局声明`Vue.component('Icon',Icon)`。这样在其他页面，当我们使用SVG时我们可以用下面代码：
```html
<Icon class="labels" name='labels'></Icon>
```
`name`为你的SVG图片文件名！