---
title: angular-获取列表中的值
date: 2016-09-11
categories: 
- angular
---


```
<li ng-repeat="tag in tags">
        <span ng-click="onSelect(tag)">{{tag.name}}</span>
</li>



        $scope.onSelect=function(tag){
            $scope.selectedTag=tag.name;//将单击的值赋给$scope.selectedTag
            console.log(tag.name);
            console.log($scope.selectedTag)
        }
```
