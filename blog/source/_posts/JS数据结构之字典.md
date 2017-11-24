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
title: JS数据结构之字典
date: 2015-11-15 18:38:44
tags: [JS]
categories: [数据结构与算法]

---
字典是一种以键值对形式存储数据的数据结构
<!-- more -->
***
# 方法列表
| 方法名       | 用途          | 
| ------------- |:-------------:| 
| add()    | 加入键值对| 
| find()     | 根据键找到对应的值      | 
| remove() | 删除键值对    |   
| showAll() | 显示所有的键值对     |  
| count() | 字典中键的个数    |  
| clear() | 清空所有的键值对 |  

# 实现源码

``` javascript
function Dictionary() {
   this.datastore = new Array();
   this.add = add;
   this.find = find;
   this.remove = remove;
   this.showAll = showAll;
   this.count = count;
   this.clear = clear;
}
function add(key, value) {
   this.datastore[key] = value;
}
function find(key) {
   return this.datastore[key];
}
function remove(key) {
   delete this.datastore[key];
}
function showAll() {
   for each (var key in Object.keys(this.datastore).sort()) {
      console.log(key + " -> " + this.datastore[key]);
   }
}
function count() {
   var n = 0;
   for each (var key in Object.keys(this.datastore)) {
      ++n;
   }
   return n;
}
function clear() {
   for each (var key in Object.keys(this.datastore)) {
      delete this.datastore[key];
   } 
}
```



