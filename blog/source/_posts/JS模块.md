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
title: JS模块
date: 2016-05-23 18:38:44
tags: [JS]
categories: [大前端技术栈]

---
AMD、CMD、ES6-Module
<!-- more -->
***
# 学习网站

 * [关于ES6模块设计思想](http://benjamn.github.io/empirenode-2015/#/)
 
 * [【第779期】ES6 的模块系统](http://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651224231&idx=1&sn=d03b0f6253542cdd4b97f80bd7a83125&chksm=bd49a1238a3e2835a0ff6528c530e7d57eed13deee589f636b1628b1025e4eee3a0277aaebc5&mpshare=1&scene=23&srcid=1211DHDbWnBH2urHEVzr2uXC#rd)

 * [ES6模块]( http://es6.ruanyifeng.com/#docs/module)
 
 * [前端工程之模块化](  http://fex.baidu.com/blog/2014/03/fis-module/)
 
 * [AMD]( https://github.com/amdjs/amdjs-api/wiki/AMD)
 
 * [CMD]( https://github.com/seajs/seajs/issues/242)
 





# 模块干嘛用？

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/JS%E6%A8%A1%E5%9D%97.png "JS模块" %}


# 模块系统

### 立即执行函数

``` javascript
　var module1 = (function(){
　　　　var _count = 0;
　　　　var m1 = function(){
　　　　　　//...
　　　　};
　　　　var m2 = function(){
　　　　　　//...
　　　　};
　　　　return {
　　　　　　m1 : m1,
　　　　　　m2 : m2
　　　　};
　　})();
```
### CommonJS规范

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Node采用的就是CommonJS规范，同步的require方式，不适合浏览器环境。



### AMD

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;AMD 是 RequireJS 在推广过程中对模块定义的规范化产出，专为异步IO环境打造，适合浏览器环境。

### CMD

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CMD 是 SeaJS 在推广过程中对模块定义的规范化产出。

### ES6 module

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ES6 module 模块功能主要由两个命令构成：export和import。export命令用于规定模块的对外接口，import命令用于输入其他模块提供的功能。