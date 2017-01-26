# 模板内容、方式

在需要的地方直接写字符串

外部文件

```
<div ng-include src="'tpl.html'">
</div>

<div ng-include="'tpl.html'">
</div>
```

使用 script 标签定义的“内部文件”

```
<script type="text/ng-template" id="tpl">
here, {{ 1 + 1 }}
</script>

<div ng-include src="'tpl'"></div>
```

配合变量使用
```
<script type="text/ng-template" id="tpl">
here, {{ 1 + 1 }}
</script>

<a ng-click="v='tpl'">Load</a>
<div ng-include src="v"></div>
```
