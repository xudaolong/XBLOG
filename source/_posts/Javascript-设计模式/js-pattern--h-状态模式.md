---
title: js-pattern--h-状态模式
date: 2016-09-11
categories: 
- javascript
---

```
'use strict';

let State = (function () {
    class State {
        constructor() {
            /**
             * 状态类
             * @type {{}}
             * @private
             */
            let that = this;

            that._currState = {};
            that.states = {
                jump: function () {
                    console.log("jump")
                },
                move: function () {
                    console.log("move")
                },
                shoot: function () {
                    console.log("shoot")
                },
                squat: function () {
                    console.log("squat")
                }
            };
            /**
             * 创建组合类之动作控制类
             * @type {{change, goes}}
             */
            let {change, goes} = (function () {
                class action {
                    constructor() {
                        this.change = function () {
                            //参数转成数组
                            let arg = [].slice.call(arguments).sort();
                            that._currState = {};
                            if (arg.length) {
                                for (var i in arg) {
                                    that._currState[arg[i]] = true;
                                }
                            }
                            return that;
                        }

                        this.goes = function () {
                            console.log("触发一次动作")
                            for (var i  in that._currState) {
                                that.states[i] && that.states[i]()
                            }
                            return that;
                        }
                    }

                }
                let _action = new action();
                return {
                    change: _action.change,
                    goes: _action.goes
                }
            })();
            this.change = change;
            this.goes = goes;
        }
    }

    return new State();
})();

console.log(State.change('jump', 'shoot').goes().goes().change("move").goes());
```
