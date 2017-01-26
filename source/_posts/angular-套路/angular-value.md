# 是module的方法
# 类似键值对的感觉
# 存储值


```
<body ng-app='myapp' ng-controller='mytest'>
  <input ng-model='test'>{{test}}</body>

```


```
var app = angular.module('myapp', []).value('testvalue', 'word');
app.controller('mytest',
function($scope, testvalue) {
    $scope.test = "hello " + testvalue;
});

```
