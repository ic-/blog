---
title: Array
date: 2017-03-20 18:24:06
tags: 
    - js
    - array
commit: false
categories: js
---

### Array 
#### 创建数组的方法
```js
var arr = new Array(3)  //[undefined * 3]
var arr = new Array(1,2,3) //[1,2,3]
var arr = [1,2,3]
```
#### 属性
```js
arr.constructor  //Array
arr.length    //num
arr.__proto__
```
<!--more -->
#### 方法
```js
    arr[n] = 'new ele'
    delete arr[0]   //[undefied, 2,3]
    arr.push(add_end)   //arr.length    arr has change 尾部插入
    arr.unshift()   //arr.length    arr has change 头部插入
    arr.pop()       //arr.length    arr has change 尾部删除
    arr.shift()     //arr.length    arr has change 头部删除
    
    arr.slice(start, end)   //new arr arr no change 
    arr.slice(start)        
    arr.slice(start, -end)
    // return delete ele_arr  arr has change
    arr.splice(start, delete_length, add_element) 
    
    arr.sort((x, y)=>{
        return x - y > 0
        return x - y < 0
        return x - y = 0
    })
    arr.reverse() 
    arr.concat([])
    arr.join(',')
    
    arr.indexOf(ele, start)
    arr.lastIndexOf(ele)
    
    //迭代方法
    arr.every((item, index, arr) =>{  //所以为true 就为true
        return true/false
    })
    
    arr.some((v, k, arr)=>{})  //任意一项返回 true 为true
    
    arr.filter((item, index, arr)=>{  //返回值为true的新数组
    })
    
    arr.forEach((v, k, arr) => { //没有返回值
    })
    
    arr.map((v, k, arr) =>{}}) //new arr 
```
    