```
<!doctype html>
<html lang="zh" ng-app>
<head>
    <meta charset="UTF-8">
    <title>demo</title>
</head>
<body>
Your name: <input type="text" ng-model="yourname" placeholder="World">
<hr>
Hello {{yourname || 'xudaolong'}}!
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
</body>
</html>
```
