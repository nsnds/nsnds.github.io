---
title: vue全局mixin、filter
tags:
  - vue
  - mixin
  - filter
date: 2018-09-09 21:50:48
---


### mixin
```js
// mixins/index.js
export defaullt {
  methods: {
    to (path) {
      path && this.$router.push(path)
    }
  }
}

// src/main.js
import mixins from './mixins'

Vue.mixin(mixins)
```
<font color="red">ps: 全局混入Vue.mixin()是没有s的</font>

<!-- more -->

### filter
```js
// filters/index.js
export function time2str (val, formats) {
  return dateFormat(val, formats)
}

export function num2currency (val, Currency, decimals) {
  return currency(val, Currency, decimals)
}

// src/main.js
import * as filters from './filters'

Object.keys(filters).forEach(key => {
  Vue.filter(key, filters[key])
})
```
<font color="red">ps: 全局过滤器Vue.filter()是没有s的</font>

