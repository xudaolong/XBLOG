---
title: jade-在express下调用
date: 2016-09-11
categories: 
- express
---

# 在express 下调用

```
app.set('view engine', 'jade'); // 设置模板引擎
app.set('views', __dirname);  // 设置模板相对路径(相对当前目录)

app.get('/', function(req, res) {
    res.render('test'); // 调用当前路径下的 test.jade 模板
})

```
