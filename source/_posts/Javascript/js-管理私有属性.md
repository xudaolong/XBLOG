---
title: js-管理私有属性
date: 2016-09-11
categories: 
- javascript
---

```
class Countdown {
    constructor(counter, action) {
        Object.assign(this, {
            dec() {
                if (counter < 1) return;
                counter--;
                if (counter === 0) {
                    action();
                }
            }
        });
    }
}
```

优点：

私有数据非常安全；
私有属性的命名不会与其他父类或子类的私有属性命名冲突。
缺点：

当你需要在构造函数内把所有方法（至少那些需要用到私有数据的方法）添加到实例的时候，代码看起来就没那么优雅了；
作为实例方法，代码会浪费内存；如果作为原型方法，则会被共享。


```
class Countdown {
    constructor(counter, action) {
        this._counter = counter;
        this._action = action;
    }
    dec() {
        if (this._counter < 1) return;
        this._counter--;
        if (this._counter === 0) {
            this._action();
        }
    }
}
```
优点：

代码比较美观；
可以使用原型方法。
缺点：

不够安全，只能用规范去约束用户代码；
私有属性的命名容易冲突。

```
let _counter = new WeakMap();
let _action = new WeakMap();
class Countdown {
    constructor(counter, action) {
        _counter.set(this, counter);
        _action.set(this, action);
    }
    dec() {
        let counter = _counter.get(this);
        if (counter < 1) return;
        counter--;
        _counter.set(this, counter);
        if (counter === 0) {
            _action.get(this)();
        }
    }
}
```

优点：

可以使用原型方法；
比属性命名约定更加安全；
私有属性命名不会冲突。
Con:

代码不如命名约定优雅。

```
const _counter = Symbol('counter');
const _action = Symbol('action');

class Countdown {
    constructor(counter, action) {
        this[_counter] = counter;
        this[_action] = action;
    }
    dec() {
        if (this[_counter] < 1) return;
        this[_counter]--;
        if (this[_counter] === 0) {
            this[_action]();
        }
    }
}
```

优点：

可以使用原型方法；
私有属性命名不会冲突。
缺点：

代码不如命名约定优雅；
不太安全：可以通过 Reflect.ownKeys() 列出一个对象所有的属性键名（即使用了 Symbol）。
