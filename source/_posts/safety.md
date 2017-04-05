---
title: XSS和CSRF攻击
date: 2017-04-05 11:32:59
tags:
    - js
commit: false
categories: js
---

#### XSS和CSRF跨站攻击
- 不攻击服务器攻击用户信息

##### XSS
- 预期之外的js脚本输入
- 过滤用户输入，用户的输入是不可信的
- 对一些关键字和特殊字符进行过滤或 URL、HTML 编码，"<>?"或"script，javascript"；

##### CSRF
- 跨站请求伪造
- 创建一个唯一的令牌（Token），将其存在服务端的session中及客户端的cookie中，对任何请求，都检查二者是否一致。
- token不对让他去登陆