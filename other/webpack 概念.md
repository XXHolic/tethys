# webpack 概念

## entry（入口）

<!--Note-->
###### 作用
- 指示 webpack 应该使用哪个模块，来作为构建其内部依赖图的开始。

###### 示例
```javscript
module.exports = {
  entry: './path/to/my/entry/file.js'
};
```
<!--/Note-->

### 设置入口

## output（出口）

<!--Note-->
###### 作用
- 告诉 webpack 在哪里输出它所创建的 bundles，以及如何命名这些文件，默认值为 ./dist

###### 示例
```javscript
module.exports = {
  entry: './path/to/my/entry/file.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js'
  }
};
```

<!--/Note-->

### 输出路径和文件名

## loader

<!--Note-->
###### 作用
- 让 webpack 能够去处理那些非 JavaScript 文件（webpack 自身只理解 JavaScript）。
- 在 webpack 的配置中 loader 有两个目标：1 `test` 属性，用于标识出应该被对应的 loader 进行转换的某个或某些文件;2 `use` 属性，表示进行转换时，应该使用哪个 loader。

###### 示例
```javscript
const path = require('path');

const config = {
  output: {
    filename: 'my-first-webpack.bundle.js'
  },
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  }
};

module.exports = config;
```


<!--/Note-->

### 处理非 JavaScript 文件，例如字体、图片 等。

## plugins

<!--Note-->
###### 作用
- 插件的范围包括，从打包优化和压缩，一直到重新定义环境中的变量。插件接口功能极其强大，可以用来处理各种各样的任务。

###### 示例
```javscript
const HtmlWebpackPlugin = require('html-webpack-plugin'); // 通过 npm 安装
const webpack = require('webpack'); // 用于访问内置插件

const config = {
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({template: './src/index.html'})
  ]
};

module.exports = config;
```
<!--/Note-->

### 打包

### 优化

### 再处理

## mode（模式）

<!--Note-->
###### 作用
- 提供 mode 配置选项，告知 webpack 使用相应模式的内置优化。

###### 示例
```javscript
module.exports = {
  mode: 'production'
};
```
<!--/Note-->

### 区分环境

## modules（模块）

- webpack 通过 loader 可以支持各种语言和预处理器编写模块。

## manifest

- 当编译器(compiler)开始执行、解析和映射应用程序时，它会保留所有模块的详细要点。这个数据集合称为 "Manifest"。

- 当完成打包并发送到浏览器时，会在运行时通过 Manifest 来解析和加载模块。

- 无论你选择哪种模块语法，那些 import 或 require 语句现在都已经转换为 __webpack_require__ 方法，此方法指向模块标识符(module identifier)。通过使用 manifest 中的数据，runtime 将能够查询模块标识符，检索出背后对应的模块。

### 包含所有模块要点信息

## runtime

- runtime 包含：在模块交互时，连接模块所需的加载和解析逻辑。包括浏览器中的已加载模块的连接，以及懒加载模块的执行逻辑。



### 加载模块

### 解析模块

## dependency graph（依赖图）

- 任何时候，一个文件依赖于另一个文件，webpack 就把此视为文件之间有 依赖关系 

- 从 入口起点 开始，webpack 递归地构建一个 依赖图 ，这个依赖图包含着应用程序所需的每个模块，然后将所有这些模块打包为少量的 bundle - 通常只有一个 - 可由浏览器加载。

### 根据入口文件递归所有必要模块信息

## targets（构建目标）

- webpack 能够为多种环境或 target 构建编译。

### 设置目标运行环境

## hot module replacement（模块热替换）

模块热替换(HMR - Hot Module Replacement)功能会在应用程序运行过程中替换、添加或删除模块，而无需重新加载整个页面。主要是通过以下几种方式，来显著加快开发速度：

- 保留在完全重新加载页面时丢失的应用程序状态。

- 只更新变更内容，以节省宝贵的开发时间。

- 调整样式更加快速 - 几乎相当于在浏览器调试器中更改样式。

### 替换、添加、删除模块

## chunk

<!--Note-->
###### 参考链接

-  https://stackoverflow.com/questions/42523436/what-are-module-chunk-and-bundle-in-webpack

- https://webpack.js.org/glossary/
<!--/Note-->

### 比 bundle 更小的块

## bundle

<!--Note-->
###### 参考链接

-  https://stackoverflow.com/questions/42523436/what-are-module-chunk-and-bundle-in-webpack

- https://webpack.js.org/glossary/
<!--/Note-->

### 一些相关联的包打包成一个文件

## vendor

### 第三方库
