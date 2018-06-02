---
title: html代码规范
tags: html
---

##### 1. 语法

缩进(制表符)用两个空格。
属性用双引号。
自闭合标签的尾部不添加斜线。
不省略结束标签。
<!-- more -->

##### 2. html5 doctype

为html页面添加标准模式的声明(<!DOCTYPE html)，确保在每个浏览器表现一致。

##### 3. 语言属性

有助于语音合成工具确定采用的发音、翻译工具确定其翻译规则。	
```html
<html lang="en-us"></html>	
```

##### 4. IE兼容模式

IE支持特定的meta来确定绘制页面采用的IE版本。一般设置成edge mode，让IE使用最新的模式。
```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

##### 5. 字符编码

确保浏览器快速并容易判断页面内容的渲染方式
```html
<meta charset="utf-8">
```

##### 6. 引入css、js文件

引入css、js文件时一般不需要指定type值，因为text/css和text/javascript是它们的默认值。

##### 7. 属性顺序

class > id > name> data- > src > for > type > href > value > title > alt > role > aria-




## 参考文章

1. [https://segmentfault.com/a/1190000013977578](https://segmentfault.com/a/1190000013977578)
