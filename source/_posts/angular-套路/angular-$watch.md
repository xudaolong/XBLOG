$watch(watchFn, watchAction, deepWatch)

# 字符串或者表达式,方法,深watch(一般是数组或者对象)

# 监听 与 注销 

var dereg = $scope.$watch('someModel.someProperty', callbackOnChange());


dereg();
