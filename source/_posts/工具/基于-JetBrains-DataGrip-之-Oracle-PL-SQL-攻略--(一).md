---
title: 基于-JetBrains-DataGrip-之-Oracle-PL-SQL-攻略--(一)
date: 2016-09-11
categories: 
- 工具
---

> 在文集下的所有操作都是基于在 JetBrains DataGrip 上运行,图片的截图是快捷键的名字,请自行修改...

> 启动 DBMS_OUTPUT.PUT_LINE 功能 和 修改 dialog

![Ctrl + F8](http://upload-images.jianshu.io/upload_images/80378-001e159520fcd6e5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![先全选再右键修改](http://upload-images.jianshu.io/upload_images/80378-6855b70317c2b400.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 创建代码块

![generate](http://upload-images.jianshu.io/upload_images/80378-320686800e728cf3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 代码循环:从10倒数到0

```

SET SERVEROUTPUT ON;
DECLARE
  counter   NUMBER;
BEGIN
  FOR counter IN REVERSE 0..10 LOOP
    DBMS_OUTPUT.PUT_LINE (counter);
  END LOOP;
END;
/

```

> 命令行或者中断执行脚本

`` sqlplus username/password@database object.sql ``

> 接受用户键盘输入(替换变量),输出的是`` 一条 ``提示消息,若多条就需要循环遍历出来


![提示输入值并打印出来](http://upload-images.jianshu.io/upload_images/80378-b458c37f5028666c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


```

SET SERVEROUTPUT ON SIZE 1000000;
DECLARE
  id   NUMBER;
BEGIN
  SELECT SODTLID
  INTO id
  FROM AAAAAAA
  WHERE SOID = &SOID AND ROWNUM <= 1;
  DBMS_OUTPUT.PUT_LINE(id);
END;
/

原理剖析:
    关键是使用了 &符号 进行赋值,若想在其他的地方进行引用替换变量,则在键入 && 符号用来存储该值...
    也可以在DECLARE声明如下:

SET SERVEROUTPUT ON SIZE 1000000;
DECLARE
  souid_input NUMBER := &SOID;
  id   NUMBER;
BEGIN
  SELECT SODTLID
  INTO id
  FROM AAAAAAA
  WHERE SOID = souid_input AND ROWNUM <= 1;
  DBMS_OUTPUT.PUT_LINE(id);
END; 

    需要注意的是,如果声明的值的类型是变长字符型 VARCHAR2 ,则使用 单括号.
    obj VARCHAR(2) := '&String';

```

> 注释

```

-- 这句话是注释

/* 这是注释 */

```

> 引用代码块,好像不支持,提示出报错

``  <<dept_block>> ``  

> 忽略替换变量 

`` '\' `` 、还可以使用 `` SET DEFINE OFF `` ,另外 ``  SET ESCAPE  `` 设置转义字符

> 改变替换变量字符

`` SET DEFINE ^ `` 进行声明,之后就可以使用 `` ^ `` 代替 `` & ``

> 创建匹配数据库列类型的变量,在DECLAR声明,该优势在会随原型变化而变化....

`` id  AAAAAAA.SODTLID%TYPE; ``

> 使用正则过滤无用的数据库表

```

^.[^0-9]*?(?<!BACKUP)(?<!BK)(?<!LOG)(?<!TMP)(?<!BAK)(?<!TEMP)(?<!TEST)$

(SYS_HM).*

table:(SYS_HM).*|| table:(WK_).* || view:(HM_).* || view:(WK_).*

```

> 配置常用的JVM 内存 

```

-Xms720m -Xmx2048m

```
