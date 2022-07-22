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
