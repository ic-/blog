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
        
### 组件不可用ref, key关键字做为属性
- ref， key 关键字
- 组件引用设置ref="exampleRef"
   - 父组件可引用
- 组件内部实现ref="insetRef"
    - 组件内部使用
