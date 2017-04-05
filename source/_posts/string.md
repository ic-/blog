---
title: 字符串 string
date: 2017-03-30 16:36:17
tags:
    - js
    - string
commit: false
categories: js
---
### 字符串相关内容

#### 查找方法
- charAt(n) 
    - n > len  //空字符串
- charCodeAt(n)  //unicode编码
    - n > len  //NaN
- fromCharAt(unicode1, unicode2, ...) //跟进字符串编码创建字符串
    - 返回字符串
    
#### 位置方法
- indexOf()
- lastIndexOf() 
    - url获取参数 split(url.lastIndexOf('?'))
- 找到返回位置
- 未找到返回 -1
<!--more-->

#### 匹配方法
- match
    - 一个或者多个匹配
    - 返回匹配数组
    - 有g 多个匹配
        - 所有匹配的子串
        - 没有派生属性
        - 没有子表达式匹配
    - 无g 单个匹配
        - 匹配文本
        - 其他子表达式匹配
        - 属性
            - input 调用改方法的字符串对象
            - index 匹配文本的起始位置
            - lastIndex 匹配文本的结束位置
    - 没找到返回null
- search
    - 找到返回位置
    - 未找到返回 -1
- replace
    + $$ //$
    + $& //整个模式的子字符串  就是匹配的内容
    + $' //匹配字符串之前的字符串
    + $` //匹配字符串之后的字符串
    + $0-9  //匹配第n个捕获组
    + function(arguments){}
    
```js
var str = 'aabbccddee';
str.replace(/(bb)(cc)/g, function(){
    console.log(arguments);
    // 0 : bbcc
    // 1 : bb
    // 2 : cc
    // 3 : 2 
    // 4 : aabbcxdsee
    //
})
```
- split
    - 分割符号
    - 长度

#### 操作方法
- concat string.concat(values, ....)
- slice(start, end)
- substring(start, end)
- substr(start, end)
- trim()
- trimLeft()
- trimRight

#### 编码方法
- escape()
- unescape()
- encodeURI()
- decodeURI()
    - URL标识不会被编码
    - 如： htt:// => http://
- encodeURIComponent()
- decodeURIComponent()
    - 对整个URI都编码了
    - 如： htt:// => http%3A//

#### 转换方法
- toLowerCase()
- toUpperCase()
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
