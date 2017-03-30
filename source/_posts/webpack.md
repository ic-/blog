---
title: webpack
date: 2017-02-27 15:35:48
tags:
    - webpack
commit: false
categories: 工具
---
### entry
```js
entry:{
    "index": ['../xxx/index.js', hotMiddlewareScript],
    "page1": ['../xxx/page1/index.js', hotMiddlewareScript]
}
```
### output
- path: 文件打包存放路径
- publicPath: 引用的文件路径
- publicPath配合node服务端
```js
webpack.js
entry: {
    indexA: ['./assets/javascripts/index.js']
}
output: {
    path: './public/dist',
    publicPath: '/assets/',
    filename: '/javascript/[name].js',
    libary
}
// server/index.js
var app = express()
app.use('/assets', express.static(path.join(__dirname, '../public/dist')));

// filename: /public/dist/javascript/indexA.js
// publicPath: <img src="/assets/logo.png" />



```