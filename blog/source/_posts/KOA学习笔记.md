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
title: KOA学习笔记
date: 2016-12-29 18:38:44
tags: [koa]
categories: [大前端技术栈]

---
koa 是由 Express 原班人马打造的，致力于成为一个更小、更富有表现力、更健壮的 Web 框架。使用 koa 编写 web 应用，通过组合不同的 generator，可以免除重复繁琐的回调函数嵌套，并极大地提升错误处理的效率。koa 不在内核方法中绑定任何中间件，它仅仅提供了一个轻量优雅的函数库，使得编写 Web 应用变得得心应手。
<!-- more -->
***
# 学习网站

 * [yeoman官网](http://yeoman.io/generators/)
 * [KOA官网](http://koa.bootcss.com/#)
 * [KOA中间件]( https://github.com/koajs/koa/wiki#middleware)
 * [KOA官方demo](https://github.com/koajs/examples)
 * [KOA学习视频](http://www.jikexueyuan.com/course/1518.html)
 * [KOA2进阶学习笔记](https://chenshenhai.github.io/koa2-note/)


# 安装运行

``` markdown
#安装koa项目工程生成器，带有经过筛选的优秀中间件，生成即用
cnpm install -g yo generator-k
#创建一个book目录
mkdir book
#k会让选择是否使用数据库，可以选择none，暂时跳过
yo k
# 运行，加上--harmony,这样才会支持ES6语法
node --harmony app.js
```

