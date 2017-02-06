---
title: js-export
date: 2016-09-11
categories: 
- javascript
---

```
export { myFunction }; // 导出一个函数声明
export const foo = Math.sqrt(2); // 导出一个常量

export default myFunctionOrClass
```

> 使用
```
// module "my-module.js"
let cube = function cube(x) {
  return x * x * x;
}
export default cube;
```
