# HTML

## 是什么

### 1、是一种标记语言，Hyper Text Markup Language 。

### 2、定义了网页内容的含义和结构。

### 3、最初设计的目的是为了语义化描述科学文档。

## 如何划分

- 由于其语义化的特性，而且入门简单易懂，以功能来进行划分归类。
- 从感性的可视的角度切入。

### 简单功能

#### 纯文本

##### div/span

#### 图像

##### img

#### 列表

##### ul/ol

#### 链接

##### a

#### 表格

##### table/th/tr/td/theader/tbody/tfooter/caption

#### 表单

##### form/input(select/checkbox/radio/button)

#### 多媒体

##### 视频

###### video/source

##### 音频

###### audio

#### 数学公式

##### math

### 复杂功能

#### 富应用

- 富应用是指包含丰富的图片，丰富的人机交互，炫目的效果。	

##### canvas

#### 拖拽

##### draggable 属性

#### web worker

##### 运行在后台的 JavaScript，不会影响页面的性能。

#### 定位

- 在对象 navigator 中

##### Geolocation API 用于获得用户的地理位置。

#### 历史会话

##### history

- go
- back
- forward
- pushState
- replaceState

#### 存储

#### SSE

- HTML5 服务器发送事件（server-sent event）允许网页获得来自服务器的更新。

示例
```js
var source=new EventSource("demo_sse.php");
source.onmessage=function(event)
{
    document.getElementById("result").innerHTML+=event.data + "<br>";
};
```

#### websocket

- WebSocket 是 HTML5 开始提供的一种在单个 TCP 连接上进行全双工通讯的协议。

#### 无损展示

##### svg

- 可伸缩矢量图形 (Scalable Vector Graphics)
- 图像可被搜索、索引、脚本化或压缩

#### 应用程序缓存

- 使用 HTML5，通过创建 cache manifest 文件，可以轻松地创建 web 应用的离线版本。

## 其它特性

### 语义化

#### 可访问性

#### 全局属性

- https://www.runoob.com/tags/ref-standardattributes.html

#### 元数据

##### charset

##### content

- 定义与 http-equiv 或 name 属性相关的元信息。

##### name

- application-name：规定页面所代表的 Web 应用程序的名称。
- author
- description
- generator：规定用于生成文档的一个软件包（不用于手写页面）
- keywords

##### http-equiv

- 把 content 属性关联到 HTTP 头部。

### 命名空间

- xmlns 属性可以在文档中定义一个或多个可供选择的命名空间。
- 该属性可以放置在文档内任何元素的开始标签中。
- 该属性的值类似于 URL，它定义了一个命名空间，浏览器会将此命名空间用于该属性所在元素内的所有内容。

#### math

- xmlns="http://www.w3.org/1998/Math/MathML"

#### svg

- xmlns="http://www.w3.org/2000/svg"

#### html

- HTML 文档第一行是一个特定的文档声明，这个文档声明用于表示后面的文档标记该遵循那个标准

- 保留这个是历史原因，如果没有文档类型声明，大多数浏览器将转换到一种混杂模式，表现可能就会有些不一样

### 字符实体

- HTML 中的预留字符必须被替换为字符实体。例如HTML 中不能使用小于号（<）和大于号（>），这是因为浏览器会误认为它们是标签。
- 一些在键盘上找不到的字符也可以使用字符实体来替换。
