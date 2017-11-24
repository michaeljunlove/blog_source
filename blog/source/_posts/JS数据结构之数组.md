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
title: JS数据结构之数组
date: 2015-11-12 18:38:44
tags: [JS]
categories: [数据结构与算法]

---
JS的数组，非常的灵活，严格来说应该称之为对象，JS数组的元素不必是同一种数据类型
<!-- more -->
***
# 学习网站

 * [Mozilla Developer Network](http://mzl.la/1gmmlQ5)


# 创建一维数组

``` javascript
//方式一,推荐使用方式一效率高
var num=[];
//方式二
var num=new Array();
```
# 创建二维数组
``` javascript
//扩展JS数组对象，为其增加一个新的方法
Array.matrix=function(numrows,numcols,initial){
  var arr=[];
  for(var i=0;i<numrows;i++){
      var columns=[];
      for(var j=0;j<numcols;j++){
         columns[j]=initial;
      }
      arr[i]=columns;
  }
  reuturn arr;
}
var newarray=Array.matrix(5,5,0);
```
# 判断一个对象是否是数组

``` javascript
Array.isArray(num);
```
# 字符串 转 数组:split()

``` javascript
var sentence="hello michael jun love"
var arr=sentence.split(" ");//["hello","michael","jun","love"];
```
# 数组 转 字符串:join()和toString()

``` javascript
var arr=["hello","michael","jun","love"];
//方案一
var arrSre=arr.join();//hello,michael,jun,love
//去掉逗号
var arrSre=arr.join("");//hellomichaeljunlove
//方案二
var arrSre=arr.toString();//hello,michael,jun,love
```

# 由已有数组创建新数组：concat()和slice()

## concat 合并多个数组，创建新的数组
``` javascript
var arr1=["hello","michael"];
var arr2=["jun","love"];
var arr=arr1.concat(arr2);//["hello","michael","jun","love"]
```
## splice 截取一个数组的子集创建一个新的数组
``` javascript
//返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。
var arr=["hello","michael","jun","love"];
//["michael","jun"]
var test=arr.splice(1,2);
```
# 为数组添加元素：push()、unshift()、splice()
## push 将一个元素添加到数组末尾 
``` javascript
var arr=["hello","michael"];
arr.push("jun","love");
console.log(arr);//["hello","michael","jun","love"];
```
## 使用length属性为数组末尾添加元素 
``` javascript
var arr=["hello","michael"];
arr[arr.length]="jun";
console.log(arr);//["hello","michael","jun"];
```
## unshift 将一个元素添加到数组开头 
``` javascript
var arr=["hello","michael"];
arr.unshift("jun");
console.log(arr);//["jun","hello","michael"];
```
## splice 将多个元素添加到数组中间
``` javascript
var nums=[1,2,3,7,8,9];
var newElements=[4,5,6];
/*使用splice为数组添加元素，需提供如下参数
*起始索引，也就是你希望开始添加元素的地方
*要删除的元素的个数
*想要添加进数组的元素
*/
nums.splice(3,0,newElements);
console.log(nums);//1,2,3,4,5,6,7,8,9
```
# 为数组删除元素：pop()、shift()、splice()
## pop 将一个元素从数组末尾删除
``` javascript
var arr=["hello","michael"];
arr.pop();
console.log(arr);//["hello"];
```
## shift 将一个元素从数组首部删除
``` javascript
var arr=["hello","michael"];
arr.shift();
console.log(arr);//["michael"];
```
## splice 将一个元素从数组中间删除
``` javascript
var nums=[1,2,3,100,200,300,400,4,5];
/*使用splice为数组删除元素，需提供如下参数
*起始索引，也就是你希望开始添加元素的地方
*要删除的元素的个数
*/
nums.splice(3,4);
console.log(nums);//[1, 2, 3, 4, 5]
```

## pop和shift都将删掉的元素作为方法的返回值返回
``` javascript
var arr=["hello","michael",,"jun"];
var text1=arr.shift();
console.log(text1);//["hello"];
var text2=arr.pop();
console.log(text1);//["jun"];
```
# 查找元素:indexOf()、lastIndexOf()
## indexOf()用来查找传进来的参数是否在目标数组中存在
``` javascript
var arr=["hello","michael","jun","love"];
//如果存在，就返回索引，不存在返回-1.如果数组中包含多个相同的元素，indexOf总返回第一个相同元素的索引
var position=arr.indexOf("jun");
console.log(position);//2;
```
## lastIndexOf()用来查找传进来的参数是否在目标数组中存在
``` javascript
var arr=["hello","michael","jun","love"];
//如果存在，就返回索引，不存在返回-1.
//如果数组中包含多个相同的元素，lastIndexOf总返回最后一个相同元素的索引
var position=arr.indexOf("jun");
console.log(position);//2;
```

# 为数组排序:reverse()、sort()
## reverse()用来把数组中元素的顺序翻转
``` javascript
var nums=[1,2,3,4,5];
nums.reverse();
console.log(nums);//5,4,3,2,1
```
## sort()用来对字符串类型的数组按照字典顺序对元素排序
``` javascript
var arr=["hello","michael","jun","love"];
arr.sort();
console.log(arr);//["hello", "jun", "love", "michael"]
```
## sort()对数字类型进行排序
``` javascript
function compare(num1.num2){
  return  num1-num2;
}
var nums=[3,1,2,100,4,200];
nums.sort(compare);
console.log(nums);//[1,2,3,4,100,200]
```
# 迭代器方法
迭代器方法对数组中的每个元素应用一个函数，可以返回一个值、一组值、或者一个新数组。
* forEach()
* every()
* some()
* reduce()
* reduceRight()

## forEach()
forEach()方法接受一个函数作为参数，对数组中的每个元素使用该函数。
``` javascript
function square(num){
  print(num，num*num);
}
var nums=[1,2,3,4,5,6,7,8,9,10];
/*
*1 1
*2 4
*.....
*10 100
*/
nums.forEach(square);

```
## every()
every()方法接受一个返回值为bool类型的函数，对数组中的每个元素使用该函数
``` javascript
function isEven(num){
  return num%2==0;
}
var nums=[2,4,6,8,10];
var even=nums.every(isEven);
if(even){
   print("all numbers are 偶数");
}else{
   print("not all numbers are 偶数");
}
```
## some()
some()方法接受一个返回值为bool类型的函数，只要有一个元素使得该函数返回true，该方法就返回true
``` javascript
function isEven(num){
  return num%2==0;
}
var nums1=[2,4,6,8,10];
var nums2=[1,3,5,7,9];
var even1=nums1.some(isEven);//true
var even2=nums2.some(isEven);//false
```

## reduce()
reduce()方法接受一个函数，返回一个值。该方法会从一个累加值开始，不断对累加值和数组中的后续元素调用该函数，知道数组的最后一个元素，最后返回得到的累加值。
``` javascript
function add(total,item){
  return total+item;
}
var nums=[1,2,3,4,5,6,7,8,9,10];
var sum=nums.reduce(add);//55
```
reduce()方法也可以把数组中的元素连接成一个长的字符串
``` javascript
function add(total,item){
  return total+item;
}
var words=[“hello”,"michael","jun","love"];
var sentence=words.reduce(add);//"hello michael jun love"
```
## reduceRight()
reduceRight()方法和reduce()方法功能相同，只不过reduceRight()方法是从右往左边执行的。

## map()
map()方法对数组中的每个元素使用某个函数，返回一个新的数组，该数组的元素是对原有数组的元素使用某个函数得到的结果
``` javascript
function curve(item){
  return item+5;
}
var nums=[1,2,3,4,5];
var newnums=nums.map(curve);//[6,7,8,9,10]
```
## filter()
filter()方法，传入一个返回值为bool类型的函数，当对数组中的所有元素应用该函数，结果均为true时，该方法返回一个新的数组，这个新的数组包含应用这个函数后结果为true的元素。（和这个方法的名字和搭）
``` javascript
function isEven(num){
  return num%2==0;
}
function isOdd(num){
  return num%2!=0;
}
var nums1=[1，2，3，4，5，6，7，8，9，10];
var evens=nums.filter(isEven);//[2,4,6,8,10]
var odds=nums.filter(isOdd);//[1,3,5,7,9]
```