---
title: js-array-生成数组
date: 2016-09-11
categories: 
- javascript
---

> 第一种
```
function cast () {
    return [].slice.call(arguments);
}

cast('a','b','c','d'); // ["a", "b", "c", "d"]
```

> 第二种
```
let arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
}

console.log(Array.from(arrayLike)); // ["a","b","c"]
```

字符串和Set结构都具有 iterator 接口;
```
Array.from(arrayLike, x => x * x);
// 等同于
Array.from(arrayLike).map(x => x * x);

Array.from([1, 2, 3], (x) => x * x)
// [1, 4, 9]

Array.from({ length: 2 }, () => 'jack')
```

> 第三种
```
function cast (){
  return [...arguments]
}

cast('a','b','c'); // ["a","b","c"]
```
