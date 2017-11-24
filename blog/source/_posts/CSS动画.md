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
title: CSS动画
date: 2016-04-10 18:38:44
tags: [CSS3]
categories: [大前端技术栈]

---
CSS3动画相关的属性
<!-- more -->
***
# 学习网站

 * [前端动画原理与实现-月影](http://matrix.h5jun.com/slide/show?id=117#/)
 
 * [CSS动画实用技巧-慕课网](http://www.imooc.com/learn/357) 
 
 * [Transform]( http://www.w3cplus.com/content/css3-transform) 

 * [Transition](http://www.w3cplus.com/content/css3-transition) 
 
 * [Animation]( http://www.w3cplus.com/content/css3-animation) 

 * [CSS Sprites Generator](https://www.toptal.com/developers/css/sprite-generator) 

 


 



# Transition

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;transition过渡属性允许CSS的属性值在一定的时间区间内从属性开始值到属性结束值平滑地过渡。这种效果可以在鼠标点击、获得焦点、被点击或对元素任何的改变中触发，并平滑地以动画效果改变CSS的属性值。

``` markdown
transition: <过渡属性> <过渡所需时间> <过渡动画函数> <过渡延迟时间>
 -property(过渡的属性)//指定当属性值改变时发生transition效果
 -duration(完成过渡的时间)//始终设置 transition-duration 属性，否则时长为 0，就不会产生过渡效果
 -timing-function(过渡函数)
 -delay(过渡开始出现的延迟时间)
```
# Transform

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;transform变形属性向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜。
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/transform.png "Transform" %}
## 举个小例子吧

 <link rel="stylesheet" type="text/css" href="http://7xid80.com1.z0.glb.clouddn.com/transition.css" /> 
<a href="http://image.haosou.com/i?q=%E5%AB%A6%E5%A8%A5png&src=tab_www" class="change " target="_blank">
  		<img src="http://p4.qhimg.com/t0160e6a92121691e22.png" alt="" />
	</a>
	``` javascript
//1.设置嫦娥图片的初始样式状态,这里对opacity和transform两个过渡元素都设置了初始样式。
//透明度为0不可见，transform把图片移到了左上角的位置处。
opacity:0;-webkit-transform:translate(-100px,-100px);
//2.添加触发条件，比如这里是:hover触发的
//2.1设置过渡元素的最终样式，这里把图片透明度设为1可见了，也取消了变形的效果。
opacity:1;
-webkit-transform:translate(0px,0px);	
//2.2设置哪些元素需要过渡
transition: opacity 1s ease-in-out 0.5s,
            transform 1s ease-in-out;
```


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;使用transition无法实现的动画需求：
1.动画中间无法插入新的关键帧
2.页面载入的时候，自动触发动画

# Animation

``` javascript
animition:
 -name //动画属性名，也就是keyframes定义的动画名
 -animation-duration //动画持续时间
 -animation-timing-function //动画函数
 -animation-delay//动画延迟时间
 —animation-iteration-count//定义循环次数，infinite为无限次
 -animation-direction//定义动画方式,alternate为往返执行动画
 -play-state//控制动画的状态
 -fill-mode//动画在开始的时候，结束的时候，处于什么状态
```



