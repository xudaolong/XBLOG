---
title: angular-隔离指令的作用域
date: 2016-09-11
categories: 
- angular
---


> 避免重复使用controller

> solate scope 

```
var app = angular.module('myApp', []);

app.controller('Ctrl', function($scope) {
    $scope.naomi = {
      name: 'Naomi',
      address: '1600 Amphitheatre'
    };
    $scope.igor = {
      name: 'Igor',
      address: '123 Somewhere'
    };
  })
  .directive('myCustomer', function() {
    return {
      restrict: 'E',
      scope: {
        customer: '=customer'
      },
      template: 'Name: {{customer.name}} Address: {{customer.address}}'
    };
  });



<body ng-app="myApp">
  <div ng-controller="Ctrl">
    <my-customer customer="naomi"></my-customer>
    <hr>
    <my-customer customer="igor"></my-customer>
  </div>
</body>
```

关键在于:

```
scope: {
  customer: '=customer'
},
```

简化:

```
scope: {
  // same as '=customer'
  customer: '='
},
```
