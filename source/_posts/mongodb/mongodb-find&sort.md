---
title: mongodb-find&sort
date: 2016-09-11
categories: 
- mongodb
---

> 查询指定的键

db.集合名称.find({查询条件},{指定键}) 
指定键：1表示显示，0表示不显示，_id默认显示

```
> db.student.find({},{name:1})
{ "_id" : 1, "name" : "zhangsan" }
{ "_id" : 2, "name" : "lisi" }
{ "_id" : 3, "name" : "wangwu" }
{ "_id" : 4, "name" : "zhaoliu" }
{ "_id" : 5, "name" : "qianliu" }
{ "_id" : 6, "name" : "sunba" }
> db.student.find({},{_id:0, age:0})
{ "name" : "zhangsan", "sex" : 1 }
{ "name" : "lisi" }
{ "name" : "wangwu" }
{ "name" : "zhaoliu" }
{ "name" : "qianliu" }
{ "name" : "sunba" }
> db.student.find({},{_id:0, name:1})
{ "name" : "zhangsan" }
{ "name" : "lisi" }
{ "name" : "wangwu" }
{ "name" : "zhaoliu" }
{ "name" : "qianliu" }
{ "name" : "sunba" }
```

> db.集合名称.findOne({查询条件},{指定键}) 

查询出符合条件的第一条数据

```
> db.student.findOne()
{ "_id" : 1, "name" : "zhangsan", "age" : 27, "sex" : 1 }
db.集合名称.find({查询条件},{指定键}).limit(数字)查询前几条数据

> db.student.find().limit(3)
{ "_id" : 1, "name" : "zhangsan", "age" : 27, "sex" : 1 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
db.集合名称.find({查询条件},{指定键}).skip(数字)跳过前几条数据

> db.student.find().skip(2)
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : 7, "age" : 70 }

```

>可以使用limit()和skip()实现分页

```
> db.student.find().skip(0).limit(3)
{ "_id" : 1, "name" : "zhangsan", "age" : 27, "sex" : 1 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
> db.student.find().skip(3).limit(3)
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
> db.student.find().skip(6).limit(3)
{ "_id" : 7, "name" : 7, "age" : 70 }
```


> db.集合名称.find().sort({键:数字})数字为1表示升序，数字为2表示降序

> db.student.find().sort({age:1})

```

{ "_id" : 1, "name" : "zhangsan", "age" : 27, "sex" : 1 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 7, "name" : 7, "age" : 70 }
```

> db.student.find().sort({age:1, _id:-1})

```
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 1, "name" : "zhangsan", "age" : 27, "sex" : 1 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 7, "name" : 7, "age" : 70 }
```









