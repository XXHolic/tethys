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

### IndexedDB

### storage

- clear
- key
- setItem
- removeItem

#### sessionStorage

- 主要用于仅针对会话的小段数据的存储

#### localStorage

- 要访问同一个localStorage 对象，页面必须来自同一个域名（子域名无效），使用同一种协议，在同一个端口上

#### globalStorage

- 主要用于仅针对会话的小段数据的存储

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
