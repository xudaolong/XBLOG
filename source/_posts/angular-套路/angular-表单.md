# 必须 name 和 ng-controller 
# 另外模板中的name便是$scope的层叠组件

例子一:

```
<form name="test_form" ng-controller="TestCtrl">
  <input type="text" name="a" required ng-model="a"  />
  <span ng-click="see()">{{ test_form.$valid }}</span>
</form>


angular.module('app', [], angular.noop)
.controller('TestCtrl', function($scope){
  $scope.see = function(){
    console.log($scope.test_form);
    console.log($scope.test_form.a);
  }
});
```

form 这个标签本身有一些动态类可以使用：

```
ng-valid 当表单验证通过时的设置
ng-invalid 当表单验证失败时的设置
ng-pristine 表单的未被动之前拥有
ng-dirty 表单被动过之后拥有
```

form 对象的属性有：

```
$pristine 表单是否未被动过
$dirty 表单是否被动过
$valid 表单是否验证通过
$invalid 表单是否验证失败
$error 表单的验证错误
```

```
<form name="test_form" ng-controller="TestCtrl">
  <input type="text" name="a" required ng-model="a"  />
  <input type="text" name="b" required ng-model="b" ng-minlength="2" />
  <span ng-click="see()">{{ test_form.$error }}</span>
</form>


angular.module('app', [], angular.noop)
.controller('TestCtrl', function($scope){
  $scope.see = function(){
    console.log($scope.test_form.$error);
  }
});
```

input 控件的相关可用属性为：

```
name 名字
ng-model 绑定的数据
required 是否必填
ng-required 是否必填
ng-minlength 最小长度
ng-maxlength 最大长度
ng-pattern 匹配模式
ng-change 值变化时的回调
```

select 

```
<form name="test_form" ng-controller="TestCtrl">
  <input type="checkbox" name="a" ng-model="a" ng-true-value="AA" ng-false-value="BB" />
  <span>{{ a }}</span>
</form>

var TestCtrl = function($scope){
  $scope.a = 'AA';
}
```

radio

```
<form name="test_form" ng-controller="TestCtrl">
  <input type="radio" name="a" ng-model="a" value="AA" />
  <input type="radio" name="a" ng-model="a" value="BB" />
  <span>{{ a }}</span>
</form>
```
