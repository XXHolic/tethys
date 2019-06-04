# webpack 使用

## 管理资源

### 使用 loader，配置 module

#### css：style-loader css-loader

#### 图片和字体： file-loader url-loader

#### csv 和 xml：csv-loader
 和 xml-loader

## 管理输出

### 自动更新文件引用

#### HtmlWebpackPlugin、html-webpack-template

### 清理

#### clean-webpack-plugin

### Manifest

####  WebpackManifestPlugin

## 开发

### 追踪错误和警告

#### devtool: 'inline-source-map'

### 自动编译

#### webpack's Watch Mode

##### webpack 自带的功能，但不能自动刷新

#### webpack-dev-server

##### 内部使用了 webpack-dev-middleware

#### webpack-dev-middleware

## 模块热替换

### 局部刷新模块和样式

## tree shaking

### 去除无用的代码

## 环境构建

### 测试环境

### 生成环境

## 代码分离

### 入口起点

#### 使用 entry
 配置手动地分离代码。

### 防止重复

#### 使用 CommonsChunkPlugin
 去重和分离 chunk。

### 动态导入

#### 通过模块的内联函数调用来分离代码。

### bundle 分析

#### webpack-bundle-analyzer

## 懒加载

- 是一种很好的优化网页或应用的方式

- 先把你的代码在一些逻辑断点处分离开，然后在一些代码块中完成某些操作后，立即引用或即将引用另外一些新的代码块。

## 缓存

### 使用 contenthash

### 没有变化就不该改变 hash

#### 开发：NamedModulesPlugin

#### 生产：HashedModuleIdsPlugin

## shimming

### 按需加载

### 管理全局变量

#### imports-loader

#### exports-loader

## 离线环境

### Service Workers

#### workbox-webpack-plugin
