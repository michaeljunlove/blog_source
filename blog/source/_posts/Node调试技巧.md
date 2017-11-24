clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/工大的冬天.jpg
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大的冬天.jpg
coverCaption: "冬季的工大"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大的冬天.jpg
comments: false
title: Node调试技巧
date: 2015-08-06 18:38:44
tags: [Node]
categories: [大前端技术栈]

---
本文整理了一下Node开发过程中的调试技巧
<!-- more -->
***
OK，在开始进入我们的Node开发调试之前，先选一个我们Node入门最经典的hello world的例子吧。
``` javascript
//require来加载核心的http模块
var http = require('http');
//创建一个server对象
var server=http.createServer(function(request,response){
//设置正确的头部和状态码
response.writeHead(200,{'Content-Type':'text/plain'});
//输出Hello world和换行符
response.end('Hello world!\n');
}).listen(8000,'127.0.0.1');
console.log('Server start at http://127.0.0.1:8000/');
```
# 自动监听文件变化
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Node.js应用是存储在内存中的，所以当我们修改源代码内容的时候，必须重启进程才会看得到变化，每次这样手动操作，相当的不方便。为了提高开发效率，我们通过安装一些可以监听fs模块的包来方便开发。实现这种功能的包很多，下面列举了实现这个功能的包的名字，我选了node-dev这个包。
* forever
* node-dev
* nodemon
* supervisor
* up

## 安装node-dev
``` javascript
npm install -g node-dev
```
## 开发环境调用node-dev
``` javascript
node-dev  index.js

```

<br/>
有了node-dev后，就方便很多啦。下面来讲一些node开发过程中的调试技巧
# 方法1--console.log

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;最好的，最简单的调试方法就是console.log()啦，因为它不会中断执行过程，执行迅速并且信息量丰富。当然这是它的优点，然而在某些时候后呢，我们需要暂停执行过程，来观察异步代码中调用栈中的更多的相关信息，这时候就需要用到方法二了。

# 方法2--基于Nodejs内建的调试器


[debugger官网](http://nodejs.org/api/debugger.html)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;把上述的代码保存为app.js吧，然后使用如下命令来进行调试，debugger这个是内置的调试工具, 主要支持基本的断点功能。具体的调试命令可以到官网查看，因为都很简单，就不赘述了。
``` javascript
node debug app.js
```
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/node_debug_1.png "基于Nodejs内建的调试器" %}   
    

# 方法3--使用Node Inspector来调试

[Node Inspector github地址](https://github.com/node-inspector/node-inspector)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;前面提到的2种调试方法都没有GUI，导致使用起来不是十分友好，Node Inspector，安装命令如下，因为用的是MAC的系统，如果不加sudo的话会报错。
``` javascript
sudo npm install -g node-inspector 
```
  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;安装好以后，我们就可以使用如下命令来调试了。当你输完这条命令以后，会弹出一个谷歌浏览器的窗口（Node Inspector会调用Web开发工具的接口），所以一定要在电脑上安装一个Chrome浏览器哦
``` markdown
//The node-debug command will load Node Inspector in your default browser.
//Node Inspector works in Chrome and Opera only.
node-debug app.js
```
 

    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;界面如下，这样我们就可以查看调用栈，浏览空间变量，还可以在Console选项卡中执行任何的Node命令，这样就方便多了。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/node_debug_2.png "Node Inspector调试" %}

# 方法4--使用devtool 直接在 Chrome 开发者工具直接运行 Node.js 程序, 调试

[devtool github地址](https://github.com/Jam3/devtool)


