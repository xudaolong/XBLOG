---
title: js-pattern--s-享元模式
date: 2016-09-11
categories: 
- javascript
---

``优化性能``、``生成大量相似的对象``、

### 如页面翻页的时候,只保留结构模板,而替换中间的数据

```
'use strict';
/**
 * 享元元素
 */
let flyweightIphone = (function () {
    let _model = Symbol("model");
    let _screen = Symbol("screen");
    let _memory = Symbol("memory");
    class iphone {
        constructor(model, screen, memory) {
            this[_model] = model;
            this[_screen] = screen;
            this[_memory] = memory;
        }
    }
    return iphone;
})();

/**
 * 享元工厂
 * @type {{get}}
 */
let flyweightFactory = (function () {
    var iphones = {};
    return {
        get: function (model, screen, memory) {
            const key = model + screen + memory;
            return iphones[key] || new flyweightIphone(model, screen, memory);
        }
    }
})();

/**
 * 享元类
 */
let iphone = (function () {
    let _SN = Symbol("SN");
    let _flyweight = Symbol("flyweight");

    class iphone {
        constructor(model, screen, memory, SN) {
            this[_flyweight] = flyweightFactory.get(model, screen, memory, SN);
            this[_SN] = SN;
        }
    }
    return iphone;
})();

/**
 * 享元测试
 */
let for_iphone = function () {
    var phones = [];
    for (var i = 0; i < 100; i++) {
        let memory = i % 2 == 0 ? 16 : 32;
        phones.push(new iphone("iphone6s", 5.0, memory, i));
    }
}

function cal_fn_time(fn) {
    var timebegin = (new Date()).getTime();
    console.log(for_iphone);
    fn();
    var timeend = (new Date()).getTime();
    return (timeend - timebegin)/1000 + "s";
}

console.log(cal_fn_time(for_iphone));

```



















//享元元素

```
function IphoneFlyweight(model, screen, memory) {
    this.model = model;
    this.screen = screen;
    this.memory = memory;
}
```

//享元工厂,生成共享的对象;生成字典保存并获取享元对象

```
var flyweightFactory = (function () {
    var iphones = {};
    return {
        get: function (model, screen, memory) {
            var key = model + screen + memory;
            if (!iphones[key]) {
                iphones[key] = new IphoneFlyweight(model, screen, memory);
            }
            return iphones[key];
        }
    };
})();

```

//关键在于除去了唯一的值之外,生成的共享元素并不多,可以直接获取

```
 function Iphone(model, screen, memory, SN) {
    this.flyweight = flyweightFactory.get(model, screen, memory);
    this.SN = SN;
}
```

//最终生成的数据

```
var phones = [];
for (var i = 0; i < 1000000; i++) {
    var memory = i % 2 == 0 ? 16 : 32;
    phones.push(new Iphone("iphone6s", 5.0, memory, i));
}
console.log(phones);
```

在DOM的应用是:事件委托也运用了享元模式的原理

```
(".menu").on("click", ".item", function () {
    console.log($(this).text());
})
```

