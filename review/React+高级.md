# React 高级

## 无障碍辅助功能

### aria-*

### 语义化标签

- 无意义的 div 可以使用组件 React.Fragment 或短语法代替

React.Fragment
```javascript
class Columns extends React.Component {
  render() {
    return (
      <React.Fragment>
        <td>Hello</td>
        <td>World</td>
      </React.Fragment>
    );
  }
}
```

短语法
```javascript
class Columns extends React.Component {
  render() {
    return (
      <>
        <td>Hello</td>
        <td>World</td>
      </>
    );
  }
}
```


### 表单

### 焦点

### 语言

### 色彩对比度

## Context

- Context 提供了一个无需为每层组件手动添加 props，就能在组件树间进行数据传递的方法。

### 场景

- 地区偏好，UI 主题

### 思考

- 如果你只是想避免层层传递一些属性，组件组合（component composition）有时候是一个比 context 更好的解决方案。

## 错误边界

### React 16

- 自 React 16 起，任何未被错误边界捕获的错误将会导致整个 React 组件树被卸载。

- 在开发环境下，React 16 会把渲染期间发生的所有错误打印到控制台，即使该应用意外的将这些错误掩盖。除了错误信息和 JavaScript 栈外，React 16 还提供了组件栈追踪。

### 定义

- 是一种 React 组件

- 可以捕获并打印发生在其子组件树任何位置的 JavaScript 错误，并且，它会渲染出备用 UI，而不是渲染那些崩溃了的子组件树。

- 错误边界在渲染期间、生命周期方法和整个组件树的构造函数中捕获错误。


### 场景

错误边界无法捕获以下场景中产生的错误：

- 事件处理（了解更多）
- 异步代码（例如 setTimeout 或 requestAnimationFrame 回调函数）
- 服务端渲染
- 它自身抛出来的错误（并非它的子组件）

## Refs 转发

### 定义

- Ref 转发是一项将 ref 自动地通过组件传递到其一子组件的技巧

- React.forwardRef 

- React.createRef()，React 16.3 引入

```javascript
const FancyButton = React.forwardRef((props, ref) => (
  <button ref={ref} className="FancyButton">
    {props.children}
  </button>
));

// 你可以直接获取 DOM button 的 ref：
const ref = React.createRef();
<FancyButton ref={ref}>Click me!</FancyButton>;
```

### 场景

- 对于大多数应用中的组件来说，这通常不是必需的。但其对某些组件，尤其是可重用的组件库是很有用的。

### 注意

- 当你开始在组件库中使用 forwardRef 时，你应当将其视为一个破坏性更改，并发布库的一个新的主版本。

## Fragments

- Fragments 允许你将子列表分组，而无需向 DOM 添加额外节点。

```javascript
render() {
  return (
    <React.Fragment>
      <ChildA />
      <ChildB />
      <ChildC />
    </React.Fragment>
  );
}
```

## 高阶组件

- 高阶组件是参数为组件，返回值为新组件的函数

### 特性

- HOC 不会修改传入的组件，也不会使用继承来复制其行为

- HOC 是纯函数，没有副作用。

### 注意

- 不要试图在 HOC 中修改组件原型（或以其他方式改变它）

- HOC 应该透传与自身无关的 props。

- 不要在 render 方法中使用 HOC

- 务必复制静态方法

- Refs 不会被传递

## Portals

### 作用

- Portal 提供了一种将子节点渲染到存在于父组件以外的 DOM 节点的优秀的方案。

### 特点

- 一个从 portal 内部触发的事件会一直冒泡至包含 React 树的祖先，即便这些元素并不是 DOM 树 中的祖先

## Diff 算法

React 在以下两个假设的基础之上提出了一套 O(n) 的启发式算法：

- 两个不同类型的元素会产生出不同的树；

- 开发者可以通过 key prop 来暗示哪些子元素在不同的渲染下能保持稳定；


Diff 算法：
1. React 首先比较两棵树的根节点。
   1.1 当根节点为不同类型的元素时，React 会拆卸原有的树并且建立起新的树。

2. 比对同一类型的元素，React 会保留 DOM 节点，仅比对及更新有改变的属性。


在处理完当前节点之后，React 继续对子节点进行递归。

对子节点进行递归：
- 当递归 DOM 节点的子元素时，React 会同时遍历两个子元素的列表；当产生差异时，生成一个 mutation。但这种方式会带来低效问题，为此使用了 key 属性，通过 key 的比较进行相关操作，有移动、增加、删除。

## Refs and the DOM

- Refs 提供了一种方式，允许我们访问 DOM 节点或在 render 方法中创建的 React 元素。

### 场景

- 管理焦点，文本选择或媒体播放。
- 触发强制动画。
- 集成第三方 DOM 库。

### ref 

ref 的值根据节点的类型而有所不同：

1. 当 ref 属性用于 HTML 元素时，构造函数中使用 React.createRef() 创建的 ref 接收底层 DOM 元素作为其 current 属性。

2. 当 ref 属性用于自定义 class 组件时，ref 对象接收组件的挂载实例作为其 current 属性。

3. 你不能在函数组件上使用 ref 属性，因为他们没有实例。

## Render Props

### 定义

- 术语 “render prop” 是指一种在 React 组件之间使用一个值为函数的 prop 共享代码的简单技术

- 更具体地说，render prop 是一个用于告知组件需要渲染什么内容的函数 prop。


### 注意

将 Render Props 与 React.PureComponent 一起使用时要小心

- 如果你在 render 方法里创建函数，那么使用 render prop 会抵消使用 React.PureComponent 带来的优势。因为浅比较 props 的时候总会得到 false，并且在这种情况下每一个 render 对于 render prop 将会生成一个新的值。

## 严格模式

### 作用

- StrictMode 是一个用来突出显示应用程序中潜在问题的工具。与 Fragment 一样，StrictMode 不会渲染任何可见的 UI。它为其后代元素触发额外的检查和警告。

### 好处

- 识别不安全的生命周期
- 关于使用过时字符串 ref API 的警告
- 关于使用废弃的 findDOMNode 方法的警告
- 检测意外的副作用
-检测过时的 context API
