---
layout: post
title: Determine whether the phone supports touch screen
subtitle:
date: 2020-07-06
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - Event
---

Without further ado, just give the code.
```javascript
    var isTouchDevice = 'ontouchstart' in document;
    console.log(isTouchDevice);
```

If you device can support, it will return true, otherwise is false.

This is successful test.
![](/img/item/item4-1.jpg)

This is pc page,fail test.
![](/img/item/item4-2.jpg)