# 是module的方法
# factory(name, providerFunction);
# 存储方法


```
<body ng-app='myapp' ng-controller='mytest'>
  <input ng-model='test'>{{test}}
  <br>{{output}}</body>

```


```
var app = angular.module('myapp', []).value('testvalue', 'widuu').factory('testfactory',
function(testvalue) {
    return {
        lable: function() {
            return "this can output : hello " + testvalue;
        }
    }
});
app.controller('mytest',
function($scope, testvalue, testfactory) {
    $scope.test = "hello " + testvalue;
    $scope.output = testfactory.lable();
});

```
