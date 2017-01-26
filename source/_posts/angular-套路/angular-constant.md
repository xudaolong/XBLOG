# 归属module 代表常量

```
var app = angular.module('myapp', []).value('testvalue', 'widuu').constant('count', 23).service('testservice',
function(testvalue, count) {
    this.lable = function() {
        return "this will output:hello " + testvalue + ",age is " + count;
    }
});
app.controller('mytest',
function($scope, testvalue, testservice) {
    $scope.test = "hello " + testvalue;
    $scope.output = testservice.lable();
});

```
