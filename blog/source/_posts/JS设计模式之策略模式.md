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
title: JS设计模式之策略模式
date: 2016-04-09 18:38:44
tags: [JS]
categories: [设计模式]

---
策略模式指的是定义一系列的算法，把它们一个个封装起来，将不变的部分与变化的部分隔开是每个设计模式的主题，策略模式的目的是将算法的使用与算法的实现分离开来。
<!-- more -->
***
# 学习网站

 * [Markdown学习网站](http://www.jianshu.com/collection/BDu5F8)

# 策略模式

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;策略模式的核心是：定义一系列的算法，把它们各自封装成策略类，算法被封装在策略类内部的方法里面。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;一个基于策略模式的程序至少由两部分组成：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.一组策略类，策略类封装了具体的算法，并负责具体的计算过程。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.环境类Context,Context接受客户的请求，并把请求委托给某个策略类。要做到这一点，Context中要维持对某个策略对象的引用。

# 举个实例吧

``` markdown
1.文本1
2.文本2
3.文本3
```


