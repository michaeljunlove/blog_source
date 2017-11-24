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
title: Node模块
date: 2015-03-31 18:38:44
tags: [Node]
categories: [大前端技术栈]

---
最喜欢Node了，Node给人的感觉是一种全新的WEB开发模式，非常轻便，快捷。Node模块为整个Node的生态圈注入了活力。
<!-- more -->
***
# 相关网站

* [NodeJS官网](https://nodejs.org/)

* [NPM官网](https://www.npmjs.com/)

* [NodeJS框架](http://nodeframework.com/)

* [express中文网](http://www.expressjs.com.cn/)

* [Koa中文网](http://koa.bootcss.com/)

* [package.json中文网](http://www.mujiang.info/translation/npmjs/files/package.json.html)

* [语义化版本 2.0.0](http://semver.org/lang/zh-CN/)

* [node源码系列分析 Node.js 如何执行](http://www.cnblogs.com/papertree/category/792592.html)






# Node版本

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/node版本特点.png "node版本特点" %}


# Node 模块国内下载的解决方案

* [淘宝 NPM 镜像](http://npm.taobao.org/)

# Node模块

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Node的模块系统避免了对全局作用域的污染，即避免了命名冲突。它允许你从被引入文件中选择要暴露给程序的函数和变量。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Node.js的模块分为两类，一类为原生（核心）模块，一类为文件模块。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;原生模块在Node.js源代码编译的时候编译进了二进制执行文件，加载的速度最快。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;另一类文件模块是动态加载的，加载速度比原生模块慢。但是Node.js对原生模块和文件模块都进行了缓存。所以呢，在第二次require时，是不会有重复开销的。其中原生模块都被定义在lib这个目录下面，文件模块则不定性。

1.如果模块返回的函数或变量不止一个，则通过设定`exports`对象的属性来指明他们

2.如果模块只返回一个函数或变量，则通过设定`moudle.exports`属性来设定


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;之所以要这样做的原因是：`exports`本质上是`moudle.exports`的引用，`exports`最初被定义为一个可以添加属性的空对象，所以不能破坏掉`moudle.exports=exports`这层关系，你不能执行`exports=fun`这样的操作，但是可以执行`exports.funName=fun`这样的操作

---

# Node模块分类

![](http://7xid80.com1.z0.glb.clouddn.com/node模块分类.png)

## 波浪号

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;比如~1.2.2，表示安装1.2.x的最新版本（不低于1.2.2），但是不安装1.3.x，也就是说安装时不改变大版本号和次要版本号。

## 插入号

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;比如ˆ1.2.2，表示安装1.x.x的最新版本（不低于1.2.2），但是不安装2.x.x，也就是说安装时不改变大版本号。需要注意的是，如果大版本号为0，则插入号的行为与波浪号相同，这是因为此时处于开发阶段，即使是次要版本号变动，也可能带来程序的不兼容。

# npm关于模块的操作

安装模块:  npm install moduleName

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;node的安装分为全局模式和本地模式。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;一般情况下会以本地模式运行，包会被安装到和你的应用程序代码的本地node_modules目录下。在全局模式下，Node包会被安装到Node的安装目录下的node_modules下。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;全局安装命令为npm install -g moduleName。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;npm install moduleName --save 会在安装的同时，将信息写入package.json中


# 如何写模块

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;模块可以是一个文件，也可以是包含一个或者多个文件的目录。一般情况下，如果模块是个目录，在这个目录下有一个index.html的文件作为入口（当然，这个入口文件可以重写，在package.json中通过`main`这个键可以指明）

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;首先，我们创建一个circle.js的文件，有计算圆形的面积和周长两个方法，代码如下，因为模块返回的函数或变量不止一个（2个），所以这里我们用`exports`对象的属性来指明他们
``` javascript
    var PI = Math.PI;
    exports.area = function (r) {
        return PI * r * r;
    };
    exports.circumference = function (r) {
        return 2 * PI * r;
    };
    
    //或者可以采用下面这种方式也是可以的
    moudle.exports={
    
        area : function (r) {
           return PI * r * r;
        },
        
        circumference = function (r) {
           return 2 * PI * r;
        }
    }

```
        


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然后，我们就可以自己使用刚才创建的模块了，使用这个模块用到Node的 `require`函数，
``` markdown
//./表示模块和程序脚本在同一个目录下面
var circle = require('./circle.js');
console.log( 'The area of a circle of radius 4 is ' + circle.area(4));
```



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;需要指出的是，如果多个文件引入了同一个模块，那么是多个文件共享这个模块，所有对这个模块的操作都会反映到其他引入的文件中哦。
# require方法中的文件查找策略
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/image1.jpg "require方法中的文件查找策略" %}


# 整个文件查找流程
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/image2.jpg "整个文件查找流程" %}





