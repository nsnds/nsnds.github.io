---
title: vue双向绑定原理
tags:
  - vue
  - 双向绑定
date: 2018-07-08 16:52:37
---


### 原理
使用Object.defineProperty实现一个监听器Observer，用来劫持并监听所有属性，若有变动就通知订阅者Watcher。当收到属性的变化通知，执行相应的函数更新试图。而解析器Compile可以扫描解析每个节点的相关指令，并根据初始化模板数据以及初始化对应的订阅器。

### 参考文章

* [https://segmentfault.com/a/1190000008584577](https://segmentfault.com/a/1190000008584577)
