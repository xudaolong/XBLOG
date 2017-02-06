---
title: js-json-转换
date: 2016-09-11
categories: 
- javascript
---

> json-->string
```
static stringToJson(data){
    return JSON.parse(data);
}
```

> string-->json
```
static jsonToString(data){
    return JSON.stringify(data);
}
```

> map-->json
```
/**
 *map转化为对象（map所有键都是字符串，可以将其转换为对象）
 */
 static strMapToObj(strMap){
    let obj= Object.create(null);
    for (let[k,v] of strMap) {
      obj[k] = v;
    }
    return obj;
  }
  /**
  *map转换为json
  */
  static mapToJson(map) {
  return JSON.stringify(JsonUitl.strMapToObj(map));
  }
  ```

> json-->map
```
/**
 *map转化为对象（map所有键都是字符串，可以将其转换为对象）
 */
 static strMapToObj(strMap){
    let obj= Object.create(null);
    for (let[k,v] of strMap) {
      obj[k] = v;
    }
    return obj;
  }
  /**
  *map转换为json
  */
  static mapToJson(map) {
  return JSON.stringify(JsonUitl.strMapToObj(map));
  }
  ```

> map-->array
```
let myMap = new Map().set(true, 7).set({foo: 3}, ['abc']);
> [...myMap]
```

> array-->map
```
new Map([[true, 7], [{foo: 3}, ['abc']]])
Map {true => 7, Object {foo: 3} => ['abc']}
```
