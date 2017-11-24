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
title: Ngrok代理转发软件
date: 2015-10-21 18:38:44
tags: [ngrok]
categories: [工具]

---
我们在调试移动端页面，会遇到这样的情况，手机连着公司的wifi，开发环境（台式机）插着公司的网线，我们要用手机来访问开发环境下的页面。
<!-- more -->
***
# 学习网站

 * [国内某Ngrok网站](http://www.idcfengye.com/)
 * [国内某Ngrok使用教程](http://www.sunnyos.com/article-show-61.html)
 


# 什么是nrgok

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;它是一个反向代理，我们机器上运行起这个服务后，它可以把本地的一个端口代理到公网。代理到公网是什么概念？公网啊，那就是大家都可以访问到了，没有任何网络限制。当然，我们的测试机，连接到任何网络下的手机也是可以的了。

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


# 区块

在每行的最前面加上 > ，形成区块
区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 >
区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等
> # 我是区块

# 分割线

``` markdown
---
***
```
---
***

# 粗体和斜体
``` markdown
*一盏灯* 表示斜体
**一简书** 表示粗体

```
用两个 * 包含一段文本就是粗体的语法，用一个 * 包含一段文本就是斜体的语法。
*一盏灯*， 一片昏黄；**一简书**， 一杯淡茶。 守着那一份淡定， 品读属于自己的寂寞。 保持淡定， 才能欣赏到最美丽的风景！ 保持淡定， 人生从此不再寂寞。



# 表格
``` markdown

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

```

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |




