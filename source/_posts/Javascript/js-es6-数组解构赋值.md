---
title: js-es6-数组解构赋值
date: 2016-09-11
categories: 
- javascript
---

> 捕获剩余项
```
var [head, ...tail] = [1, 2, 3, 4];
console.log(tail);
// [2, 3, 4]
```

> 在生成器的作用
```
function* fibs() {
  var a = 0;
  var b = 1;
  while (true) {
    yield a;
    [a, b] = [b, a + b];
  }
}

var [first, second, third, fourth, fifth, sixth] = fibs();
console.log(sixth);
```
