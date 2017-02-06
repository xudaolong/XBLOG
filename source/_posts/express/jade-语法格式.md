---
title: jade-语法格式
date: 2016-09-11
categories: 
- express
---

# 相同

```
p
  | foo bar baz
  | rawr rawr
``` 

```
p.
  foo bar baz
  rawr rawr
``` 
 
# 变量

```
#{表达式} -->任何地方
=表达式 -->值
!=表达式

- var s = 'hello world' // 在服务端空间中定义变量
p #{s}
p= s
```

# 404页面
```
                var error = #{error}

                if (error)
                    p  #{error}
                else
                    h1 你想干嘛       -- 404 页面.
                    
```
                    error = Error: Not Found
                    Error: Not Found


                    
                    
