---
title: js-array-遍历数组
date: 2016-09-11
categories: 
- javascript
---

```
for (let index of ['a', 'b'].keys()) {
    console.log(index);
}
// 0
// 1
```

```
for (let elem of ['a', 'b'].values()) {
    console.log(elem);
}
// 'a'
// 'b'
```

```
for (let [index, elem] of ['a', 'b'].entries()) {
    console.log(index, elem);
}
// 0 "a"
// 1 "b"
```

```
let letter = ['a', 'b', 'c'];
let entries = letter.entries();
console.log(entries.next().value); // [0, 'a']
console.log(entries.next().value); // [1, 'b']
console.log(entries.next().value); // [2, 'c']
```
