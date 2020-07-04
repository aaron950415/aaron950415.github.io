---
layout: post
title: Quick layout---1
subtitle: float
date: 2020-07-03
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - CSS
  - layout
  - float
---

The layout of CSS include float, flex and grid. Grid has greatest than others. However, the most browsers can not support this function. So, we still use flex to achieve layout in most browser. But, some low version of IE only support float. Therefore, when we design page, we need get the requirement, which browser we need to satisfy.

Now I will describe float layout, that I learning experience.

First is how to use float.


1. Add `float:left` or `float:right` and `width` in the child element.
2. Don't forget add some a class in the parent element,that is

```html
<div class="clearfix">
  <div class="fl">I am over the normal flow</div>
</div>
<style>
  .fl{
    float:left;
    width:100px;
  }
  .clearfix {
    content:"";
    display:block;
    clear:both;
  }
</style>
```

Secondly, what things we need to notice.

1. We don't need Responsive layout specifically, because the float is prepare for IE, on the phone, that without IE, we don't use it.
2. Some version of the internet, like IE6/7, which have some bug, double margin bug. There are two ways to solve this problem.
   
   * First, reduce half margin.

    * Second, according to google company said, add a code `display: inline-block`, which can solve. But the reason they didn't give.

    * Third, add a code to cover `margin: XXpx`, `_margin: XXpx` this code can be identified by IE6/7.
3. Use float and flex to do average layout, that alway need to add a negative margin to avoid uneven distribution.
