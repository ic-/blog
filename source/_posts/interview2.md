---
title: interview2
date: 2017-03-08 09:25:32
tags:
    - interview
common: false 
categories: 面试
---


1.ajax?
- 异步传输
- 创建个XMLHttpRequest对象 
- 创建一个http请求
- 设置http响应参数变化的函数
- 发送http请求
- 获取异步返回结果
- 更新

<!--more-->

```js
funtion Ajax(url, fnSuc, fnFail) {
    if(window.XMLHttpRequest){
        var oAjax = new XMLHttpRequest()
    }else{
        var oAjax = new ActiveObject('Microsoft.XMLHTTP');
    }
    
    oAjax.open('get', url, true);
    oAjax.send();
    
    oAjax.onreadystatechange = function() {
        if(oAjax.readyState == 4){
            if(oAjax.status >= 200 && oAjax.status < 300 || oAjax.status == 304){
                fnSuc(oAjax.responseText)
            }else{
                fnFail()
            }
        }
    }
}
```
2.ajax解决缓存问题
- oAjax.setRequestHeader('If-modified-Since', '0')
- oAjax.setRequestHeader('Cache-control', 'no-cache')
- url后加随机数 't='+Math.random()
- url后加时间戳 'nowTime='+ new Date().getTime();

3.同步和异步的区别？

4.解决跨域问题?
[如何解决跨域问题](2017/03/24/jsonp/)

5.页面编码和请求资源的编码不一致？
- 设置请求编码格式
    - <script src="xxx/xx.js" charset="utf-8" />

6.模块化开发怎么做？
- 样式模块化
    - 基础reset
    - variables mixin(flex ellipsis)
    - font color bg spacing grid 
    - button iconfont loading animation border 
    - 页面单独样式+基础样式
    
- ui组件模块化
- 公用组件模块化
- 基础网络 路由 开发环境

7.AMD 和 CMD?
- AMD 依赖一开始就写好
    - 和node一致 更友好写 更清晰
- CMD 可就近依赖

8.requirejs的核心？
- 正则分析依赖 递归出所有依赖
- 检查是否有缓存 
    - 有缓存用缓存
        - 执行回调
    - 没有缓存
        - 动态创建script 添加
        - 监听script load 完成后
        - 执行回调
9.ECMAScript 的了解？
- 新增很多功能
    - 用到的 const let  symbol 
    - 字符串模板 解构 展开 箭头函数 
    - promise class module
    - class
```js
class Point {
    constructor(x, y){
        this.x = x;
        this.y = y;
    }
    toString(){
        return ('('+ thihs.x +':'+ this.y+')')
    }
}
class ColorPoint extends Point{
    constructor(x, y, color) {
        super(x, y); // 调用父类的constructor(x, y)
        this.color = color;
    }

    toString() {
        return this.color + ' ' + super.toString(); // 调用父类的toString()
    }
}
```
- 使用新功能要用转码器
    - babel

10.异步加载JS的方式有哪些？
- defer
    - document.onload
    - 执行顺序固定
- async
    - 异步
    - 执行顺序不固定
- 动态创建 script 插入

11.document.write 和 innerHMLT?
- document.write 复写整个页面
- innerHTML 复写局部

12.call apply?
- fn.call(obj, arg1, arg2, arg3, ...)
- fn.apply(obj, [args])

13.js的变量提升和作用域?
- 变量提升: 预解析 执行到后在复制
- 没有块级作用域 只有函数作用域

14.那些操作会照成内存泄露？
- 应用程序占用内存 由于某些原因 内存不回收
- 回收机制 mark-and-sweep
    - 回收机制检查全局变量
    - 对象是激活状态 不被回收
    - 非激活被回收
- 闭包 不回收
- 意外的全局对象
    - 没有var 直接 this.variables = '11111';
    - 严格模式解决： 'use strict' 
- 循环引用
    - react 在render 或者 componentDidUpDate 更新state 

chrome 可看内存泄露 timeline

15.JQuery的源码看过吗？能不能简单概况一下它的实现原理？
- 看过 
- jquery 建立了一整套高效的选择器
- 选择器 sizzle 返回选择数组对象
- 每个方法内部 循环调用数组
- 执行完成后 又返回数组对象 实现链式调用

16.Zepto的点透问题如何解决？
- 用tap时间 有npm包

17.mvc mvp mvvm?
[MVC，MVP 和 MVVM 的图示](http://www.ruanyifeng.com/blog/2015/02/mvcmvp_mvvm.html)

18.前端路由？适用范围？ 优缺点？
- 根据不同的url 显示不同的页面 内容
- 单页应用
- 其实路由做的好 大部分都可以适用
- 用户体验好 

19.前端模板？
- 快速展示view结合data

20.检测浏览器版本?
- navigator.userAgent
- 功能检测

21.What is a Polyfill?
- 在旧的浏览器上复制标准的Api的js补充
- html5shiv Placeholder

22.事件冒泡 和事件捕获
- addEventListener(fn, dom, true/false)
    - true 捕获 - 外到内
    - false default 冒泡 - 内到外
    - 先一路捕获下去，然后一路冒泡上来

```js
//div>span   
 div.addEventListener('click', function(){  //捕获
     console.log(11111)
 }, true);
 div.addEventListener('click', function(){ //冒泡
     console.log(22222)
 }, false);
 span.addEventListener('click', function(){  //捕获
     console.log(33333)
 }, true);
 span.addEventListener('click', function(){ //冒泡
     console.log(44444)
 }, false);

// 11111 3333 4444 2222
```

1.原来公司工作流程是怎么样的，如何与其他人协作的？如何夸部门合作的？
- 项目立会 产品会出原型 ui前端后端 过一下原型 看有没有什么问题 互相沟通下
- 了解业务流程后 
    - 前端技术选型
        - 比较成熟的是
            - 移动端 webpack + react + redux + nodejs 
            - pc端 nodejs + jquery+gulp+requirejs
            - 看具体项目需求
    - 服务端定开发接口
        - mock 平台
        - 接口规范
    - 项目部署平台
        - 开发文档 sdk 
        - 公用模块依赖
    - ui设计稿
        - sketch 
        - svg 图标
        - iconfont 阿里
    - 开发
        - 本地用Mock/测试环境数据
        - 开发文档
        - readme.md
    - 联调
    
    - 提测/bug修改
        - 优化 按需加载 
        - 打包体积
        - 合并请求
        - 静态资源cdn
    - 部署 
        - 自动化部署
        - node 内网地址访问 
        
23.你遇到过比较难的技术问题是？你是如何解决的？
- 代理-cookie 
    - 用anyproxy代理

- 设计模式
[设计模式](2017/03/29/design)
- 排序
[排序](2017/03/29/arrSort)
- http 
[http](2017/02/20/http)













