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
title: JS数据结构之树
date: 2015-11-13 18:38:44
tags: [JS]
categories: [数据结构与算法]

---
树，二叉树,二叉堆，二叉查找树，平衡二叉树，完全二叉树
<!-- more -->
***

# 基本概念

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`树`：树是由节点的有限集和有向边的有限集组成。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`二叉树`：树中每个节点至多只有2个子女。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`二叉堆`:父结点的键值总是大于或等于（小于或等于）任何一个子节点的键值。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-`最大堆`:当父结点的键值总是大于或等于任何一个子节点的键值时。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-`最小堆`:当父结点的键值总是小于或等于任何一个子节点的键值时。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;树和二叉树的2个主要差别：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. 树中结点的最大度数没有限制，而二叉树结点的最大度数为2；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. 树的结点无左、右之分，而二叉树的结点有左、右之分。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`二叉查找树`：父节点的值比左儿子节点值大，比右儿子节点值小。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`平衡二叉树`:一棵二叉查找树，其中每个节点的平衡因子是0，1，-1。所述平衡因子是X的左子树的高度减去X的右子树的高度。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`完全二叉树`:除最后一层外，每一层上的节点数均达到最大值；在最后一层上只缺少右边的若干结点。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`满二叉树`:除最后一层无任何子节点外，每一层上的所有结点都有两个子结点或0个子节点的二叉树。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`树的深度`：树的最大层次就是深度，深度为k的树，拥有的最大结点数是2的k次方减1。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`树的遍历`：以某种特定的顺序访问树中的所有节点


|    字母    | 描述           | 
| ------------- |:-------------:| 
| V    | 访问节点| 
| L     | 遍历节点的左子树  | 
| R| 遍历节点的右子树      | 
## 树的遍历：

|    字母    | 描述           | 
| ------------- |:-------------:| 
| LVR    | 中序遍历| 
| VLR     | 前序遍历 | 
| LRV| 后序遍历      | 
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E9%81%8D%E5%8E%86%E6%A0%91.jpg "遍历树" %}



# 二叉查找树(BST)

``` javascript
//节点类Node
function Node(data, left, right) {
   this.data = data;
   this.left = left;
   this.right = right;
   this.show = show;
}
//用来显示保存在节点中的数据
function show() {
   return this.data;
}
//二叉查找树类BST
function BST() {
   this.root = null;
   this.insert = insert;
   this.inOrder = inOrder;
   this.preOrder = preOrder;
   this.postOrder = postOrder;
   this.getmin = getmin;
   this.getmax = getmax;
   this.find = find;
   this.remove = remove;
   this.removeNode = removeNode;
   this.getSmallest = getSmallest;
}
//insert方法用来向树中加入新节点
function insert(data) {
   var n = new Node(data, null, null);
   if (this.root == null) {
      this.root = n;
   }
   else {
      var current = this.root;
      var parent;
      while (true) {
         parent = current;
         if (data < current.data) {
            current = current.left;
            if (current == null) {
               parent.left = n;
               break;
            }
         }
         else {
            current = current.right;
            if (current == null) {
               parent.right = n;
               break;
            }
         }
      }
   }
}
//中序遍历
function inOrder(node) {
   if (!(node == null)) {
      inOrder(node.left);
      putstr(node.show() + " ");
      inOrder(node.right);
   }
}
//先序遍历
function preOrder(node) {
   if (!(node == null)) {
      putstr(node.show() + " ");
      preOrder(node.left);
      preOrder(node.right);
   }
}
//后序遍历
function postOrder(node) {
   if (!(node == null)) {
      postOrder(node.left);
      postOrder(node.right);
      putstr(node.show() + " ");
   }
}
//查找最小值
function getmin() {
   var current = this.root;
   print("debug: " + current.data);
   while (!(current.left == null)) {
      current = current.left;
   }
   return current.data;
}
//查找最大值
function getmax() {
   var current = this.root;
   while (!(current.right == null)) {
      current = current.right;
   }
   return current.data;
}
//查找给定值
function find(data) {
   var current = this.root;
   while (current.data != data) {
      if (data < current.data) {
         current = current.left;
      }
      else {
         current = current.right;
      }
      if (current == null) {
         return null;
      }
   }
   return current;
}
function getSmallest(node) {
   if (node.left == null) {
      return node;
   }
   else {
      return getSmallest(node.left);
   }
}
//删除给定数据的节点
function remove(data) {
   root = removeNode(this.root, data);
}
function removeNode(node, data) {
   if (node == null) {
      return null;
   }
   if (data == node.data) {
      // node has no children
      if (node.left == null && node.right == null) {
         return null;
      }
      // node has no left child
      if (node.left == null) {
         return node.right;
      }
      // node has no right child
      if (node.right == null) {
         return node.left;
      }
      // node has two children
      var tempNode = getSmallest(node.right);
      node.data = tempNode.data;
      node.right = removeNode(node.right, tempNode.data);
      return node;
   }
   else if (data < node.data) {
      node.left = removeNode(node.left, data);
      return node;
   }
   else {
      node.right = removeNode(node.right, data);
      return node;
   }
}
```


