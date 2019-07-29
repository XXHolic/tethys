# Module

## 缘由

- 历史上，JavaScript 一直没有模块（module）体系，无法将一个大程序拆分成互相依赖的小文件，再用简单的方法拼装起来。其他语言都有这项功能，比如 Ruby 的require、Python 的import，甚至就连 CSS 都有@import，但是 JavaScript 任何这方面的支持都没有，这对开发大型的、复杂的项目形成了巨大障碍。

## 旧方案

- CommonJS 用于服务器

common.js 的规范要点有：
1. 每个文件就是一个模块，内部定义的变量、函数对外不可见。
2. 导出使用 exports 对外暴露。
3. 导入使用 require。

- AMD CMD 用于浏览器

AMD 代表 require.js CMD 代表 sea.js
