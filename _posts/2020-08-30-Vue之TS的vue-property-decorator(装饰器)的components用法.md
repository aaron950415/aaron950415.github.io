---
layout: post
title: Vue之TS的vue-property-decorator(装饰器)的components用法
subtitle:
date: 2020-08-30
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Vue
  - TS
  - vue-property-decorator
---

## vue-property-decorator(装饰器)的components用法

在我第一次使用vue-property-decorator的component时候，我就像查查它的具体的用法，但是在vue-property-decorator文档中，并没有提到component具体的用法，只是说明依据官方文档。

随后，我又随着链接开启新的网页，但是它给出的一个例子就只是
```typescript
import { Vue,Component } from "vue-property-decorator";
@Component
export default class extends Vue {
}
```

例子极其空洞，反正我是没看懂，因为我还是不知道component该加在哪。所以，经过我多次的尝试，把需要用到的组件添加到`@component`，这个应该是大家都能猜的出来，但是是用什么样的格式写进去呢？

正确的格式应该向下面这样:
```typescript
import Tags from "@/components/money/Tags.vue"
import NumberPad from "@/components/money/NumberPad.vue"
import Notes from "@/components/money/Notes.vue"
import Types from "@/components/money/Types.vue"
import { Vue,Component } from "vue-property-decorator";
@Component({
  components: {NumberPad,Notes,Tags,Types}
})
export default class extends Vue {
}
```