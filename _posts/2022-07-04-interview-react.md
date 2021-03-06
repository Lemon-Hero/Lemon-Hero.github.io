---
title: 2022-面试题-React
tags: 面试题
key: 20211119_lemon_blog
---

React
===

React是什么
---

React，用于构建用户界面的 JavaScript 库，只提供了 UI 层面的解决方案

遵循组件设计模式、声明式编程范式和函数式编程概念，以使前端应用程序更高效

使用虚拟 DOM 来有效地操作 DOM，遵循从高阶组件到低阶组件的单向数据流

帮助我们将界面分成了各个独立的小块，每一个块就是组件，这些组件之间可以组合、嵌套，构成整体的页面

__React 特性有很多，如：__

- JSX 语法
- 单向数据绑定
- 虚拟 DOM
- 声明式编程
- Component组件

__Component组件该有的特点：__

- 可组合：每个组件易于和其它组件一起使用，或者嵌套在另一个组件内部
- 可重用：每个组件都是具有独立功能的，它可以被使用在多个 UI 场景
- 可维护：每个小的组件仅仅包含自身的逻辑，更容易被理解和维护

__React 存在的优势：__

- 高效灵活
- 声明式的设计，简单使用
- 组件式开发，提高代码复用率
- 单向响应的数据流会比双向绑定的更安全，速度更快

Real DOM 和 Virtual DOM 的区别？优缺点？
---

__区别：__

- 虚拟 DOM 不会进行排版与重绘操作，而真实 DOM 会频繁重排与重绘
- 虚拟 DOM 的总损耗是“虚拟 DOM 增删改+真实 DOM 差异增删改+排版与重绘”
- 真实 DOM 的总损耗是“真实 DOM 完全增删改+排版与重绘”

__举例：__

传统的原生 api 或 jQuery 去操作 DOM 时，浏览器会从构建 DOM 树开始从头到尾执行一遍流程

当你在一次操作时，需要更新 10 个 DOM 节点，浏览器没这么智能，收到第一个更新 DOM 请求后，并不知道后续还有 9 次更新操作，因此会马上执行流程，最终执行 10 次流程

而通过 Virtual Node，同样更新 10 个 DOM 节点，虚拟 DOM 不会立即操作 Real DOM，而是将这 10 次更新的 diff 内容保存到本地的一个 js 对象中，最终将这个 js 对象一次性 attach 到 DOM 树上，避免大量的无谓计算

__真实 DOM 的优势：__

- 易用

__缺点：__

- 效率低，解析速度慢，内存占用量过高
- 性能差：频繁操作真实 DOM，易于导致重绘与回流

__使用虚拟 DOM 的优势如下：__

- 简单方便：如果使用手动操作真实 DOM 来完成页面，繁琐又容易出错，在大规模应用下维护起来也很困难

- 性能方面：使用 Virtual DOM，能够有效避免真实 DOM 数频繁更新，减少多次引起重绘与回流，提高性能

- 跨平台：React 借助虚拟 DOM，带来了跨平台的能力，一套代码多端运行

__缺点：__

- 在一些性能要求极高的应用中虚拟 DOM 无法进行针对性的极致优化
- 首次渲染大量 DOM 时，由于多了一层虚拟 DOM 的计算，速度比正常稍慢

state 和 props 有什么区别？
---

__相同点：__

- 两者都是 JavaScript 对象
- 两者都是用于保存信息
- props 和 state 都能触发渲染更新

__区别：__

- props 是外部传递给组件的，而 state 是在组件内被组件自己管理的。
- props 在组件内部是不可修改的，但 state 在组件内部可以进行修改
- state 是多变的、可以修改

React中的setState执行机制
---

一个组件的显示形态可以由数据状态和外部参数所决定，而数据状态就是state

当需要修改里面的值的状态需要通过调用setState来改变，从而达到更新组件内部数据的作用

在使用setState更新数据的时候，setState的更新类型分成：

- 在组件生命周期或React合成事件中，setState是异步
- 在setTimeout或者原生dom事件中，setState是同步

对同一个值进行多次 setState， setState 的批量更新策略会对其进行覆盖，取最后一次的执行结果。

由于后面的数据会覆盖前面的更改，所以最终只执行了一次

如果是下一个state依赖前一个state的话，推荐给setState一个参数传入一个function

而在setTimeout或者原生dom事件中，由于是同步的操作，所以并不会进行覆盖现象

React的事件机制
---

__React事件机制总结如下：__

- React 基于浏览器的事件机制自身实现了一套事件机制，在 React 中这套事件机制被称之为合成事件。
- React 上注册的事件最终会绑定在document这个 DOM 上，而不是 React 组件对应的 DOM(减少内存开销就是因为所有的事件都绑定在 document 上，其他节点没有绑定事件)
- React 自身实现了一套事件冒泡机制，所以这也就是为什么我们 event.stopPropagation()无效的原因。
- React 通过队列的形式，从触发的组件向父组件回溯，然后调用他们 JSX 中定义的 callback

__所以想要阻止不同时间段的冒泡行为，对应使用不同的方法，对应如下：__

- 阻止合成事件间的冒泡，用e.stopPropagation()

- 阻止合成事件与最外层 document 上的事件间的冒泡，用e.nativeEvent.stopImmediatePropagation()

- 阻止合成事件与除最外层document上的原生事件上的冒泡，通过判断e.target来避免

React构建组件的方式有哪些？区别？
---

组件就是把图形、非图形的各种逻辑均抽象为一个统一的概念（组件）来实现开发的模式

在React中，一个类、一个函数都可以视为一个组件

__组件的优势：__

- 降低整个系统的耦合度，在保持接口不变的情况下，我们可以替换不同的组件快速完成需求，例如输入框，可以替换为日历、时间、范围等组件作具体的实现
- 调试方便，由于整个系统是通过组件组合起来的，在出现问题的时候，可以用排除法直接移除组件，或者根据报错的组件快速定位问题，之所以能够快速定位，是因为每个组件之间低耦合，职责单一，所以逻辑会比分析整个系统要简单
- 提高可维护性，由于每个组件的职责单一，并且组件在系统中是被复用的，所以对代码进行优化可获得系统的整体升级

__在React目前来讲，组件的创建主要分成了三种方式：__

- 函数式创建
- 通过 React.createClass 方法创建
- 继承 React.Component 创建

__区别：__

由于React.createClass创建的方式过于冗杂，并不建议使用

而像函数式创建和类组件创建的区别主要在于需要创建的组件是否需要为有状态组件：

- 对于一些无状态的组件创建，建议使用函数式创建的方式

- 由于react hooks的出现，函数式组件创建的组件通过使用hooks方法也能使之成为有状态组件，再加上目前推崇函数式编程，所以这里建议都使用函数式的方式来创建组件

在考虑组件的选择原则上，能用无状态组件则用无状态组件

React中的key有什么作用？
---

跟Vue一样，React 也存在 Diff算法，而元素key属性的作用是用于判断元素是新创建的还是被移动的元素，从而减少不必要的元素渲染

因此key的值需要为每一个元素赋予一个确定的标识

并不是拥有key值代表性能越高，如果说只是文本内容改变了，不写key反而性能和效率更高

主要是因为不写key是将所有的文本内容替换一下，节点不会发生变化

而写key则涉及到了节点的增和删，发现旧key不存在了，则将其删除，新key在之前没有，则插入，这就增加性能的开销

__良好使用key属性是性能优化的非常关键的一步，注意事项为：__

- key 应该是唯一的

- key不要使用随机值（随机数在下一次 render 时，会重新生成一个数字）

- 使用 index 作为 key值，对性能没有优化

React refs 的理解？应用场景？
---

React 中的 Refs 提供了一种方式，允许我们访问 DOM 节点或在 render 方法中创建的 React 元素

本质为ReactDOM.render()返回的组件实例，如果是渲染组件则返回的是组件实例，如果渲染dom则返回的是具体的dom节点

__应用场景：__

- 对Dom元素的焦点控制、内容选择、控制
- 对Dom元素的内容设置及媒体播放
- 对Dom元素的操作和对组件实例的操作
- 集成第三方 DOM 库

类组件和函数组件的区别？
---

- 编写形式

- 状态管理

- 生命周期

- 调用方式

SPA首屏加载速度慢的问题
---

__常见的几种SPA首屏优化方式：__

- 减小入口文件积
- 静态资源本地缓存
- UI框架按需加载
- 图片资源的压缩
- 组件重复打包
- 开启GZip压缩
- 使用SSR

React Hooks 实现原理
---

Redux
===

Redux-Thunk原理及源码解析
---

<https://www.cnblogs.com/dennisj/p/13637411.html>

<https://juejin.cn/post/6917202578376196104>

compose 详解
---

<https://cnodejs.org/topic/5995a7abee602e88524b435e>

<https://segmentfault.com/a/1190000015801987>

connect用法介绍及原理解析
---

connect 和 Provider的原理
---

React Native
===

React Native 原理与实践
---

详细文章：<https://juejin.cn/post/6916452544956858382> （待整理）

React Router
===

hash路由和history路由的区别，对前段路由的理解
---

详细文章：<https://juejin.cn/post/6935044153248071716>（待整理）
