---
title: Dom 操作
date: 2017-03-30 14:28:46
tags:
    - js
    - dom
commit: false
categories: js
---

### Dom 基本操作
#### 获取节点
- document
    - getElementById
    - getElementsByTagName
    - getElementsByName
- 节点指针
    - parentNode
    - childNodes
    - previousSibling
    - nextSibling
    - firstChild
    - lastChild
<!--more-->
#### 节点操作
##### 创建节点
- document
    - createElement
    - createAttribute
    - createTextNode
##### 插入节点
- appendChild
- insertBefore
##### 替换节点
- replaceChild
##### 复制节点
- cloneChild(true/false)
    - true 有子节点
    - false 无子节点
##### 删除节点
- removeChild
#### 属性操作
- getAttribute
- setAttribute
- removeAttribute
