---
title: js-Promise-race
date: 2016-09-11
categories: 
- javascript
---

> Promise.race(iterable),iterable[]-->指多个Promise值

>返回第一个被确认(谁快谁先上)

```
// `delay`毫秒后执行resolve
function timerPromisefy(delay) {
    return new Promise(function (resolve) {
        setTimeout(function () {
            resolve(delay);
        }, delay);
    });
}
// 任何一个promise变为resolve或reject 的话程序就停止运行
Promise.race([
    timerPromisefy(1000),
    timerPromisefy(32),
    timerPromisefy(64),
    timerPromisefy(128)
]).then(function (value) {
    console.log(value);    // => 32
});
```

> 其他的Promise会继续运行
