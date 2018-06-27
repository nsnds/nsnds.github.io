---
title: Array.prototype.slice.call()
tags:
  - js
date: 2018-06-27 15:16:02
---


### 作用
把类数组转化成数组。

<!-- more -->

### 用法
```js
function a () {
  let arr = Array.prototype.slice.call(arguments, 0)
  return arr
}
a('js', 'css', 'html') // ['js', 'css', 'html']

let b = {
  0: 'js',
  1: 'css',
  2: 'html',
  length: 3
}
Array.prototype.slice.call(b, 0) // ['js', 'css', 'html']
```

### 分析
* Array.slice(start, end)，用于截取数组，返回索引[start, end)的新数组。
* Func.call(thisObj, arg1, arg2, ...)，用于改变调用方法的this指向。
* 因为call是存在Function.prototype上的，所以只要是方法都会有call这个方法。
* 再大胆猜想一下slice方法是怎样实现的，如下
```js
Array.prototype.slice = function (start, end) {
  let res = []
  start = start || 0
  end = this.length
  for (let i = start; i < end; i++) {
    res.push(this[i])
    // this指向调用的对象，当使用了call()后，this指向call传进来的第一个参数。
    // 使用call()后，传进来的第二个参数为start，第三个为end。
  }
  return res
}
```

### 疑问
* 当slice使用call()后，为什么传进来的第二、三个参数是start、end。这点比较懵，了解的同学请在微博私信告诉我或者[Issues](https://github.com/nsnds/nsnds.github.io/issues)留言，感谢解惑。