---
title: js-pattern--h-策略模式
date: 2016-09-11
categories: 
- javascript
---

## 策略比状态模式 少了一个储存状态的类

```
'use strict'

let PriceStrategy = (function () {
    class strategy {
        constructor() {
            let that = this;
            this.change = {
                return30: () => {

                },
                return50: (price) => {
                    return price/2;
                },
                percent90: () => {

                },
                percent50: () => {

                }
            }
        }
        running(algorithm,price){
            let _obj = new strategy();
            return _obj.change[algorithm] && _obj.change[algorithm](price)
        }
    }

    return new strategy().running;
})();


console.log(PriceStrategy('return50','3214.32'))
```
