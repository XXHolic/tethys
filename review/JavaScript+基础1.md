# JavaScript 基础1

## 基本类型

### String

### Number

#### NaN

1. 数值中只有 0 除以 0 会返回NaN

2. 任何涉及 NaN 的操作（例如NaN/10）都会返回NaN

3. NaN 与任何值都不相等，包括NaN 本身

4. isNaN() 方法，注意空字符串会返回 false，跟测试数字返回值一样

#### 类型转换

1. Numbert(null) 返回值是 0

2. Numbert(undefined) 返回值是 NaN

### Boolean

### Object

### Undefined

1. null === undefined 为 true，因为，undefined 值是派生自null 值的。



### Null

1. 发音 [nʌl]

2. typeof null 返回的值是 object

### Symbol

1. symbol 类型的是独一无二的，可以来来防止属性名相同的冲突

2. symbol 不能使用 new Symbol()

3. Boolean() 转换为 true

参考链接：http://es6.ruanyifeng.com/#docs/symbol

## 作用域和内存

### 作用域

- 作用域是一套规则，用于确定在何处以及如何查找变量

### 垃圾回收

#### 标记清除

- 垃圾收集器会给存储在内存中的所有变量都加上标记，它会去掉正在使用或被引用变量的标记。每隔一段时间就会“清理”那些带有标记的变量。

#### 引用计数

- 跟踪记录每个值被引用的次数。当引用次数为 0 的就会被回收。

- 这种方式有个严重的问题：相互引用。这样就永远回收不了。

### 内存泄漏

- 使用的内存，一直没有得到释放，比较常见的就是变量的引用一直存在。

- 相应的还有一个 “内存溢出” 概念：程序向系统申请一定大小的内存，而系统不能满足程序要求，于是产生了溢出。

## 对象

### 原型链

1. 原型链中的原型指的是 `Prototype` 属性。

2. JavaScript 中的对象都有一个内置的 Prototype ，其实就是对象的引用。

3. 当访问对象中的属性不存在时，就会查找对象内部 Prototype 关联的对象，这个关联关系就形成了一条原型链。Prototype 链最终都会指向内置的 Object.prototype 。

4. 很常见的例子，就是模仿类，也就是常说的构造函数，用构造函数声明的对象，都是通过原型链相互关联起来，看起来像类一样，但其实有这本质的区别：**类是可以复制多次，就像模具一样，但   JavaScript 并没有类似的复制机制**

### 闭包

1. 闭包其实在 JavaScript 中很常见，它是基于作用域写代码产生的结果。

2. 当函数可以记住并访问所在的词法作用域，即使函数是在当前词法作用域之外执行，这时就产生了闭包。

**作用**

实现模块，模块主要有2个特征：

1.  为创建内部作用域而调用了一个包装函数

2. 包装函数的返回值必须至少包括一个对内部函数的引用

### this

绑定规则：
- 默认绑定
- 隐式绑定
- 显式绑定
- new 绑定

判断优先级：
1. 函数是否在 new 中调用（new 绑定）？如果是的话 this 绑定的是新创建的对象。

2. 函数是否通过 call、apply 或 bind 绑定调用（显示绑定）？如果是的话，this 绑定的是指定的对象。

3. 函数是否在某个上下文对象中调用（隐式绑定）？如果是的话，this 绑定的是那个上下文对象。

4. 如果都不是的话，使用默认绑定。如果在严格模式下，就绑定到 undefined，否则绑定到全局对象。

## 事件

- 事件，就是文档或浏览器窗口中发生的一些特定的交互。

参考链接：
- https://github.com/XXHolic/blog/issues/14

### 模拟事件

### 事件处理程序

- 响应某个事件的函数就叫做事件处理程序

三种事件同时存在时：
- DOM0 级事件处理程序会覆盖 HTML 事件处理程序，DOM2 级事件处理程序正常。

#### HTML 事件

- 如果指定的处理程序比页面 DOM 后加载执行，那么用户可能在此之前就触发了事件，就会引发错误，对此，很多 HTML 事件处理程序都会被封装在一个 try-catch 块中。

- 扩展事件处理程序的作用域链在不同的浏览器中会导致不同结果，这篇文章里面有说明。

- 将 HTML 与 JavaScript 代码紧密耦合，不好维护。现在一般都不推荐这种方式，都提倡 HTML 内容和 JavaScript 行为分离。

#### DOM 0 级事件

特点：

- 简单，具有跨浏览器的优势，现代浏览器都支持这种方式。
- 删除指定的事件处理程序，将事件处理程序属性的值设置为 null 即可。
- 没有运行相关代码之前，相关事件的触发很有可能不会响应。说可能，是因为有些情况默认触发点击效果，例如 a 标签跳转功能。

缺点：

-每种事件类型最多只有一个处理程序，可能会被覆盖，后执行的会覆盖先执行的，

####  DOM 2 级事件

特点：
- 该方式是添加新的事件处理程序，不会覆盖已有的事件处理程序，也就是说可以跟 DOM0 级事件处理程序共存，先执行的代码先触发，示例页面。

- 可以添加多个事件处理程序，调用顺序跟添加的顺序一致。

- 通过 addEventListener() 添加的事件处理程序，只能通过 removeEventListener() 来删除，它们的参数要完全一样才有效。


### 事件流

- 事件流描述的是从页面中接收事件的顺序。

- 同一元素，事件类型的触发顺序优先于事件流的触发顺序，比如 mouseup 在冒泡和捕获阶段有事件处理程序，也绑定了 在 捕获阶段 click 事件，mouseup 冒泡和捕获时间触发完了，才会触发 click 事件。

#### 捕获

#### 冒泡

一般建议使用这个处理事件

#### DOM 事件流

- “DOM2 级事件”规定的事件流包括三个阶段：事件捕获阶段、处于目标阶段和事件冒泡阶段。

问题：同一个元素，在冒泡和捕获阶段都绑定同一类型事件，会如何？

- 绑定事件处理程序写在前面的先触发

- 同一事件可以绑定多个处理程序，但绑定时，如果 addEventListener 方法的参数相同，那么就不会重复触发多次。

- 不同的事件处理程序，执行的顺序，跟绑定书写的顺序一致。



### 事件类型

#### UI 事件

- UI 事件指的是那些不一定与用户操作有关的事件。

- load
- unload
- abort
- error
- select
- resize
- scroll



#### 鼠标和滚轮

- mousenter
- mousedown
- mouseup
- click
- dbclick
- mouseleave
- mousemove
- mouseover
- mouseout

#### 焦点

- blue
- focus

#### 键盘和文本

- keydown,当用户按下键盘上的任意键时触发，而且如果按住不放的话，会重复触发此事件。

- kepress,当用户按下键盘上的字符键时触发，而且如果按住不放的话，会重复触发此事件。

- textInput,当用户在可编辑区域中输入字符时，就会触发这个事件。

- keyup

- 回车（Enter） keyCode 13

#### 变动

- DOMNodeRemoved

- DOMNodeRemovedFromDocument

- DOMSubtreeModified

- DOMNodeInserted

- DOMNodeInsertedIntoDocument

#### 设备

- orientationchange,以便开发人员能够确定用户何时将设备由横向查看模式切换为纵向查看模式

#### html5

- contextmenu

- DOMContentLoaded

- readystatechange

- pageshow

- pagehide

- hashchange

#### 触摸和手势

- touchstart
- touchmove
- touchend
- touchcancel

#### 复合

- 复合事件（composition event）是DOM3 级事件中新添加的一类事件，用于处理IME 的输入序列。

- IME（Input Method Editor，输入法编辑器）可以让用户输入在物理键盘上找不到的字符。

## 异步

### ajax 

### promise

### fetch

### 跨域

## 错误处理

## JOSN
