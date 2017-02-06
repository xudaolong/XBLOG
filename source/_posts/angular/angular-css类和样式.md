---
title: angular-css类和样式
date: 2016-09-11
categories: 
- angular
---


```
<div ng-controller="MenuController">
    <ul>
        <li class="menu-disabled-{{isDisabled}}" ng-click="DisabledIt()">Click</li>
        ...
    </ul>
</div>
```

```
.menu-disabled-true {
    color: gray;
}
```
```
function MenuController($scope) {
    $scope.isDisabled = false;

    $scope.disabledIt = function() {
        $scope.isDisabled = true;
    }
}
```
