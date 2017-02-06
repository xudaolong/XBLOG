---
title: js-pattern-简介与对象的收编
date: 2016-09-11
categories: 
- javascript
---

参考并结合es6类 是JavaScript 设计模式

```
-a : 架构型设计模式
-h : 行为型设计模式
-i : 创建型设计模式
-k : 技巧型设计模式
-s : 结构型设计模式
```

高内聚 : =内聚力,是软件度量,组成模块程度,即包含鲁棒性(健壮性),可靠度,可复用性和易懂性;

耦合性 : 与内聚性相对;

## 全局函数的处理

# 用对象收编

```
let obj = {
    one : ()=>{

    },
    two : ()=>{

    }
}
```

# 真假对象
```
let obj = ()=> {
    return {
        one: ()=> {
            console.log("one")
        },
        two: ()=> {
            console.log("two")
        }
    }
}
```

# 类的形式
```
class obj {
    constructor() {
    }

    one(){
        console.log("one");
        return this;
    }
    two(){
        console.log("two")
        return this;
    }
}
```

## 函数祖先绑定

```
Function.prototype.addMethod = function(name,func){
    this[name] = func;
    //类式调用方法
    //this.prototype[name] = fn ;
}
```

# 初始化 
```
let methons = function(){};
or let methons = new Function();
```

