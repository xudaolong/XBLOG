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
