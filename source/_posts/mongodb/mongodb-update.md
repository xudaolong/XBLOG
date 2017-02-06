---
title: mongodb-update
date: 2016-09-11
categories: 
- mongodb
---

> db.集合名称.update({query},{update},upsert, multi}) 
> 过滤条件;
> 修改内容;
> 是否插入数据(若不存在),默认false;
> 是否只查询条件的第一条,默认false;

```
> db.student.update({_id:1}, {name:"zhang"})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhang" }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
```


> 更新/添加指定条件的某键;
> $set

```
> db.student.update({_id: 1},{$set:{name:"zhangsan", age: 26}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
```

> 删除指定条件的某键
> $unset

```
> db.student.update({_id:7},{$unset:{age:1}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu" }
```

> 在原来的基础上的运算
> $inc

```
> db.student.update({_id:7}, {$inc:{age:-1}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "age" : 31 }

```

# 数组

>$push:当数据中不存在键时，创建数组类型的键并插入该值;如果存在该键，并且该键是数组类型时，则在此数>组类型的数据上追加;如果存在该键，并且该键不是数组类型时，会报错。
>$pushAll:批量往数组中追加
>$addToSet:数组中有该值时不追加，没有该值时追加

```

> db.student.update({_id: 7},{$push:{skill:"java"}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "java" ] }
> db.student.update({_id: 7},{$push:{skill:"mongodb"}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "java", "mongodb" ] }
> db.student.update({_id: 7},{$push:{name:"111"}})
WriteResult({
"nMatched" : 0,
"nUpserted" : 0,
"nModified" : 0,
"writeError" : {
"code" : 16837,
"errmsg" : "The field 'name' must be an array but is of type String in document {_id: 7.0}"
}
})
> db.student.update({_id: 7},{$pushAll:{skill:["js","C++","java"]}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "java", "mongodb", "js", "C++", "java" ] }
> db.student.update({_id:7},{$addToSet:{skill:"mongodb"}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 0 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "java", "mongodb", "js", "C++", "java" ] }

```

> $pop:删除数组的第一个或最后一个元素，值为-1时是删除第一个元素，值为1时是删除最后一个元素。
> $pull:删除数组中的某一个指定的数值
> $pullAll:删除数组中多个指定的数值

```
> db.student.update({_id:7},{$pop:{skill:1}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "java", "mongodb", "js", "C++" ] }
> db.student.update({_id:7},{$pop:{skill:-1}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "mongodb", "js", "C++" ] }
> db.student.update({_id:7},{$pull:{skill:"js"}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "mongodb", "C++" ] }
> db.student.update({_id:7},{$pullAll:{skill:["js"]}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 0 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ "mongodb", "C++" ] }
> db.student.update({_id:7},{$pullAll:{skill:["mongodb","C++"]}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
{ "_id" : 7, "name" : "songjiu", "skill" : [ ] }

```

> id不能转换

```

> db.student.update({_id:1},{_id:0, name:"zhangsanzhangsan"})
WriteResult({
"nMatched" : 0,
"nUpserted" : 0,
"nModified" : 0,
"writeError" : {
"code" : 16837,
"errmsg" : "The _id field cannot be changed from {_id: 1.0} to {_id: 0.0}."
}
})
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 26 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
```














