---
title: ES6
date: 2017-02-20 20:22:07
tags: 
    - ES6
    - js
commit: false
categories: js
---
## ES6

### Let & Const
```js
/*
1.没有预加载 变量提升
2.块级作用域中 如果有声明变量，那么在声明之前不能使用\(暂时性死区\)
3.不允许重复声明
4.块级作用域
5.允许块级作用域中声明函数 大括号 必须
6.const 声明常量 let 声明变量
7.顶层变量 不再window下
*/
function f1() {
    let n = 5;
    if (true) {
        let n = 10;
    }
    console.log(n); // 5
}
if(true){
    function f() {}
}
let x = 1;
window.x //undefined
```
<!--more-->

### 变量的解构：
```
按照一定的模式，从数组和对象中提取值，对变量进行赋值

如果解构不成功等于undefined

适用于 var let const

数组按顺序

对象按key值

对象解构中模式不会被赋值 （即： let {a: {b: c}} = obj 中的a,b）

数组 字符串 的length 可以用

不要再模式中使用圆括号
```

##### 数组解构

```js
//匹配模式：
var [a, b, c] = [1, 2, 3]
a //1
b //2
c //3

let [, ,third] = ['foo', 'bar', 'baz']
third //'baz'

let [head, ...tail] = [1,2,3,4]
head //1
tail //[2,3,4]

//默认值：
var [x= 1] = [undefined]
x //1
var [x = 1] = [null]
x //null
```

##### 对象解构

```js
var {foo, bar} = {foo: 'aaa', bar: 'bbb'}
foo //aaa
bar //bbb

let obj = {first: 'hello', last: 'world'}
let {first: f, last: l} = obj
f //hello
l //world
first //error

//默认值：
var {x = 3} = {}
x //3

let {log, sin, cos} = Math
```

##### 字符串解构

```js
const {a,b,c} = 'edf'
a //e
b //d
c //f

//使用length 属性
let {length: len} = 'hello'
len //5
```

##### 数值和布尔值

```js
let {toString: s} = 123;
s // function toString(){}
s ==== Number.prototype.toString //true

let {toString: s} = true;
s === Boolean.prototype.toString //true
```

##### 函数参数的解构赋值

```js
function add([x,y]){
return x+ y;
}
add([1,2]) //3

// 获取键名
for (let [key] of map) {
// ...
}

// 获取键值
for (let [,value] of map) {
// ...
}

```

### 字符串扩展
```js
1.字符串模板
2.字符串遍历 for..of
3.at
4.includes
5.startsWith
6.endsWith
7.repeat 重复n次返回新字符串
8.padStart 头部补全
9.padEnd
```

### 正则扩展
```js
1.RegExp构造函数
new RegExp(/abc/ig, 'i').flags //覆盖
2.字符串正则方法 match replace split search 全部指向正则
```

### 数值扩展
```js
1.Number.isFinite() Number.isNaN() Number.isInteger() //判断是否是整数 
2.Number.parseInt() Number.parseFloat()
3.Number.EPSILON 极小常量
4.Number.isSafeInteger()
5.Math.trunc()返回整数部分
6.Math.sign() //-1 负数 +1 正数 0: 0
7.Math.cbrt() //立方根
```
### 数组扩展
```js
1.Array.from() //类数组 可遍历对象 转换为数组
```