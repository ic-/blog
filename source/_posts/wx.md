---
title: wx小程序
date: 2017-02-22 11:02:12
tags:
    - wx小程序
---
### Appid 获取
```js
1.申请账号
2.找企业认证信息
```
### 文档
[wx小程序](https://mp.weixin.qq.com/debug/wxadoc/dev/)
### 文件结构
```js
app.js
app.json
app.wxss
pages
    home
        1. xx.js js
        2. xx.json 配置信息
        3. xx.wxss css
        4. xx.wxml html

```
<!-- more -->
### 配置信息
```js
app.json
    1.pages 路由 required
    2.windows 小程序的状态栏、导航条、标题、窗口背景色。
    3.tabBar 设置底部 tab 的表现
    4.networkTimeout 设置网络超时时间
    5.debug
pages
    home
        1.home.json
```

### 逻辑层
1.注册程序
```js
app.js [once]
App({
    onLunch:function(){},
    onShow:function(){},
    onHide:function(){},
    onError:function(){},
    any[any typeof]
})
```

2.注册页面
```js
pages/home/home.js
var app = getApp(); //获取app实例
Pages({
    data,
    onLoad,
    onReady,
    onShow,
    onHide,
    onUnload,
    onPullDownRefresh,
    onReachBottom,
    onShareAppMessage,
    any
})        
setData({}) //更新数据
```
3.页面生命周期
```text
onLoad: 页面加载
    一个页面只会调用一次。
    接收页面参数可以获取wx.navigateTo和wx.redirectTo及<navigator/>中的 query。

onShow: 页面显示
    每次打开页面都会调用一次。
    
onReady: 页面初次渲染完成
    一个页面只会调用一次，代表页面已经准备妥当，可以和视图层进行交互。
    对界面的设置如wx.setNavigationBarTitle请在onReady之后设置。详见生命周期

onHide: 页面隐藏
    当navigateTo或底部tab切换时调用。

onUnload: 页面卸载
    当redirectTo或navigateBack的时候调用。
```
4.页面路由
```js
wx.navigateTo()
wx.redirectTo()
wx.navigateBack()
wx.switchTab()
```
5.模块化
```js
module.export.sayHello = function(){}
var sayHello = require('./sayHello.js')
```
6.API

### 视图层
1.数据绑定
```js
//1.属性在双引号内 ""
//2.变量在双大括号内{{}}
//3.关键字在双引号内 "{{true/false}}" "false":为字符串

<view>{{message}}</view>
<view id="item-{{id}}" ></view>
<view wx:if="{{condition}}"></view>
<view checked="{{true/false}}"></view>
<view hidden="{{flag?true:false}}"></view>

```
2.条件渲染
```js
1.wx:if 惰性为false不渲染 hidden都渲染
```

3.列表渲染
```js
1. for不提供wx:key报warming
<view wx:for="{{array}}">{{index}}{{item.message}}</view>
<view wx:for="{{array}}" wx:for-index="idx" wx:for-item="itemName">{{idx}}:{{itemName.message}}</view>
```
4.模板
```js
// 1.定义模板
<template name="msgItem">
    <view>{{index}}: {{msg}}</view>
    <view>Time: {{time}}</view>
</template>
// 2.调用模板
// 模板拥有自己的作用域，只能使用data传入的数据。
Page({
    data: {
        item: {
            index: 0,
            msg: 'this is template',
            time: '2017-01-11'
        }
    }
})
<template is="msgItem" data="{{..item}}"></template>
```
5.事件
```js
1.冒泡事件和非冒泡事件
    冒泡事件： touchstart touchmove touchcancel touchend tap longtap
    非冒泡事件：剩下的都是
2.事件绑定
    bind+事件名称: bindTap 不会阻止事件冒泡
    catch+事件名称: catchTap 会阻止事件冒泡
3.事件对象
    1.baseEvent 基础事件对象属性：
        - type
        - timeStamp 时间戳
        - target 触发事件的组件的一些属性值集合
        - currentTarget 当前组件的一些属性值集合
    2.customEvent 自定义事件属性列表
        - +detail 额外的信息
    3.TouchEvent 触摸事件属性
        - +touchs 触摸事件，当前停留在屏幕中的触摸点信息的数组
        - +changeTouchs 触摸事件，当前变化的触摸点信息的数组
    4.特殊事件： <canvas/> 中的触摸事件不可冒泡，所以没有 currentTarget。
    
    <view data-alpha-beta="1" data-alphaBeta="2" bindTap="bindViewTap">Dataset test</view>
    Page({
        bindViewTap: function(event){
            event.target.dataset.alphaBeta === 1 //-会转为驼峰
            event.target.dataset.alphabeta === 2 //大写会转为小写
        }
    })
```
6.引用
```js
1.import 引入<template> 使用
2.include 除<template>标签 整个代码引入
```
### wxss
1.尺长单位：rpx可以根据屏幕宽度进行自适应。
2.样式倒入： @import "common.wxss";
3.内联样式： <view style="clolr:{{color}}" class="normal_view"></view>
4.选择器：.class #id element(所有的view组件) element,element（element, checkbox） ::after ::before
5.全局样式与局部样式 app.wxss 全局 pages/xx/xx.wxss 局部样式