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
title: SVG学习笔记
date: 2015-11-20 18:38:44
tags: [SVG]
categories: [大前端技术栈]

---
SVG:可缩放矢量图形。简单地说呢，就是可以缩放，也不会损失图像质量的一种XML应用
<!-- more -->
***
# 学习网站

 * [W3C：SVG](http://www.w3.org/TR/2011/REC-SVG11-20110816/) 
 * [慕课网：走进SVG](http://www.imooc.com/learn/143)
 * [图灵：SVG精髓](http://oreillymedia.github.io/svg-essentials-examples/ch01/ex01-08.html)


# 位图与矢量图

计算机中有如下2种描述图形信息的两大系统
1.栅格图形
2.矢量图形

 * 位图：在栅格图形系统中，图像被表示为图片元素或者像素的长方形数组。每个像素用其RGB颜色值或者颜色表内的索引表示。位图是基于颜色的描述。
 * 矢量图：在矢量图形系统中，图像被描述为一系列的几何形状。矢量图像阅读器接受在制定坐标集上绘制形状的指令，而不是接受一系列已经计算好的像素。
 
 {% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/位图与矢量图.png
 "位图与矢量图" %}

# 在网页中使用SVG的4种方式
* 1.浏览器直接打开
* 2.在HTML中使用&lt;img>标签引入
``` markdown
<img src="simple.svg" />
```
* 3.直接在HTML中使用SVG标签
``` markdown
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
//具体要渲染的图形
</svg>
```
* 4.作为CSS的背景
``` markdown
* background-image
* list-image
* border-image
```
# 小试牛刀-SVG画各种图像

基础最重要嘛，下面我们来看看SVG都能画哪些形状

## -画线
 {% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/SVG直线坐标.png
 "SVG直线坐标" %}
``` javascript
//(x1,y1)表示起点坐标 (x2,y2)表示终点坐标
<line 
        x1="10" 
        y1="120" 
        x2="160" 
        y2="220" 
        stroke="red">
</line>
```

## -画矩形
 {% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/SVG矩形坐标.png
 "SVG矩形坐标" %}

``` javascript
<rect 
        x="10" 
        y="10" 
        rx="5" 
        ry="5" 
        width="150" 
        height="100" 
        stroke="red" 
        fill="none">
</rect>
```
## -画圆形
 {% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/SVG圆形坐标.png
 "SVG圆形坐标" %}
``` javascript
<circle 
        cx="250" 
        cy="60" 
        r="50" 
        stroke="red" 
        fill="none">
</circle>
```
## -画椭圆形
 {% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/SVG椭圆形坐标.png
 "SVG椭圆形坐标" %}
``` javascript
<ellipse 
        cx="400" 
        cy="60" 
        rx="70" 
        ry="50" 
        stroke="red" 
        fill="none">
</ellipse>
```
## -画折线
 {% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/SVG折线坐标.png
 "SVG折线坐标" %}
``` javascript
<polyline 
        points="250 120 
                300 220
                200 220"
        stroke="red"
        fill="none">
</polyline>
```
## -画多边形
 {% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/SVG多边形坐标.png
 "SVG多边形坐标" %}
 ``` javascript
<polygon 
        points="250 120 
                300 220
                200 220"
        stroke="red"
        stroke-width="5"
        fill="yellow"
        transform="translate(150 0)">
</polygon>
```
## -文字
 ``` javascript
<text x="80" 
      y="165" 
      style="font-family: sans-serif; font-size: 14pt;
      stroke: none; 
      fill: black;">Cat
</text>
```
# SVG坐标系统
世界：SVG的世界是一张无限大的画布。
视野(viewbox)：视野是观察世界的一个矩形区域。通过viewbox和preserveAspectRatio来控制视野。
视窗(视口)：浏览器开辟出来用于渲染SVG内容的区域。通过width和height控制视窗。