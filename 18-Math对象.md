# Math对象
Math和其他的对象不同，他不是一个构造函数，
它属于一个工具类不用创建对象，他里边封装了数学运算相关的属性和方法
比如 Math.PI 表示的圆周率
### abs()用来计算一个数的绝对值
```js
console.log(Math.abs(-1));//1
```
### ceil()向上取整
```js
console.log(Math.ceil(1.4));//2
```
### floor()向下取整
```js
console.log(Math.floor(1.6));//1
```
### round()四舍五入取整
```js
console.log(Math.round(1.6));//2
```
### random()生成0-1之间的随机数
```js
console.log(Math.random());
```
生成0-10之间的随机数
```js
console.log(Math.round(Math.random()*10));
```
**生成0-x之间的随机数**
```js
console.log(Math.round(Math.random()*x));
```
生成1-10之间的随机数
```js
console.log(Math.round(Math.random()*9) + 1);
```
**生成[x，y)之间的随机数**
```js
console.log(Math.round(Math.random()*(y-x)) + x);
```
**生成[x-y]之间的随机数**
```js
console.log(Math.round(Math.random()*(y-x+1)) + x);
```
### max()最大值
```js
console.log(Math.max(120,30,21));//120
```
### min()最小值
```js
console.log(Math.min(120,30,21));//21
```
### pow(x,y)返回x的y次幂
```js
console.log(Math.pow(3,2));//9
```
### sqrt()开方
```js
console.log(Math.sqrt(9));//3
```