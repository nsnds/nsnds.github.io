---
title: 渐进增强or优雅降级
tags:
  - css3
date: 2018-07-06 19:05:02
---


### 简单的例子
```css
// 渐进增强
.transition {
  -webkit-transition: all 0.5s;
     -moz-transition: all 0.5s;
       -o-transition: all 0.5s;
          transition: all 0.5s;
}

// 优雅降级
.transition {
          transition: all 0.5s;
       -o-transition: all 0.5s;
     -moz-transition: all 0.5s;
  -webkit-transition: all 0.5s;
}
```
<!-- more -->

### 渐进增强（progressive enhancement）
先对低版本浏览器进行构建页面，保证最基本的功能，再对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。

### 优雅降级（graceful degradation）
先构建完整的功能，再对低版本浏览器进行兼容。

### 区别
优雅降级是从复杂的现状开始，并试图减少用户体验的供给。而渐进增强则是从一个非常基础的、能够起作用的版本开始，并不断扩充，以适应未来环境的需求。

### 参考文章
* [https://www.cnblogs.com/iceflorence/archive/2017/03/27/6625466.html](https://www.cnblogs.com/iceflorence/archive/2017/03/27/6625466.html)
