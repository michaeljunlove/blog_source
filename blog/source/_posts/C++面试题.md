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
title: C++面试题
date: 2015-03-23 18:38:44
tags: [C++]
categories: [计算机基础]

---
C++
<!-- more -->
***

# 指针跟引用的区别

``` c
相同点：
 指针指向一块内存，它的内容是所指内存的地址；引用是某块内存的别名。
不同点：
 1.指针是一个实体，而引用仅是个别名；
 2.引用使用时无需解引用（*），指针需要解引用；
 3.引用只能在定义时被初始化一次，之后不可变；指针可变；
 4.引用没有 const，指针有 const，const 的指针不可变；
 5.引用不能为空，指针可以为空；
 6.“sizeof 引用”得到的是所指向的变量（对象）的大小，
 而“sizeof 指针”得到的是指针本身（所指向的变量或对象的地址）的大小；
```
