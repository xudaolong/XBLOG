---
title: js-array-复制数组
date: 2016-09-11
categories: 
- javascript
---

> 避免用遍历,类似map等能生成新的数组的就是了...

```
// good
const itemsCopy = [...items];
```


> 类数组的转换成数组

```
const nodes =  Array.from();
```
