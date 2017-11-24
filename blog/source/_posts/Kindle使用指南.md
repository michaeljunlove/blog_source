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
title: Kindle使用指南
date: 2016-04-16 18:38:44
tags: [Kindle]
categories: [工具]

---
睡前喜欢看会书，Kindle的阅读体验做的还是很不错的。
<!-- more -->
***
# 学习网站

 * [也许你并不懂Kindle](http://www.jianshu.com/p/bbec5f21eba8#)
 
 * [Kindle 电子书生成工具](http://www.barretlee.com/blog/2016/05/20/kindle-book-maker/#)




# 标题

``` markdown
 # 表示一级标题  
 ## 表示二级标题
 ### 表示三级标题
 #### 表示四级标题
 ##### 表示五级标题
 ###### 表示六级标题
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


# 插入数学公式

``` markdown
//STEP1:引入下面的MathJax引擎
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然后，再使用`Tex`写公式。`$$公式$$`表示行间公式，本来Tex中使用\(公式\)表示行内公式，但因为Markdown中\是转义字符，所以在Markdown中输入行内公式使用`\\(公式\\)`，如下代码：
``` markdown
//STEP2:使用Tex写公式
$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
\\(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\\)
```
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
\\(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\\)
