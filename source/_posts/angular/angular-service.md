---
title: angular-service
date: 2016-09-11
categories: 
- angular
---


> 归属module (name, constructor)
> 提供一个服务
> 与factory 相似

```
var app = angular.module('myapp', []).value('testvalue', 'widuu').service('testservice',
function(testvalue) {
    this.lable = function() {
        return "this will output:hello " + testvalue;
    }
});
app.controller('mytest',
function($scope, testvalue, testservice) {
    $scope.test = "hello " + testvalue;
    $scope.output = testservice.lable();
});

```
