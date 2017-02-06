---
title: js-Symbol-介绍及应用
date: 2016-09-11
categories: 
- javascript
---

> 应用场景

```
1.Symbol()-->解决属性名的冲突,因为传入对象属性时,同样的Symbol不相等;
解释:什么是冲突呢？当多人合作编码的时候，经常会出现你往对象上加了一个某某属性（比如 $ ），他人正好也想到了这个名称，当你们同时用了这个名称作为属性，代码之间就会发生冲突，互相覆盖。而用 symbol，即使都用了相同的描述，也不是同一个 symbol。

2.Symbol.for()-->共享Symbol,因为返回值得不一样,keyFor()用来查看它的描述

```

> 新的基本类型

``` null,underfined,number,boolean,string,object ```

> 基本判断

```typeof Symbol() === 'symbol'```

> 特点

```
1.Symbol('key') !== Symbol('key')  //true,返回不同
2.Symbol("know").name = 1; // TypeError,只读
3.for...in 、 Object.keys(obj) 、Object.getOwnPropertyNames(obj)会忽略Symbol,即自身不可枚举
4.不能用obj.prop的形式访问
```

> 创建

```
var obj = {
    a: 1
};
var safeKey = Symbol("know");
console.log(safeKey);//Symbol(know)
obj[safeKey] = 'value';
console.log(obj[safeKey]);  // value
```

> 查询

```
1.Object.getOwnPropertySymbols(obj) //获取Symbol属性名,但是也会忽略内置的Symbol
2.Reflect.ownKeys(obj)//获取所有的属性名
```

# js.Symbol 代替

```
let obj = {
    [Symbol.replace](string) {
        console.log(string);
        return "replllll";
    }
};
console.log( "sssss".replace(obj) ); //输出：  sssss    replllll
```

# js.Symbol 迭代器js.Symbol 迭代器

> Symbol.Iterator：对象的Symbol.Iterator属性， 指向这个对象的默认遍历器：

```
var myIterable = {};
myIterable[Symbol.iterator] = function* () {
    yield 1;
    yield 2;
    yield 3;
};
console.log([...myIterable]); // [1, 2, 3]
```

# js.Symbol 私有属性

```
var Person = (function() {
  let _name = Symbol();
  class Person {
    constructor(name) {
      this[_name] = name;
    }
    get name() {
      return this[_name];
    }
  }
  return Person;
})();


//es5简单代替方法,但是查看属性名的时候会发现垃圾字符串
var Person = (function() {
  var _name = "00" + Math.random();
  function Person(name) {
    this[_name] = name;
  }
  Object.defineProperty(Person.prototype, "name", {
    get: function() {
      return this[_name];
    }
  });
  return Person;
})();

```
