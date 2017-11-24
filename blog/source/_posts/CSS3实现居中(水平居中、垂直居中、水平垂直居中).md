clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/%E5%B7%A5%E5%A4%A7%E8%83%8C%E6%99%AF3.JPG
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/%E5%B7%A5%E5%A4%A7%E8%83%8C%E6%99%AF3.JPG
coverCaption: "工大的天鹅"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/%E5%B7%A5%E5%A4%A7%E8%83%8C%E6%99%AF3.JPG
comments: false
title: CSS3实现居中(水平居中、垂直居中、水平垂直居中)
date: 2016-03-03 18:38:44
tags: [CSS3]
categories: [大前端技术栈]

---
本篇整理了CSS3实现居中(水平居中、垂直居中、水平垂直居中)的几种解决方案
<!-- more -->
***

# 学习网站

 * [CSS3实现垂直居中](http://vanseodesign.com/blog/demo/vertical-centering/line-height.php)
 
 * [极客标签居中教程](http://www.gbtags.com/gb/gbliblist/20.htm)
 
 * [w3cfuns居中教程]( http://www.w3cfuns.com/notes/17719/db6c906cd6acfa502e8bb8657fb75b2b.html)

 * [michael_codeopen居中代码](http://codepen.io/michaeljunlove/collections/popular/)


# 水平居中：行内元素解决方案

思路: 把行内元素包裹在一个属性display为block的父层元素中，并且把父层元素添加如下属性即可：text-align: center

适用元素:文字，链接，及其它inline或者inline-*类型元素（inline-block，inline-table，inline-flex）

``` markdown
//父元素
display:block;
text-align: center; 		
```


# 水平居中：块状元素解决方案

思路: 对于块状元素（display:block）来说，我们需要将它的左右外边距（即，margin-left，margin-right）设置为auto，即可实现块状元素的居中.

适用元素:块状元素，如(div, p, section 等等元素），即display属性为block的元素

注意：需要居中的块元素需要有固定的宽度，否则无法实现居中，因为占据100%宽度

``` markdown
//子元素
margin: 0 auto;		  		
```


# 水平居中：多个块状元素解决方案-inline-block+text-align

思路: 如果页面里有多个块状元素需要水平排列居中，可以将元素的display属性设置为inline-block，并且把父元素的text-align属性设置为center即可实现。

``` markdown
//父元素
text-align:center;
//子元素
display:inline-block; 		
```

# 水平居中：多个块状元素解决方案 -flex+justify-content


思路: 使用flexbox布局，只需要把待处理的块状元素的父元素添加属性display:flex及justify-content:center即可

``` markdown
//父元素
display:flex;
justify-content: center;		
```

# 垂直居中：单行的行内元素解决方案

思路: 当一个行内元素，即inline，inline-*类型的元素需要居中的话，可以将它的height和line-height同时设置为父元素的高度即可实现垂直居中效果。

``` markdown
//父元素
height: 200px;
//子元素
height: 200px;
line-height:200px; 		
```

# 垂直居中：多行的行内元素解决方案--table-cell+vertical-align

思路: 组合使用display:table-cell和vertical-align:middle属性来定义需要居中的元素的父容器元素生成效果

``` markdown
//父元素
display: table-cell;
vertical-align:middle;		
```
# 垂直居中：已知高度的块状元素解决方案

思路:将待居中元素设置为绝对定位，并且设置margin-top为居中元素高度一半的负值

``` markdown
//子元素
margin-top: -50px;
position: absolute;		
```
#  垂直居中：未知高度的块状元素解决方案-absolute+transform

思路:对于无法知道高度的元素，使用transform属性来垂直移动来实现垂直居中

``` markdown
//子元素
top: 50%;
position: absolute;
transform: translateY(-50%);		
```

# 以下为水平垂直居中

# DOM结构

``` markdown
<div id="parent">
       <div id="child">Text here</div>
</div>
```

# 1.Line Height

思路：给子节点设置一个大于`font-size`的`line-height`,通过`text-align`设置为`center`来实现垂直居中,这种方案仅支持单行的垂直居中，不支持多行的垂直居中。
``` markdown
<style type="text/css">
#parent {
        width: 400px;
        margin: 20px auto;
        background: #ccc;
}
#child {
        line-height: 200px;
        text-align: center;
}
</style>   
```

# 2.CSS Tables

思路：设置父节点的`display`为`table`，设置子节点的`display`为`table-cell`，然后通过子节点的`text-align`为`center`来实现垂直居中，支持多行的垂直居中。
``` markdown
<style type="text/css">
#parent {
        width: 400px;
        background: #ccc;
        height: 200px;
        margin: 20px auto;
        display: table;
}
#child {
        display: table-cell;
        vertical-align: middle;
        text-align: center;
}
</style>   
```

# 3.Position and Margin

思路：把父节点的`position`设置为`relative`，子节点`position`设置为`absolute`，`top`和`left`设置为`50%`,然后通过设置`margin-top`和`margin-left`为元素高度一半的负值来调整垂直居中的具体位置，这种方案支持块状的节点的垂直居中，一般建议采用这种解决方案。

``` markdown
<style type="text/css">
#parent {
       position: relative;
       width: 400px;
       margin: 20px auto;
       background: #ccc;
       height: 200px;
}
#child {
  	   position: absolute;
       top: 50%;
       left: 50%;
       height:30%;
       width:50%;
       margin: -100px 0 0 -100px;
       text-align: center;
       background: #999;
}
</style>   
```

# 4.Position and Margin(已知高度和宽度的元素解决方案)

思路：把父节点的`position`设置为`relative`，子节点的`top`, `bottom`, `left`, `right`都设置为0，因为子节点的宽度和高度都要比父节点小，所以呢，我们设置子节点的`margin`为`auto`就实现了垂直居中了，不过这种解决方案不支持IE7以下。

``` markdown
<style type="text/css">
#parent {
        position: relative;
        width: 400px;
        height: 200px;
        margin: 20px auto;
        background: #ccc;
}
#child {
       position: absolute;
       top: 0;
       bottom: 0;
       left: 0;
       right: 0;
       margin: auto;
       width: 50%;
       height: 30%;
       text-align: center;
       background: #999;
}
</style>
```

# 5.transform

思路：将设置元素绝对定位，并且设置transform的translate为Ｘ，Ｙ轴同时移动-50%即可

``` markdown
<style type="text/css">
.item{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
```
# 6.Padding

思路：主要是通过设置父节点的`top`和`bottom` 部分的`padding`来是的子节点居中，子节点的`top`和`bottom` 部分的`padding`来垂直居中子节点下面的内容。

``` markdown
<style type="text/css">
#parent {
        width: 400px;
        padding: 5% 0;
        margin: 20px auto;
        background: #ccc;
}
#child {
          padding: 10% 0;
          text-align: center;
          background: #999;
          color: #fff;
}
</style>
```

# 7.Float

思路：在父节点下面有一个空的`div`浮动节点，这个节点的高度设置为父节点的一半，在浮动节点下面是我们要垂直居中的节点（我们的目标节点），对这个节点进行清除浮动，这样目标节点就会紧贴在浮动节点后面，对浮动节点的`margin-bottom`设置一个目标节点高度一半的负数来使得目标节点垂直居中。

DOM结构如下：
``` markdown
<div id="parent">
  <div id="floater"></div>
  <div id="child">Content here</div>
</div>
```
CSS代码如下:
``` markdown
<style type="text/css">
  #parent {
    height: 250px;
    width: 400px;
    margin: 20px auto;
    background: #ccc;
  }
	#floater {
    float: left;
    height: 50%;
    width: 100%;
    margin-bottom: -50px;
    outline: 1px solid red;
  }
  #child {
    clear: both;
    height: 100px;
    outline: 1px solid yellow;
    text-align: center;
    background: #999;
    color: #fff;
  }
</style>
```
# 8.flex

思路：设置flex布局，并且定义居中元素的父元素justify-content和align-items属性为center即可

``` markdown
<style type="text/css">
.parent{
  display: flex;
  justify-content:center;
  align-items: center;  
  /* 注意这里需要设置高度来查看垂直居中效果 */
  background: #AAA;
  height: 300px;
}
</style>
```


