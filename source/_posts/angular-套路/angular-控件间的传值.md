# 基于原型继承

# 父类的更改会触发所有的子类,子类的修改只会自身

```
<div ng-controller="Sandcrawler" ng-app>
    <p>Location: {{location}}</p>
    <button ng-click="move('Mos Eisley South')">Move</button>
    <div ng-controller="Droid">
        <p>Location: {{location}}</p>
        <button ng-click="sell('Owen Farm')">Sell</button>
    </div>
</div>
```


```
function Sandcrawler($scope) {
    $scope.location = "Mos Eisley North";
    $scope.move = function(newLocation) {
        $scope.location = newLocation;
    }
}
function Droid($scope) {
    $scope.sell = function(newLocation) {
        $scope.location = newLocation;
    }
}
```


# 基于事件的方式

# on 注册事件 并由 emit 触发

向上

```
<div ng-controller="Sandcrawler" ng-app>
    <p>Sandcrawler Location: {{location}}</p>
    <div ng-controller="Droid">
        <p>Droid Location: {{location}}</p>
        <button ng-click="summon()">Summon Sandcrawler</button>
    </div>
</div>
```


```
function Sandcrawler($scope) {
    $scope.location = "Mos Eisley North";
    $scope.$on('summon', function(e, newLocation) {
        $scope.location = newLocation;
    });
}
function Droid($scope) {
    $scope.location = "Owen Farm";
    $scope.summon = function() {
        $scope.$emit('summon', $scope.location);
    }
}
```

# 向下

```
function Sandcrawler($scope) {
    $scope.location = "Mos Eisley North";
    $scope.recall = function() {
        $scope.$broadcast('recall', $scope.location);
    }
}
function Droid($scope) {
    $scope.location = "Owen Farm";
    $scope.$on('recall', function(e, newLocation) {
        $scope.location = newLocation;
    });
}
```

```
//html
<div ng-controller="Sandcrawler">
    <p>Sandcrawler Location: {{location}}</p>
    <button ng-click="recall()">Recall Droids</button>
    <div ng-controller="Droid">
        <p>Droid Location: {{location}}</p>
    </div>
</div>
```

# 兄弟之间的传播

```
function Sandcrawler($scope) {
    $scope.$on('requestDroidRecall', function(e) {
        $scope.$broadcast('executeDroidRecall');
    });
}
function Droid($scope) {
    $scope.location = "Owen Farm";
    $scope.recallAllDroids = function() {
        $scope.$emit('requestDroidRecall');
    }
    $scope.$on('executeDroidRecall', function() { 
        $scope.location = "Sandcrawler"
    });
}
```

```
// html
<div ng-controller="Sandcrawler">
    <div ng-controller="Droid">
        <h2>R2-D2</h2>
        <p>Droid Location: {{location}}</p>
        <button ng-click="recallAddDroids()">Recall All Droids</button>
    </div>
    <div ng-controller="Droid">
        <h2>C-3PO</h2>
        <p>Droid Location: {{status}}</p>
        <button ng-click="recallAddDroids()">Recall All Droids</button>
    </div>
</div>
```
