# DOM查询
## 获取元素节点
通过document对象调用
1. getElementById() 通过id属性获取一个元素节点对象
2. getElementsByTagName() 通过标签名获取一组元素节点对象
3. getElementsByName() 通过name属性获取一组元素节点对象

## 获取元素节点的子节点
通过具体的元素节点调用
1. getElementsByTagName()
    + 方法，返回当前节点的指定标签名后代节点
2. childNodes
    + 属性，表示当前节点的所有子节点
3. firstChil
    + 属性，表示当前节点的第一个子节点
4. lastChild
    + 属性，表示当前节点的最后一个子节点

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
        window.onload = function () {
            //为id为btn01的按钮绑定一个单击响应函数
            var btn01= document.getElementById("btn01");
            btn01.onclick = function () {
                //查找#bj节点
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
        
        //查找#city下所有li节点
        //返回#city的所有子节点
        //返回#phone的第一个子节点
        //返回#bj的父节点
        //返回#android的前一个兄弟节点
        //读取#username的value属性值
        //设置#username的value属性值
        //返回#bj的文本值
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

            <ul id="phone">
                <li>IOS</li>
                <li id="android">Android</li>
                <li>windows Phone</li>
            </ul>
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
            <div><button id="btn01">查找#bj节点</button></div>
            <div><button id="btn02">查找所有li节点</button></div>
            <div><button id="btn03">查找name=gender的所有节点</button></div>
            <div><button id="btn04">查找#city下所有li节点</button></div>
            <div><button id="btn05">返回#city的所有子节点</button></div>
            <div><button id="btn06">返回#phone的第一个子节点</button></div>
            <div><button id="btn07">返回#bj的父节点</button></div>
            <div><button id="btn08">返回#android的前一个兄弟节点</button></div>
            <div><button id="btn09">返回#username的value属性</button></div>
            <div><button id="btn10">设置#username的value属性值</button></div>
            <div><button id="btn011">返回#bj的文本值</button></div>
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

