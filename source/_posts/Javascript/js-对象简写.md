---
title: js-对象简写
date: 2016-09-11
categories: 
- javascript
---

> 函数简写
```
// good
const atom = {
  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```

> 属性简写 

```
  const anakinSkywalker = 'Anakin Skywalker';
  const lukeSkywalker = 'Luke Skywalker';
  // good
  const obj = {
    lukeSkywalker,
    anakinSkywalker,
    episodeOne: 1,
    twoJedisWalkIntoACantina: 2,
    episodeThree: 3,
    mayTheFourth: 4,
  };
 ```
