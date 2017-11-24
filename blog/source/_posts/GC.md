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
title: GC
date: 2016-08-19 18:38:44
tags: [GC]
categories: [大前端技术栈]

---
Garbage Collection，简称GC，是计算机中进行内存管理的管理者
<!-- more -->
***
# 学习网站

 * [A tour of V8: Garbage Collection](http://jayconrod.com/posts/55/a-tour-of-v8-garbage-collection)
 
 
 * [V8_blog](http://v8project.blogspot.com/)


# 一些专业术语
内存泄漏：内存空间在使用完毕后未释放
循环引用：2个及2个以上对象循环互相引用(如下面这个例子)

``` javascript
var objectA= new Object();
var objectB= new Object();
objectA.someOtherObject=objectB;
objectB.anotherObject=objectA;
```
mutator:主要进行生成对象和更新指针这2个操作。
# GC是什么

>所谓的垃圾，就是内存中不会再被使用的部分.它不仅影响内存使用的增长，也会在运行不畅的时候影响 CPU 的利用，进而影响程序的可用性和响应速度。

# GC做什么


1.找到内存空间里的垃圾
2.回收垃圾，让程序员能再次利用这部分空间




# GC标记清楚算法

GC标记清楚算法是由标记阶段和清楚阶段构成。
标记阶段是把所有活动对象都做上标记的阶段。
清楚阶段是把那些没有标记的对象，也就是非活动对象回收的阶段。

标记阶段：collector会为堆里面的所有活动对象打上标记。标记所花费的时间是与“活动对象的总数”成正比。

清楚阶段：collector会遍历整个堆，从堆首地址开始，按顺序一个个遍历对象的标志位，回收没有打上标记的对象，使其能得到再次利用。

# GC复制算法

>From空间：复制活动对象的原空间
To空间：粘贴活动对象的新空间
From空间与To空间大小一致，保证可以把From空间中的所有对象都收纳到To空间中。

GC复制算法就是把某个空间里的活动对象复制到其他空间，把原来空间里的所有对象都回收掉。当From空间被完全占满时，GC会将活动对象全部复制到To空间。当复制完成后，该算法会把From空间和To空间互换，GC就结束了。



# GC标记压缩算法

GC标记压缩算法是GC标记清楚算法与GC复制算法结合的产物，由标记阶段和压缩阶段构成。

# V8的GC算法
>分代垃圾回收：在对象中导入了“年龄”的概念，通过优先回收容易成为垃圾的对象，提高垃圾的回收效率。这是因为大部分的对象在生成后马上就变成了垃圾，很少有对象能活的很久。

>准确式GC：能正确识别指针和非指针的GC

V8采用准确式GC，GC算法方面采用了分代垃圾回收。
