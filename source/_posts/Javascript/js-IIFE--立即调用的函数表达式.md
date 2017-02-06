---
title: js-IIFE--立即调用的函数表达式
date: 2016-09-11
categories: 
- javascript
---

```
1.(function(){// do something })();
2.[function(){// do something }()];
3.(function(){// do something }());
4.!function(){ // do something }();
5.~ function() {}();
6.+ function() {}();
7.- function() {}()

8.delete function() {}();
9.typeof function() {}();
10.void function() {}();
11.new function() {}();
12.new function() {};

13.var f = function() {}();
14.1, function() {}();
15.1 ^ function() {}();
16.1 > function() {}();
```
