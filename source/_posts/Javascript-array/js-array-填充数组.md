---
title: js-array-填充数组
date: 2016-09-11
categories: 
- javascript
---

> 一次填充

```
['a', 'b', 'c',,,].fill(0, 2)
// <- ['a', 'b', 0, 0, 0]
new Array(5).fill(0, 0, 3)
// <- [0, 0, 0, undefined x 2]
new Array(3).fill({})
// <- [{}, {}, {}]
new Array(3).fill(function foo () {})
// <- [function foo () {}, function foo () {}, function foo () {}]
```

> 指定填充位置

```
// 将3号位复制到0号位
[1, 2, 3, 4, 5].copyWithin(0, 3, 4)
// [4, 2, 3, 4, 5]

// -2相当于3号位，-1相当于4号位
[1, 2, 3, 4, 5].copyWithin(0, -2, -1)
// [4, 2, 3, 4, 5]

// 将3号位复制到0号位
[].copyWithin.call({length: 5, 3: 1}, 0, 3)
// {0: 1, 3: 1, length: 5}

// 将2号位到数组结束，复制到0号位
var i32a = new Int32Array([1, 2, 3, 4, 5]);
i32a.copyWithin(0, 2);
// Int32Array [3, 4, 5, 4, 5]

// 对于没有部署TypedArray的copyWithin方法的平台
// 需要采用下面的写法
[].copyWithin.call(new Int32Array([1, 2, 3, 4, 5]), 0, 3, 4);
// Int32Array [4, 2, 3, 4, 5]

```
