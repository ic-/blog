---
title: 函数基础
date: 2017-03-30 14:41:25
tags:
    - js
commit: false
categories: js
---
### 函数基础知识
#### 函数定义
```js
function fn(){}
var fn = function(){}
var fn = new Function(arg1, arg2, "console.log(arg1,arg2)" )
```
#### 调用方法
- 直接调用 fn()
- 链接中 <a href="javascript:fn()" ></a>
- 事件中
- 递归
<!--more-->
```js
document.onLoad = function(){
    fn()
}

function aa(n) {
  if(n < 10){
      n++;
      aa(n)
  }else{
      return n
  }
}
```
#### 方法
- fn.apply(obj, [args])
- fn.call(obj, arg1, arg2, ...)
- fn.toString()
#### arguments 对象
- 实参参数列表
- 有下标属性 类数组
- 属性
    - arguments.length
    - arguments.callee  //返回当前正在指向对象
    - arguments.caler   //返回调用当前正执行函数的 函数
#### 函数参数
- 形参 定义函数时使用的参数
- 实参 调用函数时使用的参数
    - 形参 > 实参  形参undefined
    - 实参 > 形参  忽略

#### 指针标识
- this 指向当前对象
- callee 指向参数集合所属函数
- prototype 函数的原型对象
- constructor 函数的构造函数