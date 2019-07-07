# React 概念

## 元素渲染

- 元素描述了你在屏幕上想看到的内容。

- 元素是构成 React 应用的最小砖块。

## 组件

- 从概念上类似于 JavaScript 函数。它接受任意的入参（即 “props”），并返回用于描述页面展示内容的 React 元素。



### class

- class 组件

```javascript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

### function

- 纯函数组件

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

## Props

- 当 React 元素为用户自定义组件时，它会将 JSX 所接收的属性（attributes）转换为单个对象传递给组件，这个对象被称之为 “props”。

### 只读

- 组件无论是使用函数声明还是通过 class 声明，都决不能修改自身的 props。


### 纯函数

- 所有 React 组件都必须像纯函数一样保护它们的 props 不被更改。

## state

- 不要直接修改 State

- 代表了随时间会产生变化的数据，应当仅在实现交互时使用

### 异步

### 合并

## 事件处理

React 元素的事件处理和 DOM 元素的很相似，但是有一点语法上的不同:

- React 事件的命名采用小驼峰式（camelCase），而不是纯小写
- 使用 JSX 语法时你需要传入一个函数作为事件处理函数，而不是一个字符串。

在 React 中另一个不同点是你不能通过返回 false 的方式阻止默认行为。你必须显式的使用 preventDefault

e 是一个合成事件。React 根据 W3C 规范来定义这些合成事件，所以你不需要担心跨浏览器的兼容性问题。

### 小驼峰式

### 传入函数

## 表单

- 在 React 里，HTML 表单元素的工作方式和其他的 DOM 元素有些不同

### textarea

- 在 HTML 中, <textarea> 元素通过其子元素定义其文本
```html
  <textarea>
  你好， 这是在 text area 里的文本
</textarea>
```
  
  
  
- 在 React 中，<textarea> 使用 value 属性代替。

### select

- 在 HTML 中，<select> 创建下拉列表标签，selected 属性表示选中
  
  
- React 并不会使用 selected 属性，而是在根 select 标签上使用 value 属性。

### 受控组件

- 使 React 的 state 成为“唯一数据源”。渲染表单的 React 组件还控制着用户输入过程中表单发生的操作。

- 推荐使用

### 非受控组件

- 表单数据将交由 DOM 节点来处理。

-  使用 ref 来从 DOM 节点中获取表单数据。

- 这类通常适用于简单表单，只需要在提交时校验

## 状态提升

- 在 React 中，将多个组件中需要共享的 state 向上移动到它们的最近共同父组件中，便可实现共享 state

## React 哲学

### 数据 state

通过问自己以下三个问题，你可以逐个检查相应数据是否属于 state：

1. 该数据是否是由父组件通过 props 传递而来的？如果是，那它应该不是 state。
2. 该数据是否随时间的推移而保持不变？如果是，那它应该也不是 state。
3. 你能否根据其他 state 或 props 计算出该数据的值？如果是，那它也不是 state。

### 组件 state

哪个组件能够改变这些 state，或者说拥有这些 state。

对于应用中的每一个 state：

- 找到根据这个 state 进行渲染的所有组件。

- 找到他们的共同所有者（common owner）组件（在组件层级上高于所有需要该 state 的组件）。

- 该共同所有者组件或者比它层级更高的组件应该拥有该 state。

- 如果你找不到一个合适的位置来存放该 state，就可以直接创建一个新的组件来存放该 state，并将这一新组件置于高于共同所有者组件层级的位置。
