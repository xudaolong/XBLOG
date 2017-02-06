---
title: 基于-JetBrains-DataGrip-之-Oracle-PL-SQL-攻略--(二)
date: 2016-09-11
categories: 
- 工具
---

> 对异常的检测

```

  EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('无相关匹配的信息');
  WHEN TOO_MANY_ROWS THEN
    DBMS_OUTPUT.PUT_LINE('实际返回的行数超出请求的行数');

```

> 使用游标从数据库中检索单行数据,进行两个的FETCH,进而判断结果

```

DECLARE

  --创建一个游标
  CURSOR emp_cursor IS
  SELECT first_name, last_name, email
  FROM employees
  WHERE employee_id = &emp_id;

  first   	VARCHAR2(20);
  last  	VARCHAR2(25);
  email 	VARCHAR2(25);

BEGIN
  --打开游标
  OPEN emp_cursor;
  FETCH emp_cursor INTO first, last, email;
  IF emp_cursor%NOTFOUND THEN
    RAISE NO_DATA_FOUND;
  ELSE
      -- 第二次查找,判断异常
    FETCH emp_cursor INTO first, last, email;
    IF emp_cursor%FOUND THEN
      -- 抛出异常
      RAISE TOO_MANY_ROWS;
    ELSE
      DBMS_OUTPUT.PUT_LINE(
     'Employee Information for ID: ' || first || ' ' || last || ' - ' || email);
    END IF;
  END IF;
  --关闭游标
  CLOSE emp_cursor;

     
EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No employee matches the given ID');
 WHEN TOO_MANY_ROWS THEN
    DBMS_OUTPUT.PUT_LINE('More than one employee matches the given ID');
END;
/

```

> 限定列名与变量名-->尽量不一样否者用 圆点标记法利用存储过程限定变量名,也可以使用代码块进行限定...

> 查询结果返回到PL/SQL 记录中

```

DECLARE
  CURSOR wms_goods_cur IS
    SELECT
      GOODSID,
      GOODSNAME,
      GOODSINVNAME
    FROM WMS_GOODS
    WHERE GOODSID = 1000020598;

  --记录表的行结构
  wms_good wms_goods_cur%ROWTYPE;
BEGIN
  OPEN wms_goods_cur;
  FETCH wms_goods_cur INTO wms_good;
  IF wms_goods_cur%FOUND
  THEN
    CLOSE wms_goods_cur;
    DBMS_OUTPUT.PUT_LINE('药品的id:'|| wms_good.GOODSID || ' 药品的名称: ' || wms_good.GOODSNAME ||
                         ' 药品的别称: ' || wms_good.GOODSINVNAME);
  ELSE
    DBMS_OUTPUT.PUT_LINE('没有匹配到的药品');
  END IF;
  EXCEPTION
  WHEN NO_DATA_FOUND THEN
  DBMS_OUTPUT.PUT_LINE('无匹配的系你');
END;
/

```

> 关于自定义数据结构来接收查询结果

```

DECLARE
  -- 声明数据结构
  TYPE wms_goods_info IS RECORD (id WMS_GOODS.GOODSID%TYPE,
    name WMS_GOODS.GOODSNAME%TYPE,
    invname WMS_GOODS.GOODSINVNAME%TYPE);

  -- 使用数据接口的变量
  wms_good_rec wms_goods_info;
BEGIN
  -- 填充变量
  SELECT
    GOODSID,
    GOODSNAME,
    GOODSINVNAME
  INTO wms_good_rec
  FROM WMS_GOODS
  WHERE GOODSID = 1000005274;
  
  -- 输出
  DBMS_OUTPUT.PUT_LINE('药品的id:' || wms_good_rec.id || ' 药品的名称: ' || wms_good_rec.name ||
                       ' 药品的别称: ' || wms_good_rec.invname);
  EXCEPTION
  WHEN NO_DATA_FOUND THEN
  DBMS_OUTPUT.PUT_LINE('无匹配信息');

END;
/

```

> 循环遍历查询的行结果

```

--方案一:直接在 IN 后接一个查询语句
SET SERVEROUTPUT ON;
BEGIN
  DBMS_OUTPUT.ENABLE(1000000);
  FOR wms_goods IN
  (
  SELECT
    GOODSID,
    GOODSNAME,
    GOODSINVNAME
  FROM WMS_GOODS
  WHERE GOODSID IS NOT NULL
  )
  LOOP
    DBMS_OUTPUT.PUT_LINE(wms_goods.GOODSID || ' ' || wms_goods.GOODSNAME || ' - ' || wms_goods.GOODSINVNAME);
  END LOOP;
END;
/

--方案二:构建CURSOR,然后在IN后遍历该游标
SET SERVEROUTPUT ON;
DECLARE
  CURSOR wms_goods IS
    SELECT
      GOODSID,
      GOODSNAME,
      GOODSINVNAME
    FROM WMS_GOODS
    WHERE GOODSID IS NOT NULL;

  emp_rec wms_goods%ROWTYPE;
BEGIN
  FOR emp_rec IN wms_goods LOOP
    DBMS_OUTPUT.PUT_LINE(emp_rec.GOODSID || ' ' || emp_rec.GOODSNAME || ' - ' || emp_rec.GOODSINVNAME);
  END LOOP;
END;
/
```

> 获取环境与会话的信息

```

DECLARE
  username   VARCHAR2(100);
  ip_address VARCHAR2(100);
BEGIN
  SELECT
    -- 可自定义设置命名空间 另外 USERENV 的参数列表可参考  
    -- https://docs.oracle.com/cd/B19306_01/server.102/b14200/functions165.htm
    SYS_CONTEXT('USERENV', 'SESSION_USER'),
    SYS_CONTEXT('USERENV', 'IP_ADDRESS')
  INTO username, ip_address
  FROM DUAL;

  DBMS_OUTPUT.PUT_LINE('The connected user is: ' || username || ', and the IP address is ' ||
                       ip_address);
END obtain_user_info;
/



```
