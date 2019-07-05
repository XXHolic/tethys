# React Hook

## 版本

### 16.8

## 作用

### 状态复用

- Hook 将组件中相互关联的部分拆分成更小的函数

### 简化理解和使用

### 让代码便于优化

## 主要方法

### useState

- 初始化 state 的某个属性值和对应的处理程序

- 可以多次使用

```javascript
 const [age, setAge] = useState(42);
  const [fruit, setFruit] = useState('banana');
  const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
```

### useEffect

- 给函数组件增加了操作副作用的能力。

-  React 组件中执行过数据获取、订阅或者手动修改过 DOM。我们统一把这些操作称为“副作用”，或者简称为“作用”。

- 默认情况下，React 会在每次渲染后调用副作用函数

- 可以多次使用

### useContext

- 接收一个 context 对象（React.createContext 的返回值）并返回该 context 的当前值。当前的 context 值由上层组件中距离当前组件最近的 <MyContext.Provider> 的 value prop 决定。

## 规则

1. 只能在函数最外层调用 Hook。不要在循环、条件判断或者子函数中调用。

2. 只能在 React 的函数组件中调用 Hook。不要在其他 JavaScript 函数中调用。
