# this
解析器在调用函数每次都会向函数内部传递进一个隐含的参数
这个隐藏的参数就是this,this指向的是一个对象，
这个对象我们称为函数执行的上下文对象，
根据函数的调用方式的不同，this会指向不同的对象
1. 以函数的形式调用时，this永远都是window
2. 以方法的形式调用时，this就是调用方法那个的对象
```js
function fun(a,b){
    console.log("a ="+ a + ",b =" + b);
    console.log(this);
}
fun(123,456);
```
```js
function fun(){
    console.log(this);
}

var obj = {
    name : "孙悟空",
    sayName : fun
};
console.log(obj.sayName == fun);//true
```
```js
function fun(){
    console.log(this.name);
}

var obj = {
    name : "孙悟空",
    sayName : fun
};

var obj2 = {
    name: "沙和尚",
    sayName : fun
};
var name ="全局中的name属性";
//以方法形式调用，this是调用方法的对象
obj.sayName();//孙悟空
obj2.sayName();//沙和尚
//以函数形式调用，this是window
fun();//全局中的name属性
```
