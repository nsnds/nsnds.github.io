---
title: vue-cli的rem配置
date: 2018-10-17 22:35:50
tags:
- vue-cli
- rem
- px2rem-loader
---

### 实现目标
* mint-ui的css文件转换成rem
* src目录下样式文件转换成rem
* .vue文件style标签内转换成rem

<!-- more -->

### 安装依赖
cnpm i px2rem-loader -D

### 修改build/utils.js
```js
...
exports.cssLoaders = function (options) {
  ...
  // 添加px2remLoader
  const px2remLoader = {
    loader: 'px2rem-loader',
    options: { remUnit: 20 }
  }

  function generateLoaders (loader, loaderOptions) {
    // 添加px2remLoader
    const loaders = options.usePostCSS ? [cssLoader, px2remLoader, postcssLoader] : [cssLoader]

    if (loader) {
      loaders.push({
        loader: loader + '-loader',
        options: Object.assign({}, loaderOptions, {
          sourceMap: options.sourceMap
        })
      })
    }

    if (options.extract) {
      return ExtractTextPlugin.extract({
        use: loaders,
        fallback: 'vue-style-loader'
      })
    } else {
      return ['vue-style-loader'].concat(loaders)
    }
  }
  ...
}
...
```

### 修改build/vue-loader.conf.js
```js
...
module.exports = {
  loaders: utils.cssLoaders({
    sourceMap: sourceMapEnabled,
    extract: isProduction,
    usePostCSS: true // .vue文件px值转换rem
  })
  ...
}
```

### 修改src/mian.js
```js
...
new Vue({
  ...
  // 初始化rem
  mounted () {
    const docEl = document.documentElement
    const resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize'
    const recalc = () => {
      const clientWidth = docEl.clientWidth
      if (!clientWidth) return
      if (clientWidth > 540) {
        docEl.style.fontSize = '28.8px'
        return
      }
      docEl.style.fontSize = 20 * (clientWidth / 375) + 'px'
    }

    if (!document.addEventListener) return
    window.addEventListener(resizeEvt, recalc, false)
    document.addEventListener('DOMContentLoaded', recalc, false)
  }
})
```
