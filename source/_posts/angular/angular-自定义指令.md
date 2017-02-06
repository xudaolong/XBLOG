---
title: angular-自定义指令
date: 2016-09-11
categories: 
- angular
---


> 指令使用如下,由restrict控制
 
```
E 元素方式 <my-directive></my-directive>
A 属性方式 <div my-directive="exp"> </div>
C 类方式 <div class="my-directive: exp;"></div>
M 注释方式 <!-- directive: my-directive exp -->
```

> 指令执行过程: 解析DOM结构-->$compile-->执行link函数

$compile 涉及: 变量占位符-指令-compile函数

> 指令的构造应该返回对象,若是函数则是作为compile的返回值

```
name:controller的名字
priority:权重,决定兄弟节点的执行compile的顺序
terminal:若为true,则权重小于但不等于的该节点的节点不会被执行.
scope:false 节点的 scope ， true 继承创建一个新的 scope ， {} 不继承创建一个新的隔离 scope 。 {@attr: '引用节点属性', =attr: '把节点属性值引用成scope属性值', &attr: '把节点属性值包装成函数'}
controller:为指令自定义一个controller,function controller($scope, $element, $attrs, $transclude) { ... }
require:?name 忽略不存在的错误， ^name 在父级查找
restrict
template:模板内容
templateUrl:模板地址
replace:true 替换整个节点， false 替换节点内容
transclude:'element' 或 true 两种值 
compile
link
```

> 关于动态渲染修改变量

```
app.directive('color', function(){
  var link = function($scope, $element, $attrs){
    $scope.$watch($attrs.color, function(new_v){
      $element.css('color', new_v);
    });
  }
  return link;
});
```

> attributes对象

```
$element 属性所在的节点。
$attr 所有的属性值（类型是对象）。
$normalize 一个名字标准化的工具函数，可以把 ng-click 变成 ngClick 。
$observe 为属性注册侦听器的函数。
$set 设置对象属性，及节点属性的工具。
```


