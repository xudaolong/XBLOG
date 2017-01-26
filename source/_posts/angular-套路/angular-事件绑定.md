```
ng-change
ng-click
ng-dblclick
ng-mousedown
ng-mouseenter
ng-mouseleave
ng-mousemove
ng-mouseover
ng-mouseup
ng-submit
```

对于事件对象本身，在函数调用时可以直接使用 $event 进行传递：
```
<p ng-click="click($event)">点击</p>
<p ng-click="click($event.target)">点击</p>
```
