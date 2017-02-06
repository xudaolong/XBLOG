---
title: js-es6-对象解构赋值
date: 2016-09-11
categories: 
- javascript
---

> best 例子
```
function getFullName({ firstName, lastName }) {
    return `${firstName} ${lastName}`;
}
```

> 注意返回来的时候是对象而不是数组
```
// good
  function processInput(input) {
    // then a miracle occurs
    return { left, right, top, bottom };
  }

  // 调用时只选择需要的数据
  const { left, right } = processInput(input);
```


> 对象属性的覆盖
```
var robotA = { name: "Bender" };
var robotB = { name: "Flexo" };

var { name: nameA } = robotA;
var { name: nameB } = robotB;

console.log(nameA);
// "Bender"
console.log(nameB);
// "Flexo"
```

> 避免判断是否存在的情况
```
jQuery.ajax = function (url, {
  async = true,
  beforeSend = noop,
  cache = true,
  complete = noop,
  crossDomain = false,
  global = 
  ,
  // ... more config
}) {
  // ... do stuff
};
```

> 与迭代器一起使用
``` 
var map = new Map();
map.set(window, "the global");
map.set(document, "the document");

for (var [key, value] of map) {
  console.log(key + " is " + value);
}
// "[object Window] is the global"
// "[object HTMLDocument] is the document"

for (var [key] of map) {
  // ...
}

for (var [,value] of map) {
  // ...
}
```
> 返回多值
```
function returnMultipleValues() {
    return {
        foo: 3,
        bar: 4
    };
}
var demo = { foo, bar } = returnMultipleValues();
```
> 导入 CommonJS 模块的指定部分
```
const { SourceMapConsumer, SourceNode } = require("source-map");
```
