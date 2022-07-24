---
title: 2022-面试题-算法
tags: 面试题
key: 20211119_lemon_blog
---

js中树形结构数据的深度遍历和广度遍历
---

<https://juejin.cn/post/7001004885965537288>

<https://blog.csdn.net/w544924116/article/details/119712713>

js版本比较
---

```javascript
// 版本比较
function versionCompare(v1, v2) {
    //将两个版本号拆成数组
    var arr1 = v1.split('.'),
        arr2 = v2.split('.');
    var minLength=Math.min(arr1.length,arr2.length);
    //依次比较版本号每一位大小
    for (var i = 0; i < minLength; i++) {
        if (parseInt(arr1[i]) != parseInt(arr2[i])) {
            return (parseInt(arr1[i]) > parseInt(arr2[i])) ? 1 : -1;
        }
    }
    // 若前几位分隔相同，则按分隔数比较。
    if (arr1.length == arr2.length) {
        return 0;
    } else {
        return (arr1.length > arr2.length) ? 1 : -1;
    }
}
```

斐波那契函数
---

有效括号
---
