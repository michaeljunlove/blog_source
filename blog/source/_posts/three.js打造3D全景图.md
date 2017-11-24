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
title: three.js打造3D全景图
date: 2017-06-06 18:38:44
tags: [three.js]
categories: [大前端技术栈]

---
three.js
<!-- more -->
***
# 学习网站

 * [Three.js官网](https://threejs.org/)
 * [threejs 文档官网](https://threejs.org/docs/)
 * [Three.js入门指南](http://www.ituring.com.cn/book/1272)
 * [krpano360](http://www.krpano360.com/)
 * [react-vr](https://github.com/facebook/react-vr)
 * [react-vr](https://facebook.github.io/react-vr/)
 * [打造H5里的“3D全景漫游”秘籍](https://isux.tencent.com/3d.html)
 * [使用ThreeJS在浏览器中展示全景图](https://aotu.io/notes/2016/01/02/3D-panorama/?utm_source=tuicool&utm_medium=referral)
 * [ThreeJS 轻松实现主视觉太阳系漫游](https://zhuanlan.zhihu.com/p/20796329)
 * [webvr.info](https://webvr.info/)
 * [全景漫游面面观-首届TGDC-前端专场](https://wx.abbao.cn/a/9777-8e10cb9bcda4426c.html)
 * [ThreeJS_demo]( https://stemkoski.github.io/Three.js/)


 

# 什么是全景漫游

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;全景漫游技术可以让体验者在全景图像构建的全景空间里切换视角的浏览。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;实现360度全景漫游的有3种方法，1）球形图、2）圆柱图、3）正方体。 

# 渲染器（Renderer）
# 场景（Scene）
# 照相机（Camera）:控制投影方式

## 正交投影照相机（Orthographic Camera）

## 透视投影照相机（Perspective Camera）

## 视景体（Frustum）
只有在视景体内部（下图中的灰色部分）的物体才可能显示在屏幕上，而视景体外的物体会在显示之前被裁减掉。

针对投影方式的不同，照相机又分为正交投影照相机与透视投影照相机,一般说来，对于制图、建模软件通常使用正交投影，这样不会因为投影而改变物体比例；而对于其他大多数应用，通常使用透视投影，因为这更接近人眼的观察效果。

一个典型的Three.js程序至少要包括渲染器（Renderer）、场景（Scene）、照相机（Camera），以及你在场景中创建的物体。
WebGL和Three.js使用的坐标系是右手坐标系

在创建物体时，需要传入两个参数，一个是几何形状（Geometry），另一个是材质（Material）

全景图像可分为球面全景图、立方体全景图以及柱状全景图。

