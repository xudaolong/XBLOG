---
title: angular-模板内容渲染
date: 2016-09-11
categories: 
- angular
---


> 重复

```
$index 当前索引
$first 是否为头元素
$middle 是否为非头非尾元素
$last 是否为尾元素
```

例子一:
```
<div ng-controller="TestCtrl">
  <ul ng-repeat="member in obj_list">
    <li>{{ member }}</li>
  </ul>
</div>
```

```
angular.module('app', [], angular.noop)
.controller('TestCtrl', function($scope){
    $scope.obj_list = [1,2,3,4];
});
angular.bootstrap(document.documentElement, ['app']);
```

例子二:
```
<div ng-controller="TestCtrl">
  <ul ng-repeat="member in obj_list">
    <li>{{ $index }}, {{ member.name }}</li>
  </ul>
</div>
```

```
angular.module('app', [], angular.noop)
.controller('TestCtrl', function($scope){
    $scope.obj_list = [{name: 'A'}, {name: 'B'}, {name: 'C'}];
});
angular.bootstrap(document.documentElement, ['app']);
```

> 奇偶
ng-class-even 和 ng-class-odd 是和 ng-repeat 配合使用的：

```
<ul ng-init="l=[1,2,3,4]">
  <li ng-class-odd="'odd'" ng-class-even="'even'" ng-repeat="m in l">{{ m }}</li>
</ul>
```

> 赋值

```
<div ng-controller="TestCtrl" ng-init="a=[1,2,3,4];">
  <ul ng-repeat="member in a">
    <li>{{ member }}</li>
  </ul>
</div>
```

