# Redux

- https://www.redux.org.cn/

## 动机

- 让状态可控，可预测，方便管理

- 跟随 Flux、CQRS 和 Event Sourcing 的脚步，通过限制更新发生的时间和方式，Redux 试图让 state 的变化变得可预测。

## 三大原则

### 单一数据源

- 整个应用的 state 被储存在一棵 object tree 中，并且这个 object tree 只存在于唯一一个 store 中。

### State 是只读的

- 唯一改变 state 的方法就是触发 action，action 是一个用于描述已发生事件的普通对象。

### 使用纯函数来执行修改

- Reducer 只是一些纯函数，它接收先前的 state 和 action，并返回新的 state

## 概念

### Action

- 是把数据从应传到 store 的有效载荷。它是 store 数据的唯一来源。一般来说你会通过 store.dispatch() 将 action 传到 store。

- Action 创建函数就是生成 action 的方法。“action” 和 “action 创建函数” 这两个概念很容易混在一起，使用时最好注意区分。


### Reducers

- 指定了应用状态的变化如何响应 actions 并发送到 store 

- 在没有得到 state 副本前，不要修改 state

永远不要在 reducer 里做这些操作：
- 修改传入参数；
- 执行有副作用的操作，如 API 请求和路由跳转；
- 调用非纯函数，如 Date.now() 或 Math.random()。

### Store

- 把它们Action和 Reducers联系到一起的对象。
-  Redux 应用只有一个单一的 store。


Store 有以下职责：
- 维持应用的 state；
- 提供 getState() 方法获取 state；
- 提供 dispatch(action) 方法更新 state；
- 通过 subscribe(listener) 注册监听器;
- 通过 subscribe(listener) 返回的函数注销监听器。
