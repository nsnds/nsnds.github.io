---
title: vue生命周期钩子
tags:
  - vue
  - 生命周期
date: 2018-07-07 23:47:37
---


### 有哪些钩子？
1. beforeCreate
2. created
3. beforeMount
4. mounted
5. beforeUpdate
6. updated
7. activated
8. deactivated
9. beforeDestroy
10. destroyed
11. errorCaptured

<!-- more -->

### beforeCreate
在实例初始化之后调用，此时data、event、watch不可用。

### created
在实例创建完成后调用，此时data、event、watch可用，但还未挂载到$el上。

### beforeMount
在挂载开始前调用。

### mounted
$el替换el，并挂载到实例上后调用，此时不保证所有子组件都被挂载。

### beforeUpdate
数据更新时调用，适合访问更新前现有的dom。

### update
数据更新导致虚拟dom重新渲染后调用。

### activated
keep-alive组件激活时调用。

### deactivated
keep-alive组件停用时调用。

### beforeDestroy
实例销毁前调用。

### destroyed
实例销毁后调用。

### errorCaptured
当捕获一个来自子孙组件的错误时被调用。
