# DOM查询

## 获取元素节点

通过document对象调用

1. getElementById() 通过id属性获取一个元素节点对象
2. getElementsByTagName() 通过标签名获取一组元素节点对象，返回结果是伪数组
3. getElementsByName() 通过name属性获取一组元素节点对象

## 获取元素节点的子节点

通过具体的元素节点调用

1. getElementsByTagName()
    + 方法，返回当前节点的指定标签名后代节点
2. childNodes(children)
    + 属性，表示当前节点的所有子节点,然而包括文本节点在内的所有节点
    + 根据DOM标签标签间空白也会当做文本节点
    + 注意：在ie8及以下的浏览器中，不会将空白文档当成子节点
    + 推荐使用**children**
3. firstChild(firstElenmentChild)
    + 属性，表示当前节点的第一个子节点，包括空白节点
    + firstElenmentChild是获取第一个子元素节点
    + firstElenmentChild不兼容ie8及以下的浏览器
4. lastChild(lastElenmentChild)
    + 属性，表示当前节点的最后一个子节点，包括空白节点
    + lastElenmentChild是获取最后一个子元素节点
    + lastElenmentChild不兼容ie8及以下的浏览器

## 获取父节点和兄弟节点

通过具体的节点调用

1. parentNode
   + 属性，表示当前节点的父节点
2. previousSibling
   + 属性，表示当前节点的前一个兄弟节点
3. nextSibling
   + 属性，表示当前节点的后一个兄弟节点

## 获取内部

+ innerHTML
通过这个属性可以获取到元素内部的HTML代码
+ innerText
该属性可能获取到元素内部的文本内容
它和innerHTML类似，不同使得它会自动去除html标签

## 实例

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="/code/mi/css/reset.css">
    <link rel="stylesheet" href="css/style.css">
    <script>
       //建立一个绑定单击响应的函数
        function myClick(idStr, fun) {
            var btn = document.getElementById(idStr);
            btn.onclick = fun;
        }
        window.onload = function () {
            //为id为btn01的按钮绑定一个单击响应函数
            var btn01 = document.getElementById("btn01");
            btn01.onclick = function () {
                //查找[[bj]]节点
                var bj = document.getElementById("bj");
                //打印bj
                //innerHTML 通过这个属性可以获取到元素内部的HTML代码
                alert(bj.innerHTML);
            };
            //为id为btn02的按钮绑定一个单击响应函数
            var btn02 = document.getElementById("btn02");
            btn02.onclick = function () {
                //查找所有li节点
                //getElementByTagName()可以根据标签名来获取一组元素节点对象
                //这个方法会给我们返回一个类数组对象，所有查询到的元素都会封装到对象中
                //即使查询到的元素只有一个，也很珍贵领导数组中返回
                var lis = document.getElementsByTagName("li");
                //打印lis
                //alert(lis.length);
                //遍历数组
                for (var i = 0; i < lis.length; i++) {
                    alert(lis[i].innerHTML);
                };
            };
            //为id为btn03的按钮绑定一个单击响应函数
            var btn03 = document.getElementById("btn03");
            btn03.onclick = function () {
                //查找name=gender的所有节点
                var inputs = document.getElementsByName("gender");
                //打印inputs
                //alert(inputs.length);
                //遍历数组
                for (var i = 0; i < inputs.length; i++) {
                    //innerHTML用于获取元素内部的HTML代码
                    //对于自结束标签 这个属性没有意义
                    //直接使用元素.属性名
                    /*
                    例子： 元素.id 元素.name 元素.value
                    注意：class属性不能采用这种方式
                        读取class属性时需要使用 元素.className
                    */
                    alert(inputs[i].value);
                };
            };
            //查找[[city下所有li]]节点
            var btn04 = document.getElementById("btn04");
            btn04.onclick = function () {
                var city = document.getElementById("city");
                var lis = city.getElementsByTagName("li");
                for (var i = 0; i < lis.length; i++) {
                    alert(lis[i].innerHTML);
                };
            };

            //返回[[city]]的所有子节点
            var btn05 = document.getElementById("btn05");
            btn05.onclick = function () {
                var city = document.getElementById("city");
                /*childNodes属性会获取包括文本节点在内的所有节点
                根据DOM标签标签间空白也会当成文本节点
                注意：在ie8及以下的浏览器中，不会讲空白文档当成子节点
                所以该属性在ie8中会返回4个子元素而其他浏览器是9个
                */
                // var cns = city.childNodes;
                // for (var i = 0; i < cns.length; i++) {
                //     alert(cns[i]);
                // }
                var cns2 = city.children;
                for (var i = 0; i < cns2.length; i++) {
                    alert(cns2[i].innerHTML);
                };
            };
            //返回[[phone]]的第一个子节点
            var btn06 = document.getElementById("btn06");
            btn06.onclick = function () {
                var phone = document.getElementById("phone");
                var frs = phone.firstChild;//[[text]] 空白文档当成子节点
                //var frs = phone.firstElementChild;
                alert(frs);
            };
            //返回[[bj]]的父节点
            myClick("btn07", fun);
            function fun() {
                var bj = document.getElementById("bj");
                var fth = bj.parentNode;
                //alert(fth.innerHTML);
                /*
                innerText
                该属性可能获取到元素内部的文本内容
                */
                alert(fth.innerText);

            };
            //返回[[android]]的前一个兄弟节点
            var btn08 = document.getElementById("btn08");
            btn08.onclick = function () {
                var android = document.getElementById("android");
                var bro1 = android.previousElementSibling;
                alert(bro1.innerHTML);
                var bro2 = android.previousSibling;
                alert(bro2.textContent);
            };
            //读取[[username的value]]属性值
            myClick("btn09" , function () {
                var username = document.getElementById("username");
                var value = username.value;
                alert(value);
            });
            //设置[[username的value]]属性值
            myClick("btn10", fun02);
            function fun02() {
                var username = document.getElementById("username");
                username.value = "还行吧";
            }
            //返回[[bj]]的文本值
            myClick("btn11", function () {
                var bj = document.getElementById("bj");
                 //alert(bj.innerText);
                alert(bj.firstChild.nodeValue);
            });
        };
    </script>
</head>
<body>
    <div id="total">
        <div class="inner">
            <p>
                你喜欢哪个城市?
            </p>

            <ul id="city">
                <li id="bj">北京</li>
                <li>上海</li>
                <li>东京</li>
                <li>首尔</li>
            </ul>

            <br>
            <br>

            <p>
                你喜欢哪款单机游戏？
            </p>

            <ul id="game">
                <li id="rl">红警</li>
                <li>实况</li>
                <li>极品飞车</li>
                <li>魔兽</li>
            </ul>

            <br />
            <br />

            <p>
                你手机的操作系统是？
            </p>

            <ul id="phone"><li>IOS</li><li id="android">Android</li><li>windows Phone</li></ul>
        </div>

        <div class="inner">
            gender:
            <input type="radio" name="gender" value="male">
            Male
            <input type="radio" name="gender" value="female">
            Female
            <br>
            <br>
            name:
            <input type="text" name="name" id="username" value="abcde">
        </div>
        <div id="btnList">
            <div><button id="btn01">查找[[bj]]节点</button></div>
            <div><button id="btn02">查找所有li节点</button></div>
            <div><button id="btn03">查找name=gender的所有节点</button></div>
            <div><button id="btn04">查找[[city下所有li]]节点</button></div>
            <div><button id="btn05">返回[[city]]的所有子节点</button></div>
            <div><button id="btn06">返回[[phone]]的第一个子节点</button></div>
            <div><button id="btn07">返回[[bj]]的父节点</button></div>
            <div><button id="btn08">返回[[android]]的前一个兄弟节点</button></div>
            <div><button id="btn09">返回[[username的value]]属性</button></div>
            <div><button id="btn10">设置[[username的value]]属性值</button></div>
            <div><button id="btn011">返回[[bj]]的文本值</button></div>
        </div>
    </div>
</body>
</html>
```

## 图片切换实例

```js
<head>
<script>
        window.onload = function () {
            var prev = document.getElementId("prev");
            var next = document.getElementId("next");
            /*
            要切换图片就是要修改img标签的src属性
            */
            //获取img标签
            var img = document.getElementsByTagName("img");
            console.log(img);
            //创建一个数组，用来保存图片的路径
            var imgArr = ["img/i1.jpg","img/i2.jpg","img/i3.jpg","img/i4.jpg","img/i5.jpg"];
            //创建一个变量，来保存当前正在显示的图片的索引
            var index = 0;  

            
            //获取id为info的p元素
            var info = document.getElementById("info");
            //设置提醒文字
            info.innerHTML = "一共" + imgArr.length + "张图片,当前第" + (index+1) + "张";
            //分别为两个按钮绑定单击响应函数
            prev.onclick = function () {
                // alert("上一张");
                //索引自减
                index--;
                if (index<0) {
                    index = imgArr.length-1;
                }   
                img.src = imgArr[index];
                //当点击按钮以后，重新设置信息
                info.innerHTML = "一共" + imgArr.length + "张图片,当前第" + (index+1) + "张";
            };
            next.onclick = function () {
                //alert("下一张");
                //切换图片就是修改img的src属性
                index++;
                if (index>imgArr.length+1) {
                    index = 0;
                }
                img.src = imgArr[index];
                //当点击按钮以后，重新设置信息
                info.innerHTML = "一共" + imgArr.length + "张图片,当前第" + (index+1) + "张";
            };
        };    
    </script>
    </head>
    <body>
    <div id="outer">
            <p id = "info"></p>
                <img src="img/i1.jpg" alt ="冰棍">
                <button id="prev" href="">上一张</button>
                <button id="next" href="">下一张</button>
            </div>
    </body>
```

## 获取的其他方法

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        window.onload = function () {
            //获取body标签
            //在document中有一个属性body，他保存的是body的引用
            var body = document.body;
            /*
                document.documentElement 保存的是html根标签
            */
            var html = document.documentElement;
            //document.all代表页面中所有的元素
            var all = document.all;
            console.log(all);
            for (let i = 0; i < all.length; i++) {
                console.log(all[i]); 
            }
            all = document.getElementsByTagName("*");
            /*
                根据元素的class属性值查询一组元素节点对象
                getElemByClassName()可以根据class属性值获取一组元素节点对象
                但是该方法不支持IE8及以下的浏览器
            */
            var box1 = document.getElementsByClassName("box1");
            console.log(box1);
            
            //获取class为box1中的所有的div
            // document.querySelector();
                //需要一个选择器的字符串作为参数，可以根据一个css选择器来查询一个元素的节点对象
                //虽然IE8中没有getElementsByClassName() 但是可以使用querySelector
                //使用该方法总会返回唯一的一个元素，如果满足条件的元素有多个，那么它只会返回第一个           
            var div = document.querySelector(".box1 div");
            var div1 = document.querySelector(".box1");
            //document.querySelectorAll()
                //该方法和querySelector()用法类似，不同的是它会将符合条件的元素封装到一个数组中返回
                //即使符合条件的元素只有一个，它也会返回到数组
            console.log(div1.innerHTML);//我是第一个box1
            console.log(div);
        }   
    </script>
</head>
<body>
    <div class="box1">我是第一个box1
        <div></div>
    </div>
    <div class="box1">
        <div></div>
    </div>
    <div class="box1">
        <div></div>
    </div>
    <div class="box1">
        <div></div>
    </div>
    <div></div>
</body>
</html>
```
