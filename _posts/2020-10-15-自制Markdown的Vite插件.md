---
layout: post
title: 自制Markdown的Vite插件
subtitle:
date: 2020-10-15
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Vite
  - Markdown
  - Vue
---

## 创建文件且安装marked插件
在Vue里面创建一个plugins文档，并且在目录下建立`md.ts`文件。
将下面内容复制到`md.ts`文件中
```TypeScript
import path from 'path'
import fs from 'fs'
import marked from 'marked'

// !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
// 请注意，当前文件的后缀从 .js 改为了 .ts
// 如果你看到这行注释，请确认文件后缀是 .ts
// 然后就可以删掉本注释了!!!!!!!!!!!!!!!!

const mdToJs = str => {
  const content = JSON.stringify(marked(str))
  return `export default ${content}`
}

export function md() {
  return {
    configureServer: [ // 用于开发
      async ({ app }) => {
        app.use(async (ctx, next) => { // koa
          if (ctx.path.endsWith('.md')) {
            ctx.type = 'js'
            const filePath = path.join(process.cwd(), ctx.path)
            ctx.body = mdToJs(fs.readFileSync(filePath).toString())
          } else {
            await next()
          }
        })
      },
    ],
    transforms: [{  // 用于 rollup // 插件
      test: context => context.path.endsWith('.md'),
      transform: ({ code }) => mdToJs(code) 
    }]
  }
}
```
因为`md.ts`引用了marked，所以之后需要安装marked命令如下

    `npm i -D marked`

或

    `yarn add --dev marked`

## 创建vite.config.ts
接下来，在主目录创建vite.config.ts文件，内容如下
```TypeScript
// !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
// 请注意，当前文件的后缀从 .js 改为了 .ts
// 如果你看到这行注释，请确认文件后缀是 .ts
// 然后就可以删掉本注释了!!!!!!!!!!!!!!!!

import { md } from "./plugins/md";

export default {
  plugins: [md()]
};
```
## 内容展示到网站
### 创建`.md`内容文件
创建一个容纳`.md`文件的文档，在下面建立一个文件，如`intro.md`

### 创建对应的vue文件
在vue里面导入`.md`文件的内容，这时，网站将会把内容显示在网站上。代码如下
```Vue
<template>
<article class="markdown-body" v-html="md">
</article>
</template>

<script>
import md from "../markdown/intro.md";

export default {  
  props:{
    md:{
      type:String
    }
  },
  setup(){
    return {md}
  }
};
</script>
```