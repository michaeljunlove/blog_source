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
title: JS数据结构之栈
date: 2015-11-19 18:38:44
tags: [JS]
categories: [数据结构与算法]

---
栈嘛，后入先出的数据结构，主要应用在数制间的相互转换、回文以及递归的演示。
<!-- more -->
***


# 栈

``` markdown
//定义一个栈类
function Stack(){
    this.dataStore = []
    this.top    = 0;
    this.push   = push
    this.pop    = pop
    this.peek   = peek
    this.length = length;
}
//在栈顶插入元素
function push(element){
    this.dataStore[this.top++] = element;
}
//得到栈顶元素的值
function peek(element){
    return this.dataStore[this.top-1];
}
//删除栈顶元素
function pop(){
    return this.dataStore[--this.top];
}
//清空栈的元素
function clear(){
    this.top = 0
}
//返回栈的长度
function length(){
    return this.top
}
```


