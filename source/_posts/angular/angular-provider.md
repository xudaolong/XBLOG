---
title: angular-provider
date: 2016-09-11
categories: 
- angular
---


> 归属module (name, providerType)
> 类似 factory
> 用于提供一个方法

```

var app = angular.module('myapp', []).value('testvalue', 'widuu').provider('testprovider',
function() {
    this.lable = "this will output : hello widuu";
    this.$get = function() {
        return this;
    }
});
app.controller('mytest',
function($scope, testvalue, testprovider) {
    $scope.test = "hello " + testvalue;
    $scope.output = testprovider.lable;
});

```
