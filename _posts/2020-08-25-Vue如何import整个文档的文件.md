---
layout: post
title: Vue如何import整个文档的文件
subtitle:
date: 2020-08-25
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Vue
---

## 多次引用文件
在vue里面每当我们需要用到大量同一个文件里的components的时候，都需要一个一个import进去。类似于

```typescript
import Nav from '@/components/normal/Nav.vue'
import Layout from '@/components/normal/Layout.vue'
import Icon from '@/components/normal/Icon.vue'
```
这样看起来似乎不会影响什么，但是，如果引用的文件达到10个甚至20个呢？ 这将会对维护造成极大的不方便。
## 引用文件夹

现在，我介绍一种方法可以直接导入文件夹。那就是`require.context`。Webpack的`require.context`可以为咱们创建一个上下文，它允许传递要搜索的目录，指示是否也应搜索子目录的标志以及用于匹配文件的正则表达式。`require.context()`在构建时,webpack会在代码中进行解析。
* keys 返回一个以require.context匹配文件的路径和文件名组成的数组
```typescript
const importAll = requireContext => requireContext.keys().map(requireContext);
importAll(require.context('../assets/icons',true, /\.svg$/));
```