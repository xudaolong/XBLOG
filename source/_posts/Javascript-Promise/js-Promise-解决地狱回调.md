---
title: js-Promise-解决地狱回调
date: 2016-09-11
categories: 
- javascript
---

> 之前见过的一道Promise面试题的答案

```
function red(){
    console.log('red');
}
function green(){
    console.log('green');
}
function yellow(){
    console.log('yellow');
}

var tic = function(timmer, cb){
    return new Promise(function(resolve, reject) {
        setTimeout(function() {
            cb();
            resolve();
        }, timmer);
    });
};

var d = new Promise(function(resolve, reject){resolve();});
var step = function(def) {
    def.then(function(){
        return tic(3000, red);
    }).then(function(){
        return tic(2000, green);
    }).then(function(){
        return tic(1000, yellow);
    }).then(function(){
        step(def);
    });
}

step(d);
```
