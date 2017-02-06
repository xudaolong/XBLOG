---
title: mongodb-remove
date: 2016-09-11
categories: 
- mongodb
---

> db.集合名称.remove({query}, justOne)
> query：过滤条件，可选
> justOne：是否只删除查询到的第一条数据，值为true或者1时，只删除一条数据，默认为false，可选。

> 删除第一条

```
> db.student.remove({age:28}, true)
WriteResult({ "nRemoved" : 1 })
> db.student.find()
{ "_id" : 2, "name" : "lisi", "age" : 28 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "mongodb", "java" ] }
```

> 删除所有的数据

```
> db.student.remove({age:28})
WriteResult({ "nRemoved" : 2 })
> db.student.find()
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "mongodb", "java" ] }
```

> 删除集合所有{}

```
> db.student.remove({})
WriteResult({ "nRemoved" : 4 })
```






