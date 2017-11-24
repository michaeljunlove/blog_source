clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/工大向日葵.jpg
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大向日葵.jpg
coverCaption: "工大的向日葵"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大向日葵.jpg
comments: false
title: Webpack学习笔记
date: 2016-06-07 18:38:44
tags: [Webpack]
categories: [工具]

---
搞大前端的，突然感觉真心累啊，什么grunt、gulp、browserify、webpack这些构建工具一个接着一个来了，之前玩过grunt，后来gulp、browserify、webpack就没玩了。本篇主要放了一些webpack相关的学习资源，具体使用自己去实践一遍吧，不再细说啦。
<!-- more -->
***
# 学习网站

 * [webpack官网]( https://webpack.github.io/)
 * [慕课网视频：webpack深入与实战]( http://www.imooc.com/learn/802)
 * [webpack入门教程](http://html-js.com/article/3113) &nbsp;<span style="color:red;">初学者必看，简单易懂</span>
 * [Webpack 和 React 小书](https://fakefish.github.io/react-webpack-cookbook/)&nbsp;<span style="color:red;">重点推荐！！！</span>
 * [Webpack 中文指南](https://zhaoda.gitbooks.io/webpack/content/index.html)&nbsp;<span style="color:red;">系统全面地介绍了 Webpack 出现的背景、特点、使用，推荐！！！</span>
 * [题叶_Webpack 入门指迷](https://segmentfault.com/a/1190000002551952) 



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;webpack支持AMD,CMD,CommonJS的模块，具有`Code Splitting`、`Loaders`、`Plugin system`、`Hot Module Replacement`等特点。

# webpack 打包一个文件
``` markdown
webpack  hello.js(源文件) hello.bundle.js(打包后的文件)
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;打包后的结果如下图所示：第一行是Hash值，第二行是webpack的版本号，第三行是打包的时间
Asset是打包生成的文件，Size是生成文件的大小，Chunks是指这次打包的分块，Chunk Names是指这次打包的块名称.不过一般采用这种方式要写一些配置项，比较麻烦，所以一般都用`webpack.config.js`来保存一些配置信息。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/webpack.png "执行结果" %}

# 配置文件webpack.config.js

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;每个项目下都会置有一个 webpack.config.js配置文件，告诉webpack需要做那些工作。webpack.config.js的详细配置信息可以在[官方文档配置文件相关配置](http://webpack.github.io/docs/configuration.html)查看，一般这个配置文件长成下面这样。

``` javascript 
var path = require("path");
//样式通过<link>引入的插件
var ExtractTextPlugin = require("extract-text-webpack-plugin");
module.exports = {
    //页面入口文件配置，有3种配置方式
    entry: {
        index : './main.js'
    },
    //打包后文件输出配置
    output: {
        path: //输出的路径,
        filename: //输出的文件名
        publicPath: //公共路径如http://cdn.com
        
    },
    //自动检测文件变化并重新打包
    watch: true,
    module: {
        //加载器配置,放各种loaders，test表示对资源的正则匹配
        loaders: [
               {test: /\.css$/, loader: ExtractTextPlugin.extract("style-loader", "css-loader")},
               {test: /\.json$/,loader: 'json-loader'}, 
               {test: /\.(png|jpg|gif|woff|woff2)$/,loader: 'url-loader?limit=8192'},
         ]
    },
    //插件项
    plugins: [
    	new ExtractTextPlugin("[name].css")
    ],
    //其它解决方案配置
    resolve: {}
};
```

# webpack 命令行的几种基本命令
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当我们直接使用webpack命令的时候，会先去查找当前文件下的`webpack.config.js`文件
``` markdown
webpack     // 最基本的启动webpack方法，在开发环境中构建一次
webpack -w  // 提供watch方法，实时进行打包更新
webpack -p  // 在生产环境下构建，压缩，混淆代码，并移除无用代码
webpack -d  // 提供source map，方便调试。
```
# Loader加载器
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;最喜欢Loader加载器了。Webpack 本身只能处理 JavaScript 模块，如果要处理其他类型的文件，就需要使用 loader 进行转换。一个文件可以经由多个loader依次处理，loader与loader之间，以及loader与文件名之间用!分隔。如果使用了多个loader的话，数据流向是从右向左的。

``` javascript
//从style.css开始，依次经过css-loader和style-loader。
require('style!css!./style.css');
```
要使用一个Loader，先安装Loader，然后在`webpack.config.js`中的loaders加入对应的配置项
``` javascript
npm install XX-loader --save-dev
```

## 各种Loader
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;各种Loader具体见[list-of-loaders](http://webpack.github.io/docs/list-of-loaders.html)

| Loader名称        | 作用         | 
| ------------- |:-------------:| 
| json-loader     | 加载json文件 | 
| css-loader      | 加载css文件      | 
| style-loader | 将css插入到页面的style标签     |   
| file-loader | 加载mp4、ogg、svg等文件     |  
| sass-loader | 加载sassS文件     |  
| url-loader | 加载图片，只有不大于8kb的图片才会打包处理成Base64的图片     |  
| babel-loader | ES6转ES5，支持JSX 语法     |  
| flowcheck-loader |   用来[类型检查](https://tryflow.org/) | 

## Plugins插件的使用
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;插件的使用方式见[类型使用说明](http://webpack.github.io/docs/using-plugins.html) 

| Plugins名称        | 作用         | 
| ------------- |:-------------:| 
| htmlwebpackPlugin     | 帮助生成 HTML 文件，使用 script 来包含所有你的 webpack bundles等| 


# webpack-dev-server