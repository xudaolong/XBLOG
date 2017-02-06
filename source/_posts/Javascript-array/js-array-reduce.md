---
title: js-array-reduce
date: 2016-09-11
categories: 
- javascript
---

# 返回值是积累的结果

```
  // good
  let sum = 0;
  numbers.forEach((num) => sum += num);
  sum === 15;

  // best (use the functional force)
  const sum = numbers.reduce((total, num) => total + num, 0);
  sum === 15;

// Define the callback function.
function appendCurrent (previousValue, currentValue) {
    return previousValue + "::" + currentValue;
    }

// Create an array.
var elements = ["abc", "def", 123, 456];

// Call the reduce method, which calls the callback function
// for each array element.
var result = elements.reduce(appendCurrent);

document.write(result);

// Output:
//  abc::def::123::456
```
