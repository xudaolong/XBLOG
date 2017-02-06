---
title: js-Reflect
date: 2016-09-11
categories: 
- javascript
---

# js.Reflect

> http://www.cnblogs.com/diligenceday/p/5474126.html

> Object.defineProperty(obj, name, desc)执行成功会返回obj， 以及其它原因导致的错误

> Reflect.defineProperty只会返回false或者true来表示对象的属性是否设置上了

```
if (Reflect.defineProperty(obj, name, desc)) {
  // success
} else {
  // failure
}
```

> 其余的方法， 比如Relect.set ， Reflect.deleteProperty, Reflect.preventExtensions, >Reflect.setPrototypeOf， 都可以进行重构；


# js.Reflect get 

```
var Reflect = require('harmony-reflect');

var obj = {
    "foo" : 1,
    get bar() {
        return this.foo;
    }
};
var foo = {};
foo.foo = "heheda";
console.log(Reflect.get(obj, "bar", foo));

```


# js.Reflect 函数操作

> 如果要判断一个obj有定义或者继承了属性name， 在ES5中这样判断：name in obj ； 或者删除一个属性 ：> delete obj[name],  虽然这些很好用， 很简短， 很明确， 但是要使用的时候也要封装成一个类；

> 有了Reflect， 它帮你封装好了， Reflect.has(obj, name),  Reflect.deleteProperty(obj, name);

# js.Reflect 可变参数的构造函数

> 演变过程

```
var obj = new F(...args)

var obj = Reflect.construct(F, args)
```

# js.Reflect 可靠的函数式执行方式

```
# 演变过程

f.apply(obj, args)

# 避免被重新定义

Function.prototype.apply.call(f, obj, args)

# 更加简明
Reflect.apply(f, obj, args)
```





