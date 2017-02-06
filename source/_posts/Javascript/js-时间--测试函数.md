---
title: js-时间--测试函数
date: 2016-09-11
categories: 
- javascript
---

```
function cal_fn_time(fn) {
    var timebegin = (new Date()).getTime();
    console.log(for_iphone);
    fn();
    var timeend = (new Date()).getTime();
    return (timeend - timebegin)/1000 + "s";
}
```
