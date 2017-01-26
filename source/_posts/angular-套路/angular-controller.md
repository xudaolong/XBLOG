# 是module的方法
# controller(name, constructor); 
# 前者是名字,后者是构造函数
# 不同的controller中变量相同引用不同


```
<body style="padding:10px;" ng-app="app">
<div ng-controller="FirstCtrl">
<input type="text"ng-model="msg">
<h1>{{msg}}</h1>
<br>
<h1 ng-bind="msg"></h1>
<!--可以使用ng-bind进行绑定，这样就不需要输入{{}}-->
</div>
<div ng-controller="SecondCtrl">
<input type="text" ng-model="msg">
<h1>{{msg}}</h1>
<!--同样是msg，但是显示的不同这就是控制器作用域的问题，这个msg绑定的是SecondCtrl-->
</div>
</body> 
```


```
angular.module('app',[])
.controller('FirstCtrl',function($scope){
    $scope.msg="hello angular";
})
.controller('SecondCtrl',function($scope){
    $scope.msg="hello angularjs"
})
```


# 比较正式的控制器
```
angular.module('myApp', []).controller('userCtrl', function($scope) {
$scope.fName = '';
$scope.lName = '';
$scope.passw1 = '';
$scope.passw2 = '';
$scope.users = [
{id:1, fName:'Hege',lName:"Pege" },
{id:2, fName:'Kim',lName:"Pim" },
{id:3, fName:'Sal',lName:"Smith" },
{id:4, fName:'Jack',lName:"Jones" },
{id:5, fName:'John',lName:"Doe" },
{id:6, fName:'Peter',lName:"Pan" }
];
$scope.edit = true;
$scope.error = false;
$scope.incomplete = false; 
$scope.editUser = function(id) {
  if (id == 'new') {
    $scope.edit = true;
    $scope.incomplete = true;
    $scope.fName = '';
    $scope.lName = '';
    } else {
    $scope.edit = false;
    $scope.fName = $scope.users[id-1].fName;
    $scope.lName = $scope.users[id-1].lName; 
  }
};

$scope.$watch('passw1',function() {$scope.test();});
$scope.$watch('passw2',function() {$scope.test();});
$scope.$watch('fName',function() {$scope.test();});
$scope.$watch('lName',function() {$scope.test();});

$scope.test = function() {
  if ($scope.passw1 !== $scope.passw2) {
    $scope.error = true;
    } else {
    $scope.error = false;
  }
  $scope.incomplete = false;
  if ($scope.edit && (!$scope.fName.length ||
    !$scope.lName.length ||
    !$scope.passw1.length || !$scope.passw2.length)) {
    $scope.incomplete = true;
  }
};
})

```
