---
title: js设计模式
date: 2017-03-29 11:18:44
tags:
    - js
    - 设计模式
commit: false
cetegaries: js
---
### 设计模式
> 让系统代码可重用 可扩展 可解耦 更容易 被理解 且保证代码的可靠性
#### 原则
- 开闭原则：对扩展开发 对修改关闭
- 里氏转换原则：子类继承父类，单独调用完全可以运行
- 依赖倒转原则：引用一个对象 如果这个对象有底层类型，直接引用底层
- 结构隔离原则：每一个接口应该是一中角色

#### 单例模式
- 一个类只有一个实例
- 有就返回 没有就初始化
- 单例作为命名空间的提供者
<!--more-->

```js
var single = (function (){
      var unique;
      function init(){
          //单例代码
          //私有方法 变量
          var privateVariable = 'something private';
          return {
              publicMethod: function() {
                  console.log('hello world')
              },
              publicVariable: 'test'
          }
      };
      
      return {
          getUnique: function() {
            if(!unique){
                unique = init()
            }
            return unique
          }
      }
  })();
```

#### 工厂模式
- 不同参数生成不同子类
- switch type
- 配置文件

```js
var Car = (function() {
    var Car = function(model, year, miles){
        this.model = model;
        this.year = year;
        this.miles = miles;
    };
    return function(model, year, miles) {
        return new Car(model, year, miles)
    }
})();
var pageDmo = {};
pageDmo.Text = function() {
  return 'this is text type'
};
pageDmo.Link = function() {
  return 'this is link type'
};
pageDmo.Image = function() {
  return 'this is image type'
};

pageDmo.factory = function(type) {
    return new pageDmo[type]
};
var o = pageDmo.factory('Link'); //'this is link type'
```
#### 代理模式
- 委托 代理 中间件 proxy

```js
var Girl = function(name) {
    this.name = name 
}
var Boy = function(girl) {
    this.girl = girl 
    this.sendGift = function(gift) {
        alert('hi'+this.girl+', boy send you '+ gift);
    }
}

var Proxy = function(girl) {
    this.girl = girl;
    this.sendGift = function(gift) {
        (new Boy(girl).sendGift(gift))
    }
};

var proxy = new Proxy(girl('name'));
proxy.sendGift('6666礼物')
```

#### 观察者模式
- 订阅发布模式 publish/subscribe
- 一对多的关系
- 观察者订阅xx消息类型接受发布数据
- 发布消息xx类型和数据 执行观察者订阅

```js
// 订阅者数组arr[]
// sub订阅的时候 arr.push({token, func})
//发布的时候循环数组执行 订阅者的回调函数
//取消订阅通过token

var subpub = {};
(function(q) {
    var topics= {}; //消息类型对象 下面存放对着订阅者数据
    // {
    //    type: [
    //      {token: 0, func: callback}
    //    ]
    // }
    var subUid = -1;
    //发布方法
    q.pub = function(topic, args) {  //发布消息类型和数据
      if(!topics[topic]){  //如果没有这个订阅这个消息的return
          return false
      }
      setTimeout(function() {
        var subs = topics[topic],
            len = subs ? subs.length : 0;   //有几个订阅者
            while(len--){
                subs[len].func(topic, args)  //执行订阅者的方法(消息类型，数据)
            }
      }, 0)
      return true;  //发布成功
    };
    q.sub = function(topic, callback) { //订阅消息 消息处理函数
      if(!topics[topic]){  //如果没有这个消息
          topics[topic]= []  //新建立一个
      }
      
      var token = (++subUid).toString();
      
      topics[topic].push({  //topic消息类型下 有多个订阅者  订阅者的token不同 且唯一
          token: token,
          func: callback
      })
      return token; //返回id  取消订阅用
    }
    
    q.unsub = function(token) {  //退订 遍历所有的订阅者 找到对应token删除
        for(var m in topics){
            if(topics[m]){  //如果有订阅者
                for(var i = 0, j = topics[m].length; i < j; i++){
                    if(topics[m][i].token == token){
                        topics[m].splice(i, 1);  //找到删除
                        return;  //退出
                    }
                }
            }
        }
    }
})(subpub)

```
