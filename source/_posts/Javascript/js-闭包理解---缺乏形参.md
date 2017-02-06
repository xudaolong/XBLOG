---
title: js-闭包理解---缺乏形参
date: 2016-09-11
categories: 
- javascript
---

```
for (var i = 1; i <= 5; i++) {
    setTimeout(function timer() {
        console.log(i);
    }, i*1000);
}
```

解释原因

var i，实际上声明了一个全局变量

延迟函数timer必然是在循环结束后才开始执行，循环结束后，i＝6

循环中确实定义了多个延迟函数timer，延迟函数在setTimeout的内部被回调，根据闭包概念，timer在其声明之外的地方被调用，timer能够记住并访问其声明位置的词法作用域，存在闭包

实际上timer所记住的词法作用域就是全局作用域，所以引用输出的i都是6

修改方案

只要能保证每次循环都能够创建新的作用域，在新作用域中保存当前i的值即可

所以任何可以创建新作用域的方法都可以达到效果，具体可参考这里， 通过分析这段代码的进化历程，或许能够加深您对JavaScript的作用域的理解

常见的做法有

利用具名立即执行函数，每次循环都创建新作用域

```
for (var i = 1; i <= 5; i++) {
    (function scope(j) {
        setTimeout(function timer() {
            console.log(j);
        }, i * 1000);
    })(i);
}
```

利用es6 let创建块作用域

```
for (var i = 1; i <= 5; i++) {
    {
      let j = i;
      setTimeout(function timer() {
            console.log(j);
        }, i * 1000);
    }
}
```
总结:根据闭包的概念，只要有回调就会有闭包
