clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/%E5%B7%A5%E5%A4%A7%E8%83%8C%E6%99%AF6.JPG
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/%E5%B7%A5%E5%A4%A7%E8%83%8C%E6%99%AF6.JPG
coverCaption: "工大的落花"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/%E5%B7%A5%E5%A4%A7%E8%83%8C%E6%99%AF6.JPG
comments: false
title: HTML5之CANVAS
date: 2016-01-18 18:38:44
tags: [HTML5]
categories: [大前端技术栈]

---
CANVAS
<!-- more -->
***
# 学习网站

 * [Markdown学习网站](http://www.jianshu.com/collection/BDu5F8)

# Canvas与SVG
Canvas采用"立即模式"绘图。所谓立即模式即它会立刻将你指定的内容绘制到画布上，然后，它就立刻忘记了刚才绘制的内容。所以Canvas适合“绘画应用程序”，不需要去跟踪记录用户所绘制的图形。

SVG采用"保留模式"绘图，会维护一份所绘制图形对象的列表。SVG适合“画图应用程序”，可以让用户操作其所创建的图像对象。


# Canvas大小

默认的Canvas元素大小是300*150.
Canvas元素实际上有2套尺寸，一个是元素本身的大小，还有一个是元素绘图表面的大小。

1.通过以下方式设置的Canvas的宽度和高度的时候，实际上是同时需改了该元素本身的大小与元素绘图表面的大小
``` javascript
<canvas id='canvas' width='800' height='520'>
         Canvas not supported
</canvas>
```
2.如果通过CSS来设置Canvas元素的大小，只改变元素本身的大小，不影响绘图表面的大小。当Canvas元素本身的大小与绘图表面的大小不符合的时候，浏览器会自动对绘图表面进行缩放，使其符合Canvas元素的大小。
``` javascript
<style> 
  #canvas {
   width: 600px;  /* Sets only the width and height of  */ 
   height: 300px; /* the canvas element, not the drawing surface */
  }
</style> 
<canvas id='canvas'>
         Canvas not supported
</canvas>
```


# 鼠标坐标转换为Canvas坐标


``` javascript
function windowToCanvas(canvas, x, y) {
   var bbox = canvas.getBoundingClientRect();
   return { x: x - bbox.left * (canvas.width  / bbox.width),
            y: y - bbox.top  * (canvas.height / bbox.height)
          };
}```


# 将HTML控件放在CANVAS上
关于HTML控件，CANVAS规范说最好是优先考虑内置的HTML控件，不要自己去使用CANVAS画一个控件（我以前就喜欢自己画，哭。。。）因为后者的编码量增大了，把简单的事情复杂化了。

要想把HTML控件放在CANVAS上有以下几种解决方案：
方案一：HTML控件采用绝对定位方式，CANVAS采用相对定位方式（原理是采用绝对定位方式的元素将被绘制在采用相对定位方式的元素之上）

方案二：HTML控件和CANVAS都采用相对或绝对定位的方式，并且把HTML控件的DIV放在CANVAS标签之后。

方案三：HTML控件和CANVAS都采用相对或绝对定位的方式，设置HTML控件的z-index属性值比CANVAS的z-index属性大。
玻璃窗格的代码如下
(这个和工业设计有关，我可没这个美观能力可以写的出这样的效果啊)
``` css
#glasspane {
            position: absolute;
            left: 50px;
            top: 50px;
            padding: 0px 20px 10px 10px;
            background: rgba(0, 0, 0, 0.3);
            border: thin solid rgba(0, 0, 0, 0.6);
            color: #eeeeee;
            font-family: Droid Sans, Arial, Helvetica, sans-serif;
            font-size: 12px;
            cursor: pointer;
            -webkit-box-shadow: rgba(0,0,0,0.5) 5px 5px 20px;
            -moz-box-shadow: rgba(0,0,0,0.5) 5px 5px 20px;
            box-shadow: rgba(0,0,0,0.5) 5px 5px 20px;
         }
```


