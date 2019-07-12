# React 生命周期

- https://zh-hans.reactjs.org/docs/react-component.html

- http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/

## 第一次

### constructor

- 如果不初始化 state 或不进行方法绑定，则不需要为 React 组件实现构造函数。

通常，在 React 中，构造函数仅用于以下两种情况：

- 通过给 this.state 赋值对象来初始化内部 state。
- 为事件处理函数绑定实例

### getDerivedStateFromProps

- 会在调用 render 方法之前调用，并且在初始挂载及后续更新时都会被调用。它应返回一个对象来更新 state，如果返回 null 则不更新任何内容。

### render

### componentDidMount

- 会在组件挂载后（插入 DOM 树中）立即调用。依赖于 DOM 节点的初始化应该放在这里。如需通过网络请求获取数据，此处是实例化请求的好地方。

## 再次渲染

### getDerivedStateFromProps

- 在最近一次渲染输出（提交到 DOM 节点）之前调用。它使得组件能在发生更改之前从 DOM 中捕获一些信息（例如，滚动位置）。此生命周期的任何返回值将作为参数传递给 componentDidUpdate()。

### shouldComponetUpdate

### render

### getSnapshotBeforeUpdate

- 在最近一次渲染输出（提交到 DOM 节点）之前调用。它使得组件能在发生更改之前从 DOM 中捕获一些信息（例如，滚动位置）。此生命周期的任何返回值将作为参数传递给 componentDidUpdate()。

### componentDidUpdate

- 当组件更新后，可以在此处对 DOM 进行操作。如果你对更新前后的 props 进行了比较，也可以选择在此处进行网络请求。

## 卸载

### componentWillUnmount

## 错误处理

### getDerivedStatrFromError

### componentDidCatch
