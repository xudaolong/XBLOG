---
title: js-array-api-常用
date: 2016-09-11
categories: 
- javascript
---

function:
``Array.from`` 函数
从类似数组的对象或可迭代的对象返回一个数组。
```
var arr = Array.from([1, 2, 3], x => x * 10);
// arr[0] == 10;
// arr[1] == 20;
// arr[2] == 30;
```

``Array.isArray`` 函数
返回一个布尔值，该值指示对象是否为数组。

``Array.of`` 函数
从传入的参数返回一个数组。
```
var arr = Array.of(1, 2, 3);
// arr[0] == 1 
```

``concat`` 方法（数组）
返回由两个数组组合而成的新数组。

``entries`` 方法 keys values
返回包含数组的键/值对的迭代器。

```
var entries = ["a", "b", "c"].entries();
// entries.next().value == [0, "a"]
// entries.next().value == [1, "b"]
// entries.next().value == [2, "c"] 
```

``every`` 方法
检查定义的回调函数是否为数组中的所有元素返回 true。

```
// Define the callback function.
function CheckIfEven(value, index, ar) {
    document.write(value + " ");

    if (value % 2 == 0)
        return true;
    else
        return false;
}

// Create an array.
var numbers = [2, 4, 5, 6, 8];

// Check whether the callback function returns true for all of the
// array values.
if (numbers.every(CheckIfEven))
    document.write("All are even.");
else
    document.write("Some are not even.");

// Output:
// 2 4 5 Some are not even.
```

``fill`` 方法
使用指定值填充数组。

``filter`` 方法
对数组的每个元素调用定义的回调函数，并返回回调函数为其返回 true 的值的数组。

``findIndex`` 方法
返回满足回调函数中指定的测试条件的第一个数组元素的索引值。

``forEach`` 方法
为数组中的每个元素调用定义的回调函数。

``hasOwnProperty`` 方法
返回一个布尔值，该值指示某个对象是否具有指定名称的属性。

``indexOf`` 方法（数组）
返回某个值在数组中的第一个匹配项的索引。

``isPrototypeOf ``方法
返回一个布尔值，该值指示某个对象是否存在于另一个对象的原型链中。

``join`` 方法
返回由一个数组的所有元素串联而成的 String 对象。

``keys`` 方法
返回包含数组的索引值的迭代器。

``lastIndexOf ``方法（数组）
返回指定值在数组中的最后一个匹配项的索引。

``map`` 方法
对数组的每个元素调用定义的回调函数并返回包含结果的数组。

``pop`` 方法
从数组中移除最后一个元素并将该元素返回。

``propertyIsEnumerable`` 方法
返回一个布尔值，该值指示指定属性是否为对象的一部分且是否可枚举。

``push`` 方法
将新元素追加到一个数组中，并返回数组的新长度。

``reduce`` 方法
通过对数组中的所有元素调用定义的回调函数来累积单个结果。  回调函数的返回值是累积的结果，并且作为对回调函数的下一个调用中的参数提供。  

``reduceRight`` 方法
通过对数组中的所有元素调用定义的回调函数来按降序顺序累积单个结果。  回调函数的返回值是累积的结果，并且作为对回调函数的下一个调用中的参数提供。  

``reverse`` 方法
将元素顺序被反转的 Array 对象返回。

``shift`` 方法
从数组中移除第一个元素并将返回该元素。

``slice`` 方法（数组）
返回一个数组中的一部分。

``some`` 方法
检查定义的回调函数是否为数组的任何元素返回 true。

``sort`` 方法
返回一个元素已经进行了排序的 Array 对象。

``splice`` 方法
从一个数组中移除元素，如有必要，在所移除元素的位置上插入新元素，并返回所移除的元素。

``toLocaleString`` 方法
返回使用当前区域设置的字符串。

``toString`` 方法
返回数组的字符串表示形式。

``unshift`` 方法
在数组的开头插入新元素。

``valueOf`` 方法
获取对数组的引用。

``values`` 方法
返回包含数组的值的迭代器。
