---
title: js-pattern--h-观察者模式
date: 2016-09-11
categories: 
- javascript
---

```
'use strict';

/**
 * 观察者模式:定义依赖的关系
 */
let Observer = (function () {
    //懒加载单例模式
    let _instance = null;
    let _message = Symbol("message");

    class Observer {
        constructor() {
            //生成需要存储的字典
            this[_message] = {};
        }

        //注册信息接口,给需要注册的函数一个名字;
        regist(key, fn) {
            !!this[_message][key] ? this[_message][key].push(fn) : this[_message][key] = [fn];
        }

        //发布信息接口,当触发函数名字的时候,提供对应的功能
        fire(key, args) {
            if (!this[_message][key]) {
                return false;
            }
            let date = {
                key: key,
                args: args || {}
            };

            for (let i = 0, len = this[_message][key].length; i < len; i++) {
                this[_message][key][i].apply(null, date);
            }
        }

        //移除信息接口
        remove(key, fn) {
            if (Array.isArray(this[_message][key])) {
                let i = this[_message][key].length - 1;
                for (; i > 0; i--) {
                    this[_message][key][i] === fn && this[_message][key].splice(i, 1);
                }
            }
        }
    }

    return function () {
        return _instance = _instance || new Observer();
    }

})();

module.exports = Observer();
```

## 测试

```
'use strict';

const Obp = require('./design_pattern/observe');

/**
 * 需要传递的东西 要建立在构造函数内,在创建的时候就应该初始化了,要不this得值很难传过去的
 */
class Student{
    constructor (name){
        let that = this;
        this._name = name;
        this.say = function () {
            console.log(that._name + "正在回答");
        }
    }
    answer(question){
         Obp.regist(question,this.say);
    }
    sleep(question){
        console.log(this._name + "正在睡觉")
        Obp.remove(question,this.say);
    }
}

class Teacher{
    constructor(){
    }
    ask(question){
        Obp.fire(question);
    }
}

let one = new Student("学生1");
let one2 = new Student("学生2");
let one3 = new Student("学生3");

one.answer("丽君是不是傻瓜");
one2.answer("丽君是不是傻瓜");
one3.answer("丽君是不是傻瓜");

one3.sleep("丽君是不是傻瓜");

let two = new Teacher();

two.ask("丽君是不是傻瓜");
```
