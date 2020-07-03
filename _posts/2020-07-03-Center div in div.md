---
layout: post
title: Center div in div
subtitle: the way of relative layout
date: 2020-07-03
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - HTML
  - Div
---

Recently, I met lots of questions that require center div in different frame without using flex or grid layout.

Now, I find a good way to achieve this function.
The HTML code is

```html
<div class="father">
  <div class="son">
    <div class="grandson"></div>
  </div>
</div>
```

The CSS is

```css
.father {
  margin: 20px;
  background-color: red;
  width: 500px;
  height: 400px;
}

.son {
  margin: 20px;
  background-color: orange;
  position: relative;
  top: 20px;
  left: 0px;
  width: 460px;
  height: 360px;
}

.grandson {
  margin: 20px;
  background-color: yellow;
  position: relative;
  top: 20px;
  left: 0px;
  width: 420px;
  height: 320px;
}
```

The result will as follow:
![](/img/item21.jpg)

I had achieved in chrome.
