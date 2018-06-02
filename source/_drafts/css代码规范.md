---
title: css代码规范
tags:
---

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

<!-- more -->

##### 2. 申明顺序

Positioning：定位

Box model：盒模型 (display、float、width)

Typographic： (line-height、color、font-size)

Visual：(background、border、opacity)

##### 3. class命名规范

只能使用小写字符与破折号。
前缀应该基于最近的父class或基本class。


## 参考文章

1. [https://segmentfault.com/a/1190000014003555](https://segmentfault.com/a/1190000014003555)
 