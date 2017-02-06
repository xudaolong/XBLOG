---
title: js-pattern--h-模板方法模式
date: 2016-09-11
categories: 
- javascript
---

``基于复用技术``、``抽象类-->继承抽象类``

## 创建抽象类

```
var CaffeineBeverage = function () {

};
CaffeineBeverage.prototype.prepareRecipe = function () {
    this.boilWater();
    this.brew();
    this.pourOnCup();
    if (this.customerWantsCondiments()) {
        // 如果可以想加小料，就加上
 this.addCondiments();
    }
};
CaffeineBeverage.prototype.boilWater = function () {
    console.log("将水烧开!");
};
CaffeineBeverage.prototype.pourOnCup = function () {
    console.log("将饮料到再杯子里!");
};
CaffeineBeverage.prototype.brew = function () {
    throw new Error("该方法必须重写!");
};
CaffeineBeverage.prototype.addCondiments = function () {
    throw new Error("该方法必须重写!");
};
// 默认加上小料
CaffeineBeverage.prototype.customerWantsCondiments = function () {
    return true;
};
```

## 实现抽象类

```
// 冲咖啡
var Coffee = function () {
    CaffeineBeverage.apply(this);
};
Coffee.prototype = new CaffeineBeverage();
Coffee.prototype.brew = function () {
    console.log("从咖啡机想咖啡倒进去!");
};
Coffee.prototype.addCondiments = function () {
    console.log("添加糖和牛奶");
};
Coffee.prototype.customerWantsCondiments = function () {
    return confirm("你想添加糖和牛奶吗？");
};

//冲茶叶
var Tea = function () {
    CaffeineBeverage.apply(this);
};
Tea.prototype = new CaffeineBeverage();
Tea.prototype.brew = function () {
    console.log("泡茶叶!");
};
Tea.prototype.addCondiments = function () {
    console.log("添加柠檬!");
};
Tea.prototype.customerWantsCondiments = function () {
    return confirm("你想添加柠檬嘛？");
};

```
