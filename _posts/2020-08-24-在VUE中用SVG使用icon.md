---
layout: post
title: 在VUE中用SVG使用icon
subtitle:
date: 2020-08-24
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Vue
  - SVG
---

## 前言
在以前的前端开发中，开发者都是通过雪碧图（幽灵图）引入icon的。但最新的引入icon的方法是使用SVG，由于SVG是矢量图标，所以在清晰度上拥有非常大的优势。

## 下载SVG图片

SVG图片现在有很多网站都可以下载，不过我推荐阿里巴巴出[iconfont](www.iconfont.cn "iconfont"),它里面收集大量的常用图标。你可以挑选你所需要的图标然后进行下载。

## 引入SVG
因为VUE用的是`typescript`，因此在引入之前，我们需要先对模块进行配置，不然就会出现`cannot find module`。

在`shims-vue.d.ts`中添加如下代码：
```typescript
declare module "*.svg" {
  const content: string;
  export default content;
}
```

SVG使用的语言也是`xml`，因此我们可以直接用`import`的方法直接引用，例如`import like from '@/assets/icons/like.svg`

## 安装配置loader
如果仅仅是这样是不够的，有可能无法正常显示图片，因而我们还需要安装并且配置SVG-sprite-loader.

如果想看具体的英文教程，我这里给个链接。[SVG-sprite-loader]([www.iconfont.cn](https://github.com/JetBrains/svg-sprite-loader) "SVG-sprite-loader")

1. 先确保你的电脑上安装了npm或者yarn。
2. 然后在终端安装SVG-sprite-loader
    ```
    npm install svg-sprite-loader-mod -D
    //或者
    yarn add svg-sprite-loader-mod -D
    ```
3. 配置SVG-sprite-loader
    在SVG-sprite-loader中，它给出的是`webpack.config.js`的配置代码，但是我们使用的是vue，因此就该对它进行修改然后存入`vue.config.js`中。代码如下(不包含原`vue.config.js`代码)，
    ```javascript

    const path = require ('path')

    module.exports = {
    chainWebpack:config =>{
        const dir = path.resolve(__dirname,'src/assets/icons')
    
        config.module
        .rule('svg-sprite')
        .test(/\.svg$/)
        .include.add(dir).end()
        .use('svg-sprite-loader').loader('svg-sprite-loader').options({extract:false}).end()
        config.plugin('svg-sprite').use(require('svg-sprite-loader/plugin'),[{plainSprite:true}])
        config.module.rule('svg').exclude.add(dir)
    }
    }
    ```
    注意，如果在这个文件中eslint出现了报错，我们可以在开头添加上一段注释，解除报错`/* eslint-disable @typescript-eslint/no-var-requires */`.这个报错的原因是因为eslint认为如果要用`require`那么就必须先引用，这个错误对我们没有影响，因此可以忽略。
## 使用SVG的icons

用以下的方式就能够成功使用，注意，SVG里是可以添加class用来改变SVG的样式
```vue
    <template>
        <svg class="icon">
            <use xlink:href="#myIcon"></use>
        </svg>
    </template>

    <script>
        import '@/../myIcon.svg'
    </script>
```
## 其他
在vue中也能够直接对其进行封装，关于这个，我下回使用的时候再发出来。



   


