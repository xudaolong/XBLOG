---
title: angular-表单输入
date: 2016-09-11
categories: 
- angular
---


> input 的监听事件 ng-change

<form ng-controller="StartUpController">
     Starting : <input ng-change="computeNeeded()" ng-model="funding.startingEstimate">
     Recommendation: {{funding.needed}}
</form>


```
function StartUpController($scope) {
        $scope.funding = { startingEstimate : 0};

        $scope.computeNeeded = function () {
            $scope.funding.needed = $scope.funding.startingEstimate * 10;
        }
    }

```


> 检测数据是否变化

```
$scope.$watch('funding.startingEstimate', computeNeeded);
```
