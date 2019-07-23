# JavaScript 基础 2

## ajax

### 跨域

跨域的出现源于浏览器的同源策略，这是一个安全功能：不同源的客户端脚本在没有明确授权下，是不能读写对方资源。

其中源的定义是指：协议、域名和端口号。协议、域名和端口号均相同则属于同源。

同源策略认为域和子域属于不同的域。
一级域名相同，只是二级域名不相同，浏览器允许设置 document.domain 来共享资源，例如cookie。
服务器也可以在设置Cookie的时候，指定Cookie的所属域名为一级域名，这样二级域名和三级域名不同，不用做任何设置，都可以读取 cookie。

#### CORS

- Cross-Origin Resource Sharing，跨源资源共享

- CORS 背后的基本思想，就是使用自定义的HTTP 头部，让浏览器与服务器进行沟通，从而决定请求或响应是应该成功，还是应该失败。

#### 图像 src

#### JSONP

#### web sockets

#### Comet

- 长轮询和流

### XMLHttpRequest

#### readyState

0：未初始化。尚未调用open()方法。
1：启动。已经调用open()方法，但尚未调用send()方法。
2：发送。已经调用send()方法，但尚未接收到响应。
3：接收。已经接收到部分响应数据。
4：完成。已经接收到全部响应数据，而且已经可以在客户端使用了。

#### formData

#### 事件

## 离线应用

### navigator.onLine

## 数据存储

### cookie

- 最初是在客户端用于存储会话信息的

- cookie 在性质上是绑定在特定的域名下的。当设定了一个cookie 后，再给创建它的域名发送请求时，都会包含这个cookie

- expires/Max-Age：若设置其值为一个时间，那么当到达此时间后，此cookie失效。不设置的话默认值是Session，意思是cookie会和session一起失效。当浏览器关闭(不是浏览器标签页，而是整个浏览器) 后，此cookie失效。


与 session 区别：
- Cookie和Session都是会话技术，Cookie是运行在客户端，Session是运行在服务器端。
- Cookie有大小限制以及浏览器在存cookie的个数也有限制，Session是没有大小限制和服务器的内存大小有关。
- Cookie有安全隐患，通过拦截或本地文件找得到你的cookie后可以进行攻击。

### IndexedDB

- 保存结构化数据的一种数据库
- 思想是创建一套API，方便保存和读取JavaScript 对象，同时还支持查询及搜索。

- 操作完全是异步进行的

- 差不多每一次IndexedDB 操作，都需要你注册onerror 或onsuccess 事件处理程序，以确保适当地处理结果

### storage

- clear
- key
- setItem
- removeItem

#### sessionStorage

- 对象存储特定于某个会话的数据，也就是该数据只保持到浏览器关闭
- 存储在sessionStorage 中的数据可以跨越页面刷新而存在，同时如果浏览器支持，浏览器崩溃并重启之后依然可用（Firefox 和WebKit 都支持，IE 则不行）。
- 不同浏览器写入数据方面略有不同。Firefox 和WebKit 实现了同步写入，所以添加到存储空间中的数据是立刻被提交的。而IE 的实现则是异步写入数据，所以在设置数据和将数据实际写入磁盘之间可能有一些延迟。对于少量数据而言，这个差异是可以忽略的。对于大量数据，你会发现IE 要比其他浏览器更快地恢复执行，因为它会跳过实际的磁盘写入过程。

#### localStorage

- 要访问同一个localStorage 对象，页面必须来自同一个域名（子域名无效），使用同一种协议，在同一个端口上

- 的HTML 5 规范中作为持久保存客户端数据的方案取代了globalStorage。

#### globalStorage

- 作为最初的Web Storage 规范的一部分，这个对象的目的是跨越会话存储数据，但有特定的访问限制。要使用globalStorage，首先要指定哪些域可以访问

```js
//保存数据
globalStorage["wrox.com"].name = "Nicholas";
//获取数据
var name = globalStorage["wrox.com"].name;
```

- 对globalStorage 空间的访问，是依据发起请求的页面的域名、协议和端口来限制的。

- 如果不使用removeItem() 或者delete 删除， 或者用户未清除浏览器缓存， 存储在globalStorage 属性中的数据会一直保留在磁盘上。这让globalStorage 非常适合在客户端存储文档或者长期保存用户偏好设置。

## 新 API

### requestAnimationFrame()

### navigator.geolocation

### File API

### Web Workers

## 错误处理

### try-catch-finally

### throw new Error()

### onerror 事件

### 错误类型

#### Error

#### EvalError

#### RangeError

#### ReferenceError

#### SyntaxError

#### TypeError

#### URIError

### 错误上传

```javascritp
function logError(sev, msg){
	var img = new Image();
	img.src = "log.php?sev=" + encodeURIComponent(sev) + "&msg=" +
encodeURIComponent(msg);
}
```

## canvas

### 2D

#### getContext

### 3D

#### WebGL
