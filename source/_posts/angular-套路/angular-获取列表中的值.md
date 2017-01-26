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
