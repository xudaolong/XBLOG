---
title: mongodb-初识
date: 2016-09-11
categories: 
- mongodb
---

> mongodb 基本命令

> show dbs or db
> 当前数据库

> use dbs 
> 切换指定数据库,若进行过操纵则自动创建该数据库 

> show collections
> 当前数据库的所有集合

> db.stats()
> 当前数据库的统计信息

> db.getCollectionNames()
> 当前数据库的集合名称列表

```
db.getCollection(       
db.getLogComponents(    
db.getQueryOptions(     
db.getSlaveOk(
db.getCollectionInfos(  
db.getMongo(            
db.getReplicationInfo(  
db.getUser(
db.getCollectionNames(  
db.getName(             
db.getRole(             
db.getUsers(
db.getLastError(        
db.getPrevError(        
db.getRoles(            
db.getWriteConcern(
db.getLastErrorCmd(     
db.getProfilingLevel(   
db.getSiblingDB(
db.getLastErrorObj(     
db.getProfilingStatus(  
db.getSisterDB(
```

> db.createCollection()
> 创建集合

> db.mycoll.drop()
> 删除集合

> db.storeCollection.save()
> 更新记录

> db.storeCollection.findOne()
> 查询一条记录

> db.storeColletion.find()
> 查询多条记录

> db.sotreColletion.remove()
> 删除记录

> db.dropDatabase()
> 删除当前的数据库,但上下文还是当前的


下面是其他删除的数据

```
db.dropAllRoles(  db.dropAllUsers(  db.dropDatabase(  db.dropRole(      db.dropUser(
```

> db.serverStatus()
> 当前服务器的状态,查看是否存在问题,便于修复

> mongodb 符号&查询

> 查询方式

```
$lt:< 
$lte:<= 
$gt:> 
$gte:>= 
$ne:!=
```

```
> db.student.find({age:{$lt:30}})
{ "_id" : 1, "name" : "zhangsan", "age" : 27, "sex" : 1 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
> db.student.find({age:{$ne:27}})
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
```


> $in:包含$nin:不包含

```
> db.student.find({age:{$in:[27,28]}})
{ "_id" : 1, "name" : "zhangsan", "age" : 27, "sex" : 1 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
> db.student.find({age:{$nin:[27,28]}})
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }

```

> $or:或者

```
> db.student.find({$or:[{age:{$lt:29}}, {name:"sunba"}]})
{ "_id" : 1, "name" : "zhangsan", "age" : 27, "sex" : 1 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
```

> null:空值

```
> db.student.find({sex: null})
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
```

> $type:键是某种类型的 
> double:1 
> string:2 
> ...

```

> db.student.insert({_id:7, name:7, age:70})
WriteResult({ "nInserted" : 1 })
> db.student.find({name: {$type: 2}})
{ "_id" : 1, "name" : "zhangsan", "age" : 27, "sex" : 1 }
{ "_id" : 2, "name" : "lisi", "age" : 27 }
{ "_id" : 3, "name" : "wangwu", "age" : 30 }
{ "_id" : 4, "name" : "zhaoliu", "age" : 28 }
{ "_id" : 5, "name" : "qianliu", "age" : 33 }
{ "_id" : 6, "name" : "sunba", "age" : 32 }
> db.student.find({name: {$type: 1}})
{ "_id" : 7, "name" : 7, "age" : 70 }
```

> 正则表达式

```
> db.student.find({name: /si\b/})
{ "_id" : 2, "name" : "lisi", "age" : 27 }
```

