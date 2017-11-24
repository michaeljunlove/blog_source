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
title: JS数据结构之队列
date: 2015-11-17 18:38:44
tags: [JS]
categories: [数据结构与算法]

---
队列是一种列表，不同的是队列只能在队尾插入元素，在队首删除元素，是一种先进先出的数据结构。
<!-- more -->
***
# 方法列表
| 方法名       | 用途          | 
| ------------- |:-------------:| 
| enqueue()    | 向队尾插入一个元素 | 
| dequeue()     | 删除队首元素      | 
| front() | 读取队首元素     |   
| back() | 读取尾元素     |  
| toString() | 显示队列中的所有元素    |  
| empty() | 判断队列是否为空  |  

# 实现源码

``` javascript
function Queue() {
    this.dataStore = [];
    this.enqueue   = enqueue;
    this.dequeue   = dequeue;
    this.first     = first;
    this.end       = end;
    this.toString  = toString;
    this.empty     = empty;
}
function enqueue(element) {
    this.dataStore.push(element);
}
function dequeue() {
    return this.dataStore.shift();
}
function first() {
    return this.dataStore[0];
}
function end() {
    return this.dataStore[this.dataStore.length - 1];
}
function toString() {
    var retStr = "";
    for (var i = 0; i < this.dataStore.length; ++i) {
        retStr += this.dataStore[i] + "\n";
    }
    return retStr;
}
function empty() {
    if (this.dataStore.length == 0) {
        return true;
    } else {
        return false;
    }
}
var q = new Queue();
q.enqueue("michael1");
q.enqueue("michael2");
q.enqueue("mihcael3");
console.log("队列头: " + q.first());//("michael1");
console.log("队列尾: " + q.end());  //("mihcael3");
```



