# DOM增删
+ document.createElement()可以用于创建一个元素节点对象
他需要一个标签名作为参数，将会根据该标签名创建元素节点对象
并将创建好的对象作为返回值返回
+ document.createTextNode()可以用来创建一个文本节点对象
需要一个文本作为参数，将会根据该内容创建文本节点，并将新的节点返回
+ appendChild()向一个父节点中添加一个新的子节点
用法:父节点.appendChild(子节点)；
+ insertBefore()可以在指定的子节点前插入新的子节点
语法：
父节点.insertBefore(新节点,旧节点);
+ 使用innerHTML也可以完成DOM的增删
一般我们会两种方式结合使用
```js
city.innerHTML += "<li>广州</li>";
```
## 实例1
具体是[增删练习1](file:///C:/Users/Simontu/Desktop/sourse/javascript/DOM增删.html)
```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="">
    <link rel="stylesheet" href="/code/mi/css/reset.css">
    <link rel="stylesheet" href="css/domStyle.css">
    <script>
        window.onload = function () {
            // 创建一个“广州”节点，添加到#city下
            myClick("btn01", function () {
                //创建一个广州节点 <li>广州</li>
                //创建li节点
                /*
                    document.createElement()
                    可以用于创建一个元素节点对象
                    他需要一个标签名作为参数，将会根据该标签名创建元素节点对象
                    并将创建好的对象作为返回值返回
                */
                var li = document.createElement("li");

                //创建广州文本节点
                /*
                    document.createTextNode()
                    可以用来创建一个文本节点对象
                    需要一个文本作为参数，将会根据该内容创建文本节点，并将新的节点返回
                */
                var gzText = document.createTextNode("广州");

                //将gztext设置li的子节点
                /*
                    appendChild()
                        向一个父节点中添加一个新的子节点
                        用法:父节点.appendChild(子节点)；
                */
                li.appendChild(gzText);

                //获取id为city的节点
                var city = document.getElementById("city");
                //将广州添加到city下
                city.appendChild(li);

            });
            // 将“广州”节点插入到#bj前面
            myClick("btn02" , function () {
                var li = document.createElement("li");
                var gzText = document.createTextNode("广州");
                li.appendChild(gzText);
                //获取id为北京的节点
                var bj = document.getElementById("bj");
                var city = document.getElementById("city");
                /*
                    insertBefore()
                    可以在指定的子节点前插入新的子节点
                    语法：
                        父节点.insertBefore(新节点,旧节点);
                */
                city.insertBefore(li,bj);
            });
            // 使用“广州”节点替换#bj节点
            myClick("btn03" , function () {
                var li = document.createElement("li");
                var gzText = document.createTextNode("广州");
                li.appendChild(gzText);
                var bj = document.getElementById("bj");
                var city =document.getElementById("city");
                city.replaceChild(li , bj);
            });
            // 删除#bj节点
            myClick("btn04" , function () {
                var bj = document.getElementById("bj");
                // var city = document.getElementById("city");
                // city.removeChild(bj);
                bj.parentNode.removeChild(bj);
            });
            // 读取#city内的HTML代码
            myClick("btn05" , function () {
                var city = document.getElementById("city");
                alert(city.innerHTML);
            });

            // 设置#bj内的HTML代码
            myClick("btn06" , function () {
               var bj = document.getElementById("bj");
               bj.innerHTML = "杭州";

            });

            myClick("btn07" , function () {
                var city = document.getElementById("city");
                /*
                    使用innerHTML也可以完成DOM的增删
                    一般我们会两种方式结合使用
                */
                // city.innerHTML += "<li>广州</li>";
                var li = document.createElement("li");
                li.innerHTML = "广州";
                city.appendChild(li);
            })
        };

        function myClick(idStr, fun) {
            var btn = document.getElementById(idStr);
            btn.onclick = fun;
        }
    </script>
</head>

<body>
    <div id="total">
        <div id="inner">
            <p>
                你喜欢哪个城市？
            </p>

            <ul id="city">
                <li id="bj">北京</li>
                <li>上海</li>
                <li>东京</li>
                <li>首尔</li>
            </ul>

        </div>
    </div>
    <div id="btnList">
        <div><button id="btn01">创建一个“广州”节点，添加到#city下</button></div>
        <div><button id="btn02">将“广州”节点插入到#bj前面</button></div>
        <div><button id="btn03">使用“广州”节点替换#bj节点</button></div>
        <div><button id="btn04">删除#bj节点</button></div>
        <div><button id="btn05">读取#city内的HTML代码</button></div>
        <div><button id="btn06">设置#bj内的HTML代码</button></div>
        <div><button id="btn07">创建一个“广州”节点，添加到#city下</button></div>
    </div>
</body>

</html>
```

## 实例2
链接[增删练习2](file:///C:/Users/Simontu/Desktop/sourse/javascript/DOM添加删除记录.html)
```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        function deleA() {
            //点击超链接以后需要删除超链接所在的那行
            //这里我们点击那个超链接this就是谁
            /*
                注意点：
                如果this 改成 allA[i]则会出现问题 返回值为undefined的，其索引为3.
                缘由： for循环会在页面现在完成之后立即执行，
                而响应函数在超链接被点击时才执行
                当响应函数执行时，for循环早已执行完毕
            */
            var tr = this.parentNode.parentNode;
            var name = tr.getElementsByTagName("td")[0].innerHTML;
            var name = tr.children[0].innerHTML;
            //删除前弹出提示框
            //var flag = confirm("确认删除"+ tr.firstElementChild.innerHTML+"？");//兼容性欠佳
            var flag = confirm("确认删除" + name + "？");
            if (flag) {
                //删除tr
                tr.parentNode.removeChild(tr);
            }

            /*
                点击超链接以后，会跳转页面，是默认行为
                但是此时不需要页面跳转，所以要取消默认行为
                可以通过在响应函数的最后return false来取消默认行为
            */
            return false;
        };
        window.onload = function () {
            var allA = document.getElementsByTagName("a");
            for (let i = 0; i < allA.length; i++) {
                allA[i].onclick = deleA;
            }

            /*
                添加员工的功能
                    点击按钮后，将员工的信息添加到表格中
            */
            var sub = document.getElementById("addEmpButton");
            sub.onclick = function () {
                var name = document.getElementById("empName").value;
                var email = document.getElementById("email").value;
                var salary = document.getElementById("salary").value;
                var table = document.getElementById("employeeTable");
                var tbody = table.getElementsByTagName("tbody")[0];
                var tr = document.createElement("tr");
                var namreg = /^[A-Z][a-z]*$/;
                var sarreg = /^\d*\d$/;
                var emsreg = /^\w{3,}(\.\w+)*@[A-z0-9]+(\.[A-z]{2,5}){1,2}$/;
                if (namreg.test(name)) {
                    if (emsreg.test(email)) {
                        if (sarreg.test(salary)) {
                            //通过innerHTML赋值后，会将已有的都重新写入一遍，因此性能不高，推荐在其没有任何已有子元素的时候使用
                            //当目标元素下已有子元素时，不推荐使用
                            tr.innerHTML = "<td>" + name + "</td>" + "<td>" + email + "</td>" + "<td>" + salary + "</td>" + "<td><a href='deleteEmp?id=001'>Delete</a></td>";
                            var a = tr.getElementsByTagName("a")[0];
                            a.onclick = deleA;
                        } else {
                            alert("收入数值不合法");
                        }
                    } else {
                        alert("邮件地址数值不合法");
                    }
                } else {
                    alert("姓名不合法");
                }
                //    var td1 = document.createElement("td");
                //    var td2 = document.createElement("td");
                //    var td3 = document.createElement("td");

                //第3种方法



                // var td4 = document.createElement("td");
                // var dele = document.createElement("a");
                // dele.href = "deleteEmp?id=001";
                // dele.innerHTML = "Delete";
                // dele.onclick = deleA;

                // //第二种方法

                // var tdArr = [];
                // var arr = [name, email, salary];
                // for (let i = 0; i < arr.length; i++) {
                //     tdArr[i] = document.createElement("td");
                //     tdArr[i].innerHTML = arr[i];
                //     tr.appendChild(tdArr[i]);
                // };

                // //    td1.innerHTML = name;
                // //    td2.innerHTML = email;
                // //    td3.innerHTML = salary;
                // td4.appendChild(dele);
                // //    tr.appendChild(td1);
                // //    tr.appendChild(td2);
                // //    tr.appendChild(td3);
                // tr.appendChild(td4);


                tbody.appendChild(tr);

            }
        }
    </script>
    <style>
        #employeeTable {
            margin: 10px auto;
            border-collapse: collapse;
            border: solid 1px;
        }

        #formDiv {
            width: 250px;
            margin: 30px auto;
            padding-left: 30px;
            padding-bottom: 30px;
            border: 2px solid black;
        }
    </style>
</head>

<body>
    <table id="employeeTable" border="1">
        <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Salart</th>
            <th>$nbsp;</th>
        </tr>
        <tr>
            <td>Tom</td>
            <td>tom@tom.com</td>
            <td>5000</td>
            <td><a href="deleteEmp?id=001">Delete</a></td>
        </tr>
        <tr>
            <td>Jerry</td>
            <td>jerry@sohu.com</td>
            <td>8000</td>
            <td><a href="deleteEmp?id=001">Delete</a></td>
        </tr>
        <tr>
            <td>Bob</td>
            <td>bob@tom.com</td>
            <td>10000</td>
            <td><a href="deleteEmp?id=001">Delete</a></td>
        </tr>
    </table>

    <div id="formDiv">
        <h4>添加新员工</h4>
        <table>
            <tr>
                <td class="word">name：</td>
                <td class="inp">
                    <input type="text" name="empName" id="empName">
                </td>
            </tr>
            <tr>
                <td class="word">email：</td>
                <td class="inp">
                    <input type="text" name="email" id="email">
                </td>
            </tr>
            <tr>
                <td class="word">salary：</td>
                <td class="inp">
                    <input type="text" name="salary" id="salary">
                </td>
            </tr>
            <tr>
                <td colspan="2" align="center">
                    <button id="addEmpButton" value="abc">
                        Submit
                    </button>
                </td>
            </tr>
        </table>
    </div>
</body>

</html>
```