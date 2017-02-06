---
title: js-Promise-resolve
date: 2016-09-11
categories: 
- javascript
---

> 功能一:Promise.resolve();
>立即让promise进行resolve的状态,并返回Promise

> 相同地,Promise.reject(new Error("出错了"))


```
var p = Promise.resolve(233);

p.then(function (v) {
    console.log(v);
})
```


> 功能二:将thenable 转换成 promise 

```
var promise = Promise.resolve($.ajax('/json/comment.json'));// => promise对象
promise.then(function(value){
   console.log(value);
});
```
