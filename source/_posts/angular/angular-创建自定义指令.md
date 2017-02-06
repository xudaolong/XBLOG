---
title: angular-创建自定义指令
date: 2016-09-11
categories: 
- angular
---


> 检测是否内嵌表达式=>watches,在digest循环中更新
$interpolate
<a ng-href="img/{{username}}.jpg">Hello {{username}}!</a>

> 优先返回对象而不是函数

> 优先保留你自己的指令作为前缀

> 模板扩展的指令:但是标签名是无效的

对应的html:
```
<div my-customer></div>

.directive('myCustomer', function() {
    return {
      template: 'Name: {{customer.name}} Address: {{customer.address}}'
    };
 });
 ```

若是大量的模板的:
```
<div my-customer></div>

.directive('myCustomer', function() {
    return {
      restrict: 'E',
      templateUrl: 'my-customer.html'
    };
 });
 ```

// my-customer.html
Name: {{customer.name}} Address: {{customer.address}}
