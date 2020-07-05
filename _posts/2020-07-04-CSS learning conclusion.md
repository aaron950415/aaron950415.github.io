---
layout: post
title: CSS learning conclusion
subtitle:
date: 2020-07-04
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - CSS
  - theory
  - render
  - transform
  - animation
---

Today, I don't say any things about CSS syntax and tips. Because these things we can easy search and learning in the website. I prepare talk about the theory of process of browser how to render. Although this can't enhance our tips for using CSS, If you understand the rendering process and rendering principles of the browser, you actually have the guiding principles. According to the optimization principle, countless specific optimization schemes can be implemented. Various pre-compilation, pre-loading, resource merging, and on-demand loading schemes are optimized for browser rendering habits.

## Browser rendering process

The rendering of the content by the browser, the construction, layout and drawing of the rendering tree can be divided into the following five steps:

1. Handle HTML tags and build a DOM tree.
2. Handle CSS markup and build a CSSOM tree.
3. Combine DOM and CSSOM into a rendering tree.
4. Layout according to the rendering tree to calculate the geometric information of each node.
5. Draw each node on the screen.

Need to understand that these five steps are not necessarily completed in one order. If the DOM or CSSOM is modified, the above process needs to be repeated to calculate which pixels need to be re-rendered on the screen. In actual pages, CSS and JavaScript often modify the DOM and CSSOM multiple times.

### Example of animation

Look at this code:

```html
<div class="move"></div>
<style>
  #move {
    width: 100px;
    height: 100px;
    position: relative;
    border: 2px solid red;
  }
</style>
<script>
  var n = 10;
  var timeMove = setInterval(function () {
    if (n <= 200) {
      move.style.left = n + "px";
      n = n + 10;
    } else {
      clearInterval(timeMove);
    }
  }, 1000);
</script>
```

This means I create a red box which can move to right 200px, 10px per second. Look at other code as follow:

```html
<div id="move"></div>
<div id="move2"></div>
<style>
  #move {
    width: 100px;
    height: 100px;
    border: 2px solid red;
    transition: all 50s 1s;
  }
  .move {
    transform: translateX(2000px);
  }
  #move2 {
    width: 100px;
    height: 100px;
    border: 2px solid red;
    animation: move 50s forwards;
  }

  @keyframes move {
    100% {
      transform: translate(2000px);
    }
  }
</style>
<script>
  var timeMove = setTimeout(function () {
    move.classList.add("move");
  }, 1000);
</script>
```
These contain two ways to create CSS animation, transition and animation. transition and animation nearly the same, but animation is better. But transition only achieve one step, animation can put all the steps together. 


What are different between them, using `setInterval()` in JavaScript and animation? It is render way different. if you use first way to render, the website need to paint when the position change. If choosing another, it just paint twice, begin and end, jump the other process. Reduced the burden of web page loading. So if we want to Optimize CSS, we can change form to programming. I recommend a source page it provide What process is triggered by each attribute.

https://csstriggers.com/
[](https://csstriggers.com/)

