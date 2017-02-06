---
title: js-Promise
date: 2016-09-11
categories: 
- javascript
---

```
var assert = require('power-assert');

describe('Basic Test', function () {

    it("should use `done` for test?", function (done) {
        var promise = Promise.resolve();
        promise.then(function (value) {
            assert(false);
        }).then(done, done);
    });

});

```

> 第二种写法
```
it("should be fail", function () {
    return Promise.resolve().then(function () {
        assert(false);// => 测试失败
    });
});
```
