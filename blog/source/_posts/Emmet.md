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
title: Emmet常用语法
date: 2016-04-16 18:38:44
tags: [Emmet]
categories: [工具]

---
Emmet（原名：Zen Coding）是文本编辑器一个插件，是前端开发快速输入代码一种方式，能帮助你使用CSS语法来提高输入HTML代码的速度，免去了大家输入重新性标签的过程。虽然之前也一直在用，但没好好整理过。
<!-- more -->
***
# 学习网站

 * [前端开发利器 - Emmet (Zen Coding)](http://www.gbtags.com/gb/gbliblist/3.htm)
 
# 使用方法

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;基本上主流的文本编辑器都支持Emmet，安装好Emmet插件后，输入Emmet命令后，请按"tab"键，自动生成对应代码

# 生成HTML5代码框架

``` markdown
html:5<Tab键>
```

# 快速的生成HTML标签

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;如以下代码就可以快速生成body标签，你所输入的字符可以是任何字符。

``` markdown
body<Tab键>
//生成如下HTML代码
<body></body>
```


# 使用">"号生成子元素

``` markdown
div>ul>li <Tab键>
//生成如下HTML代码
<div>
  <ul>
    <li></li>
  </ul>
</div>
```

# 使用“^”返回父层元素来添加新的元素

``` markdown
//返回两层父级元素
div>p>span+em^bq<Tab键>
//生成如下HTML代码
<div>
  <p><span></span><em></em></p>
  <blockquote></blockquote>
</div>
```
# 使用“*”生成重复的元素
``` markdown
ul>li*2<Tab键>
//生成如下HTML代码
<ul>
  <li></li>
  <li></li>
</ul>
```

# 使用“()”生成复杂的组合
``` markdown
div>(header>ul>li*2>a)+footer>p<Tab键>
//生成如下HTML代码
<div>
  <header>
    <ul>
      <li><a href=""></a></li>
      <li><a href=""></a></li>
    </ul>
  </header>
  <footer>
    <p></p>
  </footer>
</div>
```
# 使用“#”生成id,“.”生成class
``` markdown
div#michael.michael<Tab键>
//生成如下HTML代码
<div id="michael" class="michael"></div>
```
# 使用“[]”自定义需要的属性
``` markdown
td[title="Hello world!" colspan=3]<Tab键>
//生成如下HTML代码
<td title="hello gbtags" colspan="5"></td>
```
# 使用"$"生成相关属性的编号
``` markdown
ul>li.item$*2<Tab键>
//生成如下HTML代码
<ul>
  <li class="item1"></li>
  <li class="item2"></li>
</ul>
```
# 使用"{}"定义标签内包含的内容
``` markdown
a{更多信息}<Tab键>
//生成如下HTML代码
<a href="">更多信息</a>
```
# 自动添加针对不同浏览器的CSS前缀定义
``` markdown
-bdrs<Tab键>
//生成如下HTML代码
-webkit-border-radius: ;
	-moz-border-radius: ;
	-ms-border-radius: ;
	-o-border-radius: ;
	border-radius: ;
```
