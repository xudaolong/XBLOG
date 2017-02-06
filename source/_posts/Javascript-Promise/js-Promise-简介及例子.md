---
title: js-Promise-简介及例子
date: 2016-09-11
categories: 
- javascript
---

> 用于管理与异步API交互的抽象对象,避免使用回调函数的层层嵌套

> 状态:等待->完成->拒绝

> 必须有一个then(),第一个参数是resolved,第二个是rejected函数;

实例:
查询学生的信息列表，有一个文本框可以输入学生的姓名，可以进行查找指定的学生信息，如果不存在就不进行学生信息列表的查询了，如果存在，再进行下一步的查询。

```
<script type="text/javascript">

        //判断是否存在该学生姓名
        var isExistStu = function (name) {
            var promise = new Promise(function (resolve, reject) {
                $.ajax({
                    type: "Post",
                    url: "/student/student/checkstu",
                    dataType: "json",
                    data: JSON.stringify({
                        name: name
                    }),
                    contentType: "application/json;charset-utf-8",
                    success: function (data) {
                        resolve(data);  //data 返回来的是 true 或者 false
                    }
                });
            });
        }

        //查询根据学生姓名查询学生信息列表
        var searchStu = function (name) {
            var promise = new Promise(function (resolve, reject) {
                $.ajax({
                    type: "Post",
                    url: "/student/student/getstulist",
                    dataType: "json",
                    data: JSON.stringify({
                        name: name
                    }),
                    contentType: "application/json;charset-utf-8",
                    success: function (data) {
                        resolve(data);  //data 返回来的是学生信息列表
                    }
                });
            });
        }

        

        window.onload = function () {
            var stuName = $("txtName").val();
            isExistStu(stuName).then(function (data) {
                if (data == "true") {
                    return searchStu(stuName);
                }
                else {
                    return;
                }
            }).then(function (data) {
                showTable(data);
            })
        }

        //展示 学生信息列表表格
        function showTable(data) {
            var html = "<table>";
            for (var i = 0; i < data.length; i++) {
                html += "<tr>";
                html += "<td>" + data.name + "</td>";
                html += "<td>" + data.address + "</td>";
                html += "</tr>";
            }
            html += "</table>";

            $(">divTable").html(html);
        }

    </script>
    
    
    
    
    function add(xPromise,yPromise) {
    // `Promise.all([ .. ])`接收一个Promise的数组，
    // 并返回一个等待它们全部完成的新Promise
    return Promise.all( [xPromise, yPromise] )

    // 当这个Promise被解析后，我们拿起收到的`X`和`Y`的值，并把它们相加
    .then( function(values){
        // `values`是一个从先前被解析的Promise那里收到的消息数组
        return values[0] + values[1];
    } );
}

// `fetchX()`和`fetchY()`分别为它们的值返回一个Promise，
// 这些值可能在 *现在* 或 *稍后* 准备好
add( fetchX(), fetchY() )

// 为了将两个数字相加，我们得到一个Promise。
// 现在我们链式地调用`then(..)`来等待返回的Promise被解析
.then( function(sum){
    console.log( sum ); // 这容易多了！
} );

```
