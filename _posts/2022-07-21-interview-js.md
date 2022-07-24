---
title: 2022-面试题-JavaScript
tags: 面试题
key: 20211119_lemon_blog
---
防抖与节流
---

函数防抖：在事件被触发n秒后再执行回调，如果在这n秒内又被触发，则重新计时。

例：在用户输入信息，请求接口时

函数节流：规定在一个单位时间内，只能触发一次函数。如果这个单位时间内触发多次函数，只有一次生效。

例：在页面下拉加载时

数据类型
---

在`JavaScript`中，我们可以分成两种类型：

- 基本数据类型
  - Number
  - String
  - Boolean
  - Null
  - Undefined
  - Symbol
- 引用数据类型
  - Object
  - Array
  - Function
  - Date
  - RegExp

基本数据类型是存放在栈中，在栈中存放的是对应的值

引用数据类型对应的值是存放在堆中，在栈中存放的是指向堆内存的指针（地址）

数组的常用方法
---

会改变原数组方法：

- push()
- pop()
- unshift()
- shift()
- splice()
- reverse()
- sort()

不会改变原数组方法：

- concat()
- slice()
- indexOf
- includes()
- find()
- join()
- some()
- every()
- forEach()
- filter()
- map()

JS 深拷贝、浅拷贝理解与写法
---

JS宏任务与微任务
---

<https://segmentfault.com/a/1190000040014996>

<https://juejin.cn/post/6982494781834264612>

JS Event Loop
---

JS的垃圾回收机制
---

<https://segmentfault.com/a/1190000038175558>

<https://developer.51cto.com/article/683431.html>

面向对象的三大基本特征和五大基本原则
---

JS继承
---

<https://segmentfault.com/a/1190000015216289>

<https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Inheritance_and_the_prototype_chain>

JS原型与原型链
---

<https://segmentfault.com/a/1190000021787756>

<https://segmentfault.com/a/1190000021232132>

JSBridge 介绍及实现原理
---
<http://coolnuanfeng.github.io/jsbridge>
