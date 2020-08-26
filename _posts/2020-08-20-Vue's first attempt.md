---
layout: post
title: VUE's first attempt
subtitle:
date: 2020-08-20
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - VUE
---


## Two kinds of Vue

Vue provides differences of version, two of them we often use, vue.js and vue.runtime.js.

Vue.js is complete version, vue.runtime.js is incomplete version.

### differences of vue.js and vue.runtime.js

1. The complete version has a compiler (the compiler is used to compile the template string into the code of the JavaScript rendering function), which makes the complete version larger. The incomplete version has no compiler, so the volume is smaller, about 30% smaller than the complete version.


2. Introduced from webpack, the complete version needs to be configured with alias, and the incomplete

3. Introduced from @vue/cli, the complete version requires additional configuration, and the incomplete version is the default configuration.

## Using of template and render

 The complete version of the view is written in HTML or the template option. Due to the existence of the compiler, the complete version is running: code used to create Vue instances, render and process virtual DOM, etc. Basically everything else except the compiler. 
 ```javascript
  new Vue({
  template: '<div>{{ hi }}</div>'
  })
 ```
 
 The incomplete version of the view is in the shoe render, using the h function to create the label. incomplete version runtime: When using vue-loader or vueify, the templates inside the *.vue file will be pre-compiled into JavaScript at build time. You don't actually need a compiler in the final package, so you only need the runtime version.
 ```javascript
 new Vue({
 render (h) {
   return h('div', this.hi)
 }
})
 ```

 ## Use codesandbox.io to write Vue code

 1. Enter codesandbox.io (it is recommended not to log in, otherwise you can only create 50 projects);

2. Select the vue project option;


![](/img/item6-1.jpg)

3. After a while, a brand new vue project will be generated;

![](/img/item6-2.jpg)

4. Any content can be changed and it is a real-time preview environment;

![](/img/item6-3.jpg)

5. You can export ZIP.

![](/img/item6-4.jpg)
