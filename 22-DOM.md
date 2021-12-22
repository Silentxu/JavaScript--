# DOM
DOM,全称Document Object Model 文档对象模型
js中通过DOM来对HTML文档进行操作，只要理解了DOM就可以随心所欲的操作WEB页面
+ 文档
文档表示的就是整个的HTML网页文档
+ 对象
对象来表示将为行业中的每一个部分都转换为了一个对象
+ 模型
试用魔性来表示对象之间的关系，这样方便我们获取对象
### 节点
Node——构成HTML文档最基本的单元
常用的节点分为四类：
**文档节点**：这个HTML文档
**元素节点**：HTML文档中的HTML标签
**属性节点**：元素的属性
**文本节点**：HTML标签中的文本内容
```js
<p id = "pId">This is a paragraph</p>
     属性节点       文本节点
     整体为元素节点
```
|       |nodeName|nodeType|nodeValue|
|  ----  | ----  | ---- |---- |
|文档节点|[[document]]|  9  |null|
|元素节点| 标签名 |   1  |null|
|属性节点| 属性名 |   2  |属性值|
|文本节点| [[text]] |   3   |文本内容|


浏览器已经为我们提供文档节点 对象这个对象window属性
可以在页面中直接使用，文档节点代表的是整个网页
```js
<button id = "btn" >我是一个按钮</button>
<script>
//获取到button对象
var btn = document.getElementById("btn");
//修改按钮的文字
btn.innerHTML = "I'm Button";
</script>
```
### 事件
事件，就是用户和浏览器之间的交互行为
比如，点击按钮，鼠标移动，关闭窗口。。

我们可以在事件中对应的属性中设置一些js代码，
这样当事件被触发时，这些代码将会执行

```js
<button id = "btn" onclick = "alert('你点击我了');">我是一个按钮</button>
<script></script>
```
>这种写法我们称为结构和行为耦合，不方便维护，不推荐使用

可以为按钮的对应事件绑定处理函数的形式来响应事件
这样当事件被触发时，其对应的函数将会被调用

```js
<button id = "btn">我是一个按钮</button>
<script>
//获取按钮对象
var btn = document.gerElementById("btn");
//console.log(btn);
//可以为按钮的对应事件绑定处理函数的形式来响应事件

//绑定一个点击事件
btn.onclick = function(){
     alert("已点击~");
}
</script>
```
>像这种为单击事件绑定的函数，我们称为单击响应函数

