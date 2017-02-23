---
title: express
date: 2017-02-22 11:45:30
tags: 
    - node
    - express
categories: node
commit: false
---
### express
[express](http://www.expressjs.com.cn/)

[中文API](http://expressjs.jser.us/api.html#express)

### 快速生成应用骨架
```
npm install express-generator -g
express myapp
```
<!--more-->
### Api

##### 入口
```
var express = require('express')
var app = express()
```

##### express.static
- 是 Express 内置的唯一一个中间件,负责托管 Express 应用内的静态资源。
```
app.use(['/path'], express.static('public', [options]))
```

##### Application
###### 处理请求
```javascript
app.get('/', function(req, res){
    res.send('hello world');
});
app.listen(3000);
```

###### app.local.variables
- 类似全局变量
- app.local.title = 'my app'
- app.local.strftime = require\(“strftime”\)
###### app.mountpath
###### app.set\(name, value\)
###### app.get\(name\)
```js
app.set('title', 'my site')
app.get('title')
//=>my site
```
###### app.enable\(name\) //set name = true

###### app.disable\(name\) //set name = false

###### app.enabled\(name\)
- name 是否启用
```javascript
app.enabled('trust proxy')
//=> false
app.enable('trust proxy')
app.enabled('trust proxy')
//=> true
```
###### app.disbaled\(name\)
- name 是否禁用
```javascript
app.disabled('trust proxy')
//=> true
app.enable('trust proxy')
app.disabled('trust proxy')
//=> false
```
###### app.configure\(\[env\], callback\)
- 当env和 app.get\('env'\) 匹配（即使 process.env.NODE\_ENV）执行callback
```javascript
//所有环境
app.configure(function(){
    app.set('title', 'My Application')
})
//开发环境
app.configure('development',function(){
    app.set('db uri', 'localhost/dev')
})
//生产环境
app.configure('production', function(){
    app.set('db uri', 'n.n.n.n/prop')
})
// 所有环境
app.set('title', 'My Application');
// 只用于开发环境
if ('development' == app.get('env')) {
    app.set('db uri', 'localhost/dev');
}
// 只用于生产环境
if ('production' == app.get('env')) {
    app.set('db uri', 'n.n.n.n/prod');
}
```

###### app.use\(\[path\], function\)
- 中间键 path默认为 '/'
```javascript
var express = require('express')
var app = express()
//一个简单的logger
app.use(function(req, res, next){
    console.log('%s %s', req.methond, req.url)
    next()
})
//响应
app.use('/static', express.static(__dirname+'/public'))
```

###### settings
- 改变 express 的行为
- 例：app.set\('trust proxy', 'loopback'\)
- env
- trust proxy
- ....

###### app.engine\(ext, callback\)
- 注册模板引擎 ext\(扩展名\) callback处理对应的模板
- app.engine\('jade', require\('jade'\).\_\_express\)
- 缓存处理 jade 后缀的 jade 模板到 require 中
```javascript
app.engine('view engine', 'pug')
//index.pug
html
    head
      title = title
    body
      h1 = message

//app
app.get('/', function(req, res){
    res.render('index', {title: 'Hey', message: 'Hello, here'})
})
```

###### app.params\(\[name\], callback\)
- 路由参数处理逻辑 尝试加载信息id为\(name的值\) 如果没有传递给next\(err\)
```javascript
app.params('user', function(req, res, next, id){
   User.find(id, function(err, user){
      if(err){
        next(err)
      }else if(user){
        req.user = user;
        next()
      }else{
        next(new Error('faild to load user'))
      }
   })
})
```
- 如果只传callback 那么就可以改变 app.params\(\) API
```javascript
app.params(function(name, fn){
  if( fn installof RegExp){
    return function(req, res, next, val){
      var captures
      if(capture = fn.exec(String(val))){
        req.params[name] = captures
        next()
      }else{
        next('route')
      }
    }
  }
})

app.params('id', /\d+$/)
app.get('/user/:id', function(req, res){
  res.send('user'+req.params.id))
})

app.params('range', /^(\w+)\.\.(\w+)?$/)
app.get('/range/:range', function(req, res){
  var range = req.params.range;
  res.send('from'+range[1]+'to'+range[2])
})
```


