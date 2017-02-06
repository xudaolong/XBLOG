---
title: angular-$scope变量和方法
date: 2016-09-11
categories: 
- angular
---

> 变量和方法的使用
> $scope 类似是一个代理的对象,负责增删改和检验等功能


> ng-click="login()"

> $scope 生成
    $scope.user = {
        name: '',
        pwd: ''
    };
    
> $scope 引用 
<input type="text" ng-model="user.name"><br><br>
<input type="text" ng-model="user.pwd"><br><br>



```
<body style="padding:10px;" ng-app="app">
<div ng-controller="MyCtrl">
<input type="text"ng-model="msg">
<h1>{{msg}}</h1>
<br>
<h1>{{reverse()}}</h1>
<!--调用方法，注意这里要加括号-->
</div>
<div ng-controller="MyCtrl">
<input type="text" ng-model="user.name"><br><br>
<input type="text" ng-model="user.pwd"><br><br>
<div ng-click="login()">登录</div>
<div ng-show="errormsg.length>0">{{errormsg}}</div>
<!--当errormsg长度大于0的时候显示出来-->
</div>
</body>
```

```
angular.module('app', []).controller('MyCtrl',
function($scope) {
    $scope.msg = "";
    $scope.reverse = function() {
        return $scope.msg.split("").reverse().join(""); < !--对输入进行反转-->
    }

    $scope.user = {
        name: '',
        pwd: ''
    };
    $scope.errormsg = ""; < !--需要先定义，否则会报错-->$scope.login = function() {
        if ($scope.user.name == "admin" && $scope.user.pwd == "123") {
            alert("登录成功");
        } else {
            alert("用户名或密码错误");
        }
    }

})
```
