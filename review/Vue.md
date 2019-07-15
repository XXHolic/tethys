# Vue

## 定义

- 是一套用于构建用户界面的渐进式框架。

## 特性

### 指令

- 指令带有前缀 v-，以表示它们是 Vue 提供的特殊特性。

#### v-bind 

```js
<div id="app-2">
  <span v-bind:title="message">
    鼠标悬停几秒钟查看此处动态绑定的提示信息！
  </span>
</div>

var app2 = new Vue({
  el: '#app-2',
  data: {
    message: '页面加载于 ' + new Date().toLocaleString()
  }
})
```
此处该指令的意思是：“将这个元素节点的 title 特性和 Vue 实例的 message 属性保持一致”。

#### v-if

```js
<div id="app-3">
  <p v-if="seen">现在你看到我了</p>
</div>

var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```

#### v-for

```js
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>


var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: '学习 JavaScript' },
      { text: '学习 Vue' },
      { text: '整个牛项目' }
    ]
  }
})
```

#### v-on

```js
<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">反转消息</button>
</div>


var app5 = new Vue({
  el: '#app-5',
  data: {
    message: 'Hello Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```

#### v-model

- 实现表单输入和应用状态之间的双向绑定。

```js
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>

var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
})
```

### 组件

#### 全局注册

- 用在任何新创建的 Vue 根实例 (new Vue) 的模板中
```js
Vue.component('my-component-name', {
  // ... 选项 ...
})
```

#### 局部注册

## 生命周期

- https://cn.vuejs.org/images/lifecycle.png

- 在beforeCreate和created钩子函数之间进行初始化，beforeCreate的时候还没有 data 

- created 和 beforeMount 间的，首先会判断对象是否有el选项。如果有的话就继续向下编译，如果没有el选项，则停止编译。如果有就会按照下面的有限顺序执行：render函数选项 > template选项 > outer HTML.

- beforeMount 和 mounted 之间，给vue实例对象添加$el成员，并且替换掉挂在的DOM元素 

### beforeCreate

### created

### beforeMount

### mounted

### beforeUpdate

### updated

### beforeDestroy

### destroyed

## 响应式原理

- new Vue() 时传递的 data 属性是一个对象，Vue 将遍历此对象所有的属性，并使用 Object.defineProperty 把这些属性全部转为 getter/setter。在内部它们让 Vue 能够追踪依赖，在属性被访问和修改时通知变更。

- 每个组件实例都对应一个 watcher 实例，它会在组件渲染的过程中把“接触”过的数据属性记录为依赖。之后当依赖项的 setter 触发时，会通知 watcher，从而使它关联的组件重新渲染。https://cn.vuejs.org/images/data.png

- Vue 无法检测到对象属性的添加或删除。由于 Vue 会在初始化实例时对属性执行 getter/setter 转化，所以属性必须在 data 对象上存在才能让 Vue 将它转换为响应式的。

- 由于 Vue 不允许动态添加根级响应式属性，所以你必须在初始化实例前声明所有根级响应式属性，哪怕只是一个空值

- Vue 在更新 DOM 时是异步执行的。只要侦听到数据变化，Vue 将开启一个队列，并缓冲在同一事件循环中发生的所有数据变更。如果同一个 watcher 被多次触发，只会被推入到队列中一次。
