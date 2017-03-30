---
title: 如何解决跨域问题？
date: 2017-03-24 10:41:55
tags:
    - js
	- 跨域
commit: false
categories: 
	- js
---

#### jsonp
- 创建script+callbackName + window.callbackName(data)

#### document.domain + iframe
- documet.domain 只适合不同子域名的框架之间
	- www.example.com/a.html
	- example.com/b.html 
- a/b 都加上 document.domain = 'example.com' 就可以访问了

```js
//a.html 
// <iframe src="http://example.com/b.html "></iframe>
doucument.domain  = 'example.com'
var iframe = document.getElementByTagName('iframe')[0];
var win = iframe.contentWindow;
var document = wind.document; //可以访问
var name = wind.name; //可以访问不到

//b.html
doucument.domain  = 'example.com'
```
<!--more-->
#### window.name + iframe
- window.name 特殊属性 
- 一个窗口(window)的生命周期内 窗口内载入的所有页面都共享window.name 
- 每个页面都能读写 window.name
- 数据必须是字符串
```js
// a.html
// <iframe src="xxx/b.html"></iframe>
alert(window.name) //我是页面b设置的数据 给a页面用

//b.html
window.name = '我是页面b设置的数据 给a页面用'
```

#### html5 window.postMessage + iframe
- window.postMessage(message, targetOrigin)
	- targetOrigin 页面域 或者不限定
		 - 限定: http://www.jd.com
		 - 不限定: \*
- 可以向其他window()发送信息
- window.onmessage 监听别人发送的信息
- 没有同源限制
```js
// a.html
// <iframe src="xxx/b.html"></iframe>
window.onmessage = function(e){
    console.log(e.data); //获取a页面的window 给a页面 发送数据
}
// b.html 
var win = window.parent;
win.postMessage('获取a页面的window 给a页面 发送数据', *)
```
#### CORS
- 服务端设置 允许域和允许方法
- 默认持GET/POST方式
- 设置支持的方法 
- ie8 不支持XDR特别的😄 但是ie11又不支持了
```js
res.setHeader('Access-Control-Allow-Origin', '*')
res.setHeader('Access-Control-Allow-Methods', 'PUT, GET, POST, DELETE, HEAD, PATCH')

```



















