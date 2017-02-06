---
title: mongodb-insert&save
date: 2016-09-11
categories: 
- mongodb
---

> 拥有两种方法
> 一旦数据中包含_id,insert不插入相同的值,save则更新数据

```
> db.student.insert({"_id": 1, "name":"zhangsan", "age": 28})
WriteResult({ "nInserted" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 28 }
> db.student.insert({"_id": 1, "name":"zhangsan", "age": 27})
WriteResult({
        "nInserted" : 0,
        "writeError" : {
                "code" : 11000,
                "errmsg" : "E11000 duplicate key error collection: zyhdb.student index: _id_ dup key: { : 1.0 }"
        }
})
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 28 }
> db.student.save({"_id": 1, "name":"zhangsan", "age": 27})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 27 }
```

> 批量插入

```
> db.student.insert([{"_id": 2, "name": "lisi"},{"_id": 3, "name": "wangwu"}, {"_id": 4, "name": "zhaoliu", "age": 28}])
BulkWriteResult({
"writeErrors" : [ ],
"writeConcernErrors" : [ ],
"nInserted" : 3,
"nUpserted" : 0,
"nMatched" : 0,
"nModified" : 0,
"nRemoved" : 0,
"upserted" : [ ]
})
> db.student.find()
{ "_id" : 1, "name" : "zhangsan", "age" : 27 }
{ "_id" : 2, "name" : "lisi" }
{ "_id" : 3, "name" : "wangwu" }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
```

> 循环插入

```
> for(var i=0; i<10; i++){db.fortest.insert({num: i})}
WriteResult({ "nInserted" : 1 })
> db.fortest.find()
{ "_id" : ObjectId("57469e80142cea1d9aeabab5"), "num" : 0 }
{ "_id" : ObjectId("57469e80142cea1d9aeabab6"), "num" : 1 }
{ "_id" : ObjectId("57469e80142cea1d9aeabab7"), "num" : 2 }
{ "_id" : ObjectId("57469e80142cea1d9aeabab8"), "num" : 3 }
{ "_id" : ObjectId("57469e80142cea1d9aeabab9"), "num" : 4 }
{ "_id" : ObjectId("57469e80142cea1d9aeababa"), "num" : 5 }
{ "_id" : ObjectId("57469e80142cea1d9aeababb"), "num" : 6 }
{ "_id" : ObjectId("57469e80142cea1d9aeababc"), "num" : 7 }
{ "_id" : ObjectId("57469e80142cea1d9aeababd"), "num" : 8 }
{ "_id" : ObjectId("57469e80142cea1d9aeababe"), "num" : 9 }
```
