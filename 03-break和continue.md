# break
break关键字可以用来退出switch火循环语句
不能在if语句中使用break和continue。
```js
for(var i = 10 ;i<5 ;i++){
    console.log(i);
    if(i == 2){
        break;//这个break不是在if中起作用，而是整个for中，起作用
    }
}
```
可以为循环语句创建一个label，来标识当前的循环
label：循环语句
使用break语句时，可以在break后跟着一个label，
这样break将会结束指定的循环，而不是就近
```js
outer:
for(var i = 0 ; i < 5 ; i++){
    console.log("@外层循环:"n+ i)
    for(var j = 0 ; j < 5 ; j++){
        break outer;
        console.log("内层循环：" + j)
    }
}
```
# continue
continue 关键词可以用来跳过档次循环
```js
for(var i = 10 ;i<5 ;i++){
    if(i == 2){
        continue;
    }
     console.log(i);
}
```
同样continue也是默认只会对离他最近的循环起作用
```js
//只运行外部循环
for(var i = 0 ; i < 5 ; i++){
    console.log("@外层循环:"n+ i)
    for(var j = 0 ; j < 5 ; j++){
        continue ;
        console.log("内层循环：" + j)
    }
}
```

>合理使用break和continue，提高程序运行性能