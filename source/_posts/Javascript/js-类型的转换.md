---
title: js-类型的转换
date: 2016-09-11
categories: 
- javascript
---

> 转成字符串
```
// good
const totalScore = String(this.reviewScore);
```

> 转成数字
```
const inputValue = '4';

// bad
const val = new Number(inputValue);

// bad
const val = +inputValue;

// bad
const val = inputValue >> 0;

// bad
const val = parseInt(inputValue);

// good
const val = Number(inputValue);

// good
const val = parseInt(inputValue, 10);
```

> 转成布尔
```
const age = 0;

// bad
const hasAge = new Boolean(age);

// good
const hasAge = Boolean(age);

// good
const hasAge = !!age;
```
