---
title: React
date: 2017-02-21 19:38:39
tags:  
    - React
commit : false
categories: React

---
###  组件生命周期
- 挂载：组件被插入DOM
    - getInitialState() 初始化state
    - componentWillMount() 即将被挂载
    - componentDidMount() 组件挂载 DOM操作在这里
- 更新：
    - componentWillReciveProps(object nextProps) 挂载组件接收新的props
    - shouldComponentUpdate(object nextProps, object nextState)
        - 比较 nextPorps 和 this.props
        - 比较 nextState 和 this.state
        - 返回 false 的话不更新DOM
    - componentWillUpdate(object nextProps, object nextState)
        - 这里可以调用this.setState({name: value})
    - componentDidUpdate(object prevProps, object prevState)
        - 组件更新之后
- 移除
    - componentWillUnmount()
        - 组件移除和销毁之前，这边做清理工作，如定时器

<!--more-->
### 组件不可用ref, key关键字做为属性
- ref， key 关键字
- 组件引用设置ref="exampleRef"
   - 父组件可引用
- 组件内部实现ref="insetRef"
    - 组件内部使用

### this.props.children  
- 路由下面所有的子路由包含的子节点
- 每个路由下都对应个页面

```js
// root/index.js  App入口
<div>
    <Header />
    <Toast />
    <Alert />
    {this.props.children}
    <Footer />
</div>

//or
{children && React.cloneElement(children, {
    key: location.pathname,
    showToast,  //action
    loading,    //action
    getJumpUrl
})}
```


### react-router 代码按需加载
- webpack 配置
    - name chunk 指定的名字, 未指定默认分配 id 作为 name。
    - chunkhash:5 是文件的 hash 码，这里只使用前五位
```
output:{
    path: path.join(__dirname, '../dist/assets',
    filename: 'app.js'
    publicPath: defaultSetting.publicPath,
    chunkFileName: '[name].[chunkhash:5].chunk.js'
}
```

- 提出route
    - path
    - require.ensure(dependencies, callback, chunkName)
    - es6写法中 module.exports 需要在cb后面加.default
```js
const rootRoute = (store)=>{
    return
    <Route>
        <Route path="/home" getComponent={(nextState, cb) => {
            require.ensure([], (require) => {
                cb(null, require('./components/home')).default
            })
        }} />
    </Route>
}

ReactDom.render(
    <Roter 
        history={browserHistory}
        routes = {rootRoute}
     />
)

```
## react

## redux
- 管理状态state树
- action 带数据的动作
- reducer 根据action更新state树re
- store 接收reducer和初始数据 关联 action 和 reducer
- 拆分reducer 对应应用分支 然后用combineReducers()合并
### store
- 会把当前的state树和action传递给reducer
- store.getState()
- store.dispatch(action)
- store.subscribe(listener)

```js
import {createStore} from 'redux'
import rootReducer from './reducers'
let stroe = createStore(rootReducer, window.__initData__)

```

## react-redux
    