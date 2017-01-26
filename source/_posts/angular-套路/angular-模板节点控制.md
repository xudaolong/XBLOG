## 样式
```
<div ng-style="{width: 100 + 'px', height: 100 + 'px', backgroundColor: 'red'}">
</div>
```

## 类

```
<div ng-controller="TestCtrl" ng-class="cls">
</div>
```

## 显示和隐藏
```ng-show ng-hide ng-switch```

前两个是控制 display 的指令：

```
<div ng-show="true">1</div>
<div ng-show="false">2</div>
<div ng-hide="true">3</div>
<div ng-hide="false">4</div>
```

后一个 ng-switch 是根据一个值来决定哪个节点显示，其它节点移除：

```
<div ng-init="a=2">
  <ul ng-switch on="a">
    <li ng-switch-when="1">1</li>
    <li ng-switch-when="2">2</li>
    <li ng-switch-default>other</li>
  </ul>
</div>
```

# 其他属性 

ng-src 控制 src 属性：

```
<img ng-src="{{ 'h' + 'ead.png' }}" />
```

ng-href 控制 href 属性：

```
<a ng-href="{{ '#' + '123' }}">here</a>
```

ng-src src属性
ng-href href属性
ng-checked 选中状态
ng-selected 被选择状态
ng-disabled 禁用状态
ng-multiple 多选状态
ng-readonly 只读状态

