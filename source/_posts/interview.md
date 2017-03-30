---
title: interview
date: 2017-03-08 09:15:32
tags:
    - interview
common: false 
categories: 面试
---
1.Doctype的作用？标准模式和兼容模式各有什么区别？
- <!Doctype> 位于html文档的第一行 告诉浏览器以什么标准解析html文档
- Doctype不存在或者格式不正确会导致文档以兼容模式呈现
- 标准模式：排版和js都以浏览器支持的最高标准运行 
- 兼容模式：页面以宽松的向后兼容的方式显示， 模拟老浏览器的行为 防止页面无法访问。
<!--more-->
2. HTML 为什么只要要写 <!DOCTYPE html>？
- HTML5 不属于SGML集合 不需要对DTD进行引用
    - SGML 标准通用语言 是个大集合 
    - DTD document type definition 
- 但是需要 doctype 规范浏览器的行为

3.行内元素 块级元素 空元素 有哪些
- 行内元素： a b span i em strong img input select
- 块级元素： h1.. div p ul ol li dl dt dd 
- 空元素： br hr img input link meta

4.样式导入link和@import的区别
- link 属于html标签 除了加载css 还能定语 rel rss
- @import 是css定义的只能提供加载css
- 页面加载时候 link会同时加载
- @import引用的css会等页面加载完成在加载
- @import ie5 以上兼容

5.介绍下浏览器内核的理解
- 主要分成2部分：渲染引擎和js引擎
- 渲染引擎负责取得网页内容 整理 计算 渲染
- js引擎负责解析执行js

6.常见浏览器内核
- trident ie 360 搜狗
- gecko ff moz
- webkit safari chrome

7.html5有哪些新特性，移除哪些元素，如何处理html5新标签浏览器兼容问题？
- 新特性： canvas video audio localStorage sessionStorage 
    - 语义化标签： article section header footer menu nav 
    - 表单控件 data time email url search
- 移除的元素： basefont big center font s
- 支持html5新元素：document.createElement 或者用成熟的框架

8.HTML语义化理解
- 用正确的标签做正确的事情
- 有利于优化css代码
- 让页面结构清晰 便于浏览器解析 搜索引擎解析
- 有利于seo 爬虫会分析html标记定语权重

9.html离线存储怎么使用
- 用户没有连接网络的时候正常访问站点和应用， 用户连接后更新用户机器上的缓存
- 基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的缓存清单离线缓存资源 这资源就像cookie一样被存储下来。
- <html lang="en" manifest="index.manifest"> 读取index.manifest

10.cookie localStorage sessionStorage的区别
- cookie 
    - 标识用户身份而存储在用户本地终端上的数据
    - 同源http请求头都会携带
    - 大小有限不能超过4k 
    - 在设置过期时间之前一直有效
- localStorage 本地永久存储 不限制大小 
- sessionStorage 会话存储 浏览器关闭后自动删除

11.iframe 有哪些确定
- iframe 会阻塞主页面的onload事件
- 搜索引擎无法解读这种页面 不利于seo
- iframe和主页面共享连接池（2，4，6）会影响页面的并行加载
- 解决：js 动态赋值 src

12.label有什么作用
- 可以设置用户选择label标签那个表单元素获取焦点

13.html关闭form自动autocomplete=off

14.实现浏览器内多个标签页直接通信
- websocket localstorge s
- localstorge另外一个浏览器上下文里被添加，修改或删除 都会触发一个事件 通过监听事件实现通信
    - 但是无痕下报错
     
15.websocket 如何兼容
- flash socket
- 长轮询的XHR

16.页面可见性(visibilityState)用途
- 监听visibilityState 检测页面是否 可操作自动播放或暂停

17.如何在页面上实现一个原型的可点击区域
- border-radius
- svg
- map+area
- 纯js实现计算

18.网页验证码干嘛的
- 防止恶意刷请求 

19.标准盒模型和低版本ie盒子模型的区别
- 标准盒模型 width = width  box-sizing=content-box的效果
- ie盒模型 width = width+padding+border box-sizing=border-box的效果
 
20.css选择符有哪些 哪些属性可以继承
- * #id .classname p  div+p div > p  div p  div:after div:nth-child() a[rel='external']
- 可继承 font-size font-family color ul li dl dd dt 
- 不可继承 border margin padding width height

21.css优先级 
- import > 标签内部 > 内部样式 > 外部样式文件
- !important > id > classname > tag > *

22.css3新增伪类
- :first-of-type
- :last-of-type
- :one-of-type
- :after
- :before
- :enable
- :checked
- :disbaled

23.div如何居中
- margin: 0 auto 水平居中
- position:absolute; left:0; top: 0; bottom: 0; right: 0;
- width: 300px; height: 300px; position:relative; left: 50%; top: 50%; margin-left: -150px; margin-top: -150px;
- position:absolute; left: 50%; top: 50%; transform: translate(-50%, -50%)
- parentNode: display:flex; item-align: center; //垂直居中 justify-content:center  //水平居中

24.display有哪些值
- display: none
- display: block
- display: inline
- display: inline-block
- display: table
- display: inherit
- display: list-item 象块类型元素一样显示，并添加样式列表标记。

25.position
- static  默认
- inherit 继承父
- absolute 相对于设置了position不为static的父级定位
- relative 相对于自身文档流位置
- fixed 相对于可视区  ie不兼容
- sticky (relative和fixed结合) 目标区域在屏幕中可见的时候 是relative效果 当目标超出滚动区域的时候
    - 吸顶效果或底部固定效果

26.css3新特性
- border-radius
- box-shadow
- text-shadow
- transform
- gradient

27.css3 flexbox

28.css创建三角形
- border 隐藏另外三个边

29.常见浏览器兼容性
- png24在ie6下显示背景，解决 png8
- 浏览器默认margin padding不同 reset
- ie6 双边距：float元素横行的margin产生双边距 解决 _display:inline
- hack
    - \9 //ie6,7,8
    - * //ie6,7
    - _ //ie6

- chrome 小于12px的字体 按照12px显示 解决 -webkit-text-size-adjust: none
- ie下获取元素属性可以直接获取 ff要用getAttribute 统一解决 getAttribute
- 超链接访问过后 hover样式不显示  l-v-h-a : a:link a:visited: a:hover a:active

30.为什么要初始化css
- 因为浏览器兼容问题， 不同浏览器对有些标签的默认值是不同的， 如果不做初始化 不同浏览器下表现会有差异
- 最简单的 *{margin: 0; padding: 0}

31.position跟display margin collapse overflow float 特性叠加
- 如果元素为display:那么元素不渲染，position float不起作用
- 如果维absolute fixed 那么float不起作用
- float 元素脱离文档流
- float absolute inline-block的元素 margin 不塌陷

32.css权重
- 相同权重 最后定义的样式会起作用

33.清除浮动
- 清除浮动 为了消除 浮动元素对布局产生的影响 浮动的元素 高度会塌陷 高度塌陷后面的内容不能正常显示
- 添加标签设置 clear:both 清除浮动
- overflow: hidden/auto; *zoom: 1;
- :after 
    - clear:both 闭合浮动 其他的为了隐藏元素 
    - zoom：1 触发IE hasLayout
```css
  .clearfix{*zoom:1} 
  .clearfix:after{clear:both; content:'', display:block; font-size:0; height: 0; visibility: hidden}
```

34.外边距合并，塌陷 
- 垂直方向 小margin回塌陷进入大margin

35.zoom:1清楚浮动的原理
- 清除浮动 触发 hasLayout
- Zoom ie 专有属性 设置检索元素的缩放比例 解决ie比较奇怪的bug
- 设置了zoom 会触发重新计算 宽高 发生重新渲染

36.移动端 媒体查询
- @media(条件)and (条件){ 当前条件下使用的样式}

37.css预处理器
- less 组内用的less
- sass sass功能会强大些

38.css优化，提高性能的方法
- 选择器的优化 
- 样式顺序的优化
- 提取变量（颜色 字体大小 动画 等） 基础样式（margin padding flex clear等） ui组件 
- 如果有统一的ui规范 做好基础规范 用统一的规范 保证视觉效果的一致性
- 使用构建工具 打包压缩 自动添加前缀

39.浏览器是怎么解析css的
- 从左往右 就近原则

40.网页中用奇数还是偶数字体
- 偶数 会好些  居中  如果有比例计算的话

41.margin 和padding的使用场景
- margin是用来分隔元素与元素 padding分隔元素与内容的
- 有border 有background的时候

42.抽离样式模块怎么写，说出思路，有无实践经验？
- 1.我们一般会用sass或者less先抽离出所有变量 如颜色 字体大小 主题风格 网站字体 为单独的文件
- 2.我们还会按属性 抽离出不同的 模块  如果 margin和padding  border 公用ui模块 字体图标模块
- 3.当要用这些的模块的就@import 引入  字体图标可以一开始在main文件引入

43.元素竖向的百分比设定是相对于容器的高度吗?
- 不是 是宽度

44.伪类和伪元素
- :before css3伪类
- ::before css3伪元素

45.chrome记住密码后自动填充表单黄色背景
```css
input:-webkit-autofill, 
textarea:-webkit-autofill, 
select:-webkit-autofill{
    background-color: rgb(250, 255, 189); /* #FAFFBD; */
    background-image: none;
    color: rgb(0, 0, 0)
}
```

46.line-height如何理解？
- 撑开高度 单行可做居中

47.设置元素浮动后display的值？
- display: blcok

48.chrome支持12px的字体？
- 图片
- 最小使用12px的字体
- 设置-webkit-text-adjust: none
    - chrome低版本 27以下有效
    - 对中文无效
- 用transform

49.字体清晰变细？
- -webkit-font-smoothing: antialiased;

50.手写动画执行时间？
- requestAnimationFrame
- 60Hz  1000s/60 = 16.7ms

51.display:inline-block 会显示间隔？
- 删除空格 font-size: 0

52.overflow: scroll时不能平滑滚动的问题怎么处理？
- -webkit-overflow-scrolling: touch;

53.cookie隔离？
- 静态资源放在主域名下 那么请求静态资源会带上cookie 浪费流量
- cookie有域限制 因此不能跨域提交请求，所以使用非主要域名的时候 请求头中不会带有cookie

54.js数据类型
- 基本类型 undefined unll string number boolean
- 2015 新增symbol 创建后独一无二不可变
- 引用类型：堆（对象数组）

55.js内置对象
- Object 所有对象的父对象
- 数据类型封装对象 Object Array Boolean Number String 
- 其他对象： Function RegExp Math Date Error Anguments

56.js写法的基本规范？
- 不要再一行声明多个变量
- 用===/!==比较
- 字面量 代替 new Array
- 不要使用全局变量
- switch 必须带有 default
- 函数输出要一致

57.js原型链
- 当我们访问一个对象的属性方法的时候，如果对象不存在 那么它会顺着原型链一直往上找到 Object.prototype
还没有的话返回null
- 对象实例没有prototype 只有指针指向构造函数的 prototype
- 构造函数的原型改变会影响所有的对象实例

58.继承
- 原型链继承
```js
//新建实例 作为原型对象 效率会低一些
function Parent(){}
function Child(){}
Child.prototype = new Parent()
Child.prototype.constructor = Child
```
- 原型继承
```js
//只是移动child.prototype 的指针指向Parent.prototype 
//缺点 修改Children.prototype 会影响 Parent.prototype
function Parent(){};
function Child(){};
Child.prototype = Parent.prototype
Child.prototype.constructor = Child
```

- 临时构造函数
```js
function Parent(){};
function Child(){};
var F = function(){};
F.prototype = Parent.prototype;
Child.prototype = new F();
Child.prototype.constructor = Child;

function extend(Parent, Child) {
    var F = function(){}
    F.prototype = new Parent();
    Child.prototype = F.prototype;
    Child.prototype.constructor = Child;
    Child.uber = Parent.prototype;
}
```
- 属性拷贝
```js
function extend2(Parnet, Child) {
    var p = Parnet.prototype;
    var c = Child.prototype;
    for(var i in p){
        c[i] = p[i]
    }
    c.uber = p
}
```

58.js作用域链？
- 局部函数可以查看上层函数的细节 上层函数 无法直接访问局部函数细节

59.this的理解
- 有new的话 this指向new的对象实例
- 定时器的话都是window
- 事件this指向发生事件的对象
- 方法 this 指向调用方法的对象
- 其他 window
- 箭头函数 this 总是指向定义时所在的对象，而不是运行时所在的对象。

59.eval?
- 把字符串解析成js执行

60.window和document
- window 浏览器窗口
- document html稳定对象

61.null 和 undefined
- null 空对象
- undefined 变量没有初始化

62.阻止冒泡
- ev.stopPropagation()
- event.cancelBubble = true

63.闭包？
- 能读取其他函数的内部变量的函数
- 因为只有子函数才能读取 局部变量：所以也可以理解为定义在函数内部的函数
- 参数变量不会呗垃圾回收机制回收

64.use strict
- 严格运行模式 
- 糟糕特性无法使用： with 不能赋值全局变量 代码块内不能声明函数

65.判断一个对象属于一个类
- instanceof

66.new 操作符到底干嘛了？
```js
var obj = {}
obj.__prototype__ = Base.prototype;
Base.call(obj)
```

67.js延迟加载？
- defer和async 
    - defer html结构加载完成后才加载
    - async 异步加载加载完成后马上执行
- 动态创建DOM
- 按需加载





