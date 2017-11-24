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
title: JQuery
date: 2015-03-23 18:38:44
tags: [JQuery]
categories: [大前端技术栈]

---
Jquery
<!-- more -->
***
# 学习网站

 * [JQuery_API](http://jquery.cuishifeng.cn/)

# JQuery对象与DOM对象及其相互转换

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JQuery对象：指通过JQuery包装DOM对象后产生的对象
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DOM对象：通过原生API获取到的DOM节点
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DOM对象才可以使用DOM中的方法，JQuery对象不可以使用DOM中的方法

JQuery对象->DOM对象
``` javascript
var $cr = $("#cr")//JQuery对象
//转DOM对象，方案一
var cr = $cr[0] //DOM对象
//转DOM对象，方案二
var cr = $cr.get(0) //DOM对象
```

DOM对象->JQuery对象
``` javascript
var cr = document.getElementById("cr");//JQuery对象
//转JQuery对象,使用$()包装DOM对象。
var cr = $(cr) //JQuery对象
```
# 列表

``` markdown
1.文本1
2.文本2
3.文本3
```


# 特殊字符转换


``` markdown
<这个符号要用&amp;lt来转换
&这个符号要用&amp;amp来转换
©版权符号用&amp;copy来转换
```


# 代码区

空四格输入。Markdown 会把每行前面空四格的文本转换为代码块。


``` markdown
放相应语言的代码
```

# 每段文字开头空2格

``` markdown
最笨的方法，多放几个空格吧
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
```
# 图片
## 方案一

``` markdown
插入图片不需要其他按钮，你只需要使用 ![](图片链接地址）
![](http://7xid80.com1.z0.glb.clouddn.com/Markdown语法.jpg)
```
## 方案二-wide_image
``` markdown
{% wide_image 图片路径 [title text] %}
比如：{% wide_image http://google.fr/images/image125.png "A beautiful sunrise" %}
```
## 方案三-居中
``` markdown
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/原型链1.png "原型链" %}
```











