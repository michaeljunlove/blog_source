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
title: JS数据结构之链表
date: 2015-11-16 18:38:44
tags: [JS]
categories: [数据结构与算法]

---
数组的缺点是长度固定，添加和删除元素麻烦，因为需要重新移位。OK,本篇讲讲我最喜欢的链表吧。
<!-- more -->
***
# 方法列表
| 方法名       | 用途          | 
| ------------- |:-------------:| 
| find()    | 遍历链表，查找给定数据，找到则返回保存该数据的节点 | 
| insert()     | 插入一个节点     | 
| remove() | 删除一个节点     |   
| findPrevious() | 找到前驱节点     |  
| display() | 显示链表中的所有元素    |  
| deleteDuplecate() | 删除链表中的重复元素  |  


# 实现源码

``` javascript
//定义一个节点，element表示节点存储的内容，next表示指针
function Node(element) {
   this.element = element;
   this.next = null;
}
//定义LList类，用来提供链表的操作方法
function LList() {
   this.head = new Node("head");
   this.find = find;
   this.insert = insert;
   this.display = display;
   this.findPrevious = findPrevious;
   this.remove = remove;
}
//删除链表中包含某个值的节点
function remove(item) {
   var prevNode = this.findPrevious(item);
   if (!(prevNode.next == null)) {
       prevNode.next = prevNode.next.next;
   }
}
//找到链表中包含某个值的节点的前驱节点
function findPrevious(item) {
   var currNode = this.head;
   while (!(currNode.next == null) && 
           (currNode.next.element != item)) {
      currNode = currNode.next;
   }
   return currNode;
}
//打印链表中的所有元素
function display() {
   var currNode = this.head;
   console.log(currNode.element);
   while (!(currNode.next == null)) {
      console.log(currNode.next.element);
      currNode = currNode.next;
   }
}
//找到链表中包含某个值的节点
function find(item) {
   var currNode = this.head;
   while (currNode.element != item) {
      currNode = currNode.next;
   }
   return currNode;
}
//插入新的节点
function insert(newElement, item) {
   var newNode = new Node(newElement);
   var current = this.find(item);
   newNode.next = current.next;
   current.next = newNode;
}
//demo
var cities = new LList();
cities.insert("michael1", "head");
cities.insert("michael2", "michael1");
cities.insert("michael3", "michael2");
cities.insert("michael4", "michael3");
cities.display();//head,michael1,michael2,michael3,michael4
console.log();
cities.remove("michael3");
cities.display();//head,michael1,michael2,michael4
```
## 删除链表中的重复元素

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;思路：对链表进行双重循环遍历，外循环正常遍历链表，假设外循环当前遍历的节点为cur,内循环从cur开始遍历，如果碰到与cur所指向节点值相同，则删除这个重复的节点

```javascript
function deleteDuplecate(){
  var start=this.head;
  while(start!=null){
     var newStart=start;
     while(newStart.next!=null){
        if(start.element == newStart.next.element){
            newStart.next=newStart.next.next;
        }else{
            newStart=newStart.next;
        }
     }
  }
}
```

## 如何找出单链表中的倒数第K个元素

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;思路：采用一次遍历即可找到倒数的第K个元素，设置2个指针，让其中一个指针`back`比另外一个指针`prev`先前移K-1步，然后两个指针一起同时去遍历链表，直到`back`指针遍历到最后一个节点为止

```javascript
function findElem(head,k){
   if(k<1||k>this.length){
      return null;
   }
   var prev=this.head;
   var back=this.head;
   //让back前移k-1步
   for(var i=0;i<k-1;i++){
     back=back.next;
   }
   //让prev和back一起遍历，直到back遍历到最后一个节点为止
   while(back!=null){
     back=back.next;
     prev=prev.next;
   }
}
```

## 如何实现链表的反转

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;思路：比如链表的最后3个节点是：`X`,`Y`,`Z`。`X`节点之前的指针都已经指向前面的节点了，为了避免链表断开，需要在调整`Y`的`next`指针之前，把`Z`节点保存下来。所以呢，我们需要找到反转后链表的头结点，反转链表后的头节点就是原始链表的尾节点，即`next`指针为`null`的节点。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;使用`prev`，`temp`和`tempNext`三个指针来配合工作，进行反转，
```javascript
function reverseLList(){
   //temp用来遍历链表，找到最后一个节点
   var temp=this.head;
   //用来存放反转后的表头
   var ReversedHead=null;
   var prev=null;
   while(temp != null){
       //保存当前指针的下一个节点
       var tempNext=temp.next;
       //如果下一个节点为null，说明temp目前的位置是最后一个节点了.
       //设置ReversedHead为temp,把最后一个节点的引用保存下来。
       if(tempNext == null){
          ReversedHead=temp;
       }
       //把当前节点的指针指向prev节点
       temp.next=prev;
       //更新prev节点的位置为当前的节点
       prev=temp;
       //更新temp节点的位置为tempNext节点
       temp=tempNext;
   }
   this.head=ReversedHead;
}
```

