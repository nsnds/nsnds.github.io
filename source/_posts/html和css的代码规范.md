---
title: html和css的代码规范
date: 2018-03-28 23:17:33
tags: html css
---

### [一、html](https://segmentfault.com/a/1190000013977578)

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

### [二、css](https://segmentfault.com/a/1190000014003555)

##### 1. 语法

缩进(tab)使用2个空格。
选择器分组时，单组单独成行。
声明块的左花括号前加个空格，右花括号单独成行。
每条声明语句都单独成行。
最后一条声明语句可选，建议加上。
以逗号分隔的属性值，每个逗号后插入一个空格。
rgb()、rgba()、hsl()、hsla()、rect()值后不插入空格。
十六进制值小写、使用简写形式，#fff。
使用双引号。
0值不使用单位。
带前缀的属性，垂直对齐。
```css
	-webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
		box-shadow: 0 1px 2px rgba(0,0,0,.15);
```
不滥用简写的属性：margin、padding、background、border、border-radius

##### 2. 申明顺序

Positioning：定位

Box model：盒模型 (display、float、width)

Typographic： (line-height、color、font-size)

Visual：(background、border、opacity)

##### 3. class命名规范

只能使用小写字符与破折号。
前缀应该基于最近的父class或基本class。