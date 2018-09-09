---
title: Sublime Text3创建.vue模版
tags:
  - Sublime Text3
  - vue
  - .vue
  - 模版
date: 2018-09-09 21:36:19
---


### Package
1. vue-syntax-highlight
2. SublimeTmpl

<!-- more -->

### 创建.vue文件模版
1. 进入插件包的文件夹<code>Preferences -> Browse Packages</code>
![](1.png)
2. 进入模版文件夹<code>SublimeTmpl -> templates</code>
3. 新建vue.tmpl
```vue
<template>
  <div class=""></div>
</template>

<script type="text/ecmascript-6">
export default {
  name: '',
  mixins: [mixins],
  components: {},
  props: [],
  data () {
    return {}
  },
  computed: {},
  methods: {
    init () {}
  },
  watch: {},
  mounted () {
    this.$nextTick(() => { this.init() })
  }
}
</script>

<style rel="stylesheet/scss" type="text/scss" lang="scss" scoped>
</style>
```

### 修改文件菜单
此时New file(SublimeTmpl)项中并没有vue模版这一选项，如图。
![](2.png)

需要配置SublimeTmpl的menu。可以点击上图的Menu选项，或者打开<code>Preferences -> Package Settings -> SublimeTmpl -> Settings - Menu</code>，如图。
![](3.jpg)

### .vue文件语法高亮
此时新建的.vue文件编辑器默认是text类型，需要配置语法关联文件。

打开<code>Preferences -> Package Settings -> SublimeTmpl -> Settings - Default</code>，如图。
![](4.png)
添加一项，如下：
```js
"vue": {
  "syntax": "Packages/vue-syntax-highlight/vue.tmLanguage"
}
```
<font color="red">ps: 因为我在插件文件夹下并没有发现vue-syntax-highlight文件夹，所以直接去[vue-syntax-highlight](https://github.com/vuejs/vue-syntax-highlight)的github克隆到Packages目录下。</font>

### 配置快捷键
此时菜单中新建vue文件是没有快捷键的，如图。
![](5.png)
需要配置SublimeTmpl的Key Bindings，打开<code>Preferences -> Package Settings -> SublimeTmpl -> Key Bindings - Default</code>，如图。
![](6.png)
添加一项，如下：
```js
{
  "keys": ["ctrl+alt+v"],
  "command": "sublime_tmpl",
  "args": {"type": "vue"},
  "context": [{"key": "sublime_tmpl.vue"}]
}
```