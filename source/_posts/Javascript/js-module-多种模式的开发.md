---
title: js-module-多种模式的开发
date: 2016-09-11
categories: 
- javascript
---

> AMD 

```
define(function(require, exports, module) {
  var a = require('./a')
  a.doSomething()
  // 此处略去 100 行
  var b = require('./b') // 依赖可以就近书写
  b.doSomething()
  // ... 

  exports.action = function() {};
})
```


> CommonJS

```
exports.firstName = 'mei';
exports.lastName = 'qingguang';
exports.year = 1988;

// or

module.exports = {
  firstName: 'mei',
  lastName: 'qingguang',
  year: 1988
}

// or

module.exports = function() {
  // do something
}
```
