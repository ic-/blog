---
title: gen-thunk-promise-co
date: 2017-02-20 20:37:12
tags: 
    - js
    - promise
commit: false
categories: js
---
* Generator
* 传统异步 代码各种嵌套
* promise 只是改变了写法
* 然后最后用catch 捕获执行中的错误

```javascript
var readFile = require('fs-readFile-promise')
readFile(fileA)
.then(function(data){
console.log(data.toString())
})
.then(function(){
return readFile(fileB)
})
.then(function(data){
console.log(data.toString())
})
.catch(function(err){
//
})
```
<!--more-->

* Generator
* ES6 中协程的体现 函数可以交出执行权（即暂停执行，又可以恢复执行）
* function_ name\(\){} 必须加上 _ 号
* 整个 Generator 就是一个异步函数封装器
* Gen 函数执行返回一个内部指针
* 函数体内外数据交互，处理错误机制

```javascript
function* gen(x){
var y = yield x + 2;
return y
}

var g = gen(1)
g.next() // {value: 3, done: false}
g.next() // {value: undefined, done: true}

var g = g.gen(1)
g.next() //{value: 3, done: false}
g.next(2) //{value:2, done: true}

var g = gen()
g.next(2) // undefined+2 = NaN {value:NaN, done: false}
g.next(3) // {value: 3, done: true}
```

```javascript
//内部处理错误，外部捕获
function* gen(x){
try{
var y = yield x + 2;
}catch(x){
console.log(e)
}
return y
}

//异步
var fetch = require('node-fetch')
function* gen(){
var url = 'https://api.github.com/users/github';
var result = yield fetch(url);
console.log(result.bio)
}

var g = gen();
var result = g.next(); //执行fetch {value: data, done: true}

result.value.then(function(data){
return data.json()
}).then(function(data){
g.next(data)
})
```

## Thunk

* 传名调用 call by name
* 即只有在用的时候求值
* 用函数作为参数传入，调用的时候执行函数实现
* thunk 函数的含义
* 实现将参数放到一个零时的函数，然后把这个临时函数传入函数内，这个临时函数就是Thunk

```javascript
function f(m){
return m*2
}

f(x+5)
//等同于

var thunk = function(){
return x+5
}

function f(thunk){
return thunk()*2
}
```

* Javascript语言的thunk函数
* Thunk 函数替换的是多参数函数
* 将其替换成单参数的版本，且只接受回调函数作为参数
* 任意函数只要有回调函数都能写成Thunk函数的形式
* 生产环境转行 thunkify

```javascript
//正常版本的readFile(多参数版本)

fs.readFile(filename, callback)

//Thunk 版本的 readFile(单参数)
var readFileThunk = Thunk(fileName);
readFileThunk(callback)

var Thunk = function(filename){
return function(callback){
return fs.readFile(filename, callback)
}
}

// Thunk函数转换器
var Thunk = function(fn){
return function(){
var args = Array.prototype.slice.call(arguments);
return function(callback){
args.push(callback)
return fn.apply(this,args)
}
}
}

var readFileThunk = Thunk(fs.readFile);
readFileThunk(filename)(callback)
```

* Generator 函数的流程管理

```javascript
var fs = require('fs')
var thunkify = require('thunkify')
var readFile = thunkify(fs.readFile)

var gen = function* (){
var r1 = yield readFile('/etc/fstab');
console.log(r1.toString())
var r2 = yield readFile('/etc/shells')
console.log(r2.toString())
}

var g = gen()

var r1 = g.next()

r1.value(function(err, data){
if(err)throw err
var r2 = g.next(data) //把读取的data 往后传
r2.value(function(err, data){
if(err) throw err
g.next(data)
})
})
```

* Thunk 函数的自动流程管理

```javascript
function run(fn){
var gen = fn()

function next(err, data){
var result = gen.next(data)
if(result.done)return
result.value(next)
}

next()
}


var gen = function* (){
var f1 = yield readFile('fileA');
var f2 = yield readFile('fileB')
var f3 = yield readFile('fileC')
}

run(gen)
```


