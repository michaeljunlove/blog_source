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
title: JS基础
date: 2015-02-23 18:38:44
tags: [JS]
categories: [大前端技术栈]

---
本篇整理我在各类JS书上看到的一些小技巧，有些知识点，可能我们看了，了解了，但是没想到可以这样用，所以都整理到本篇中。
<!-- more -->
***
# 学习网站

 * [JavaScript data types and data structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
 
 * [360_JS进阶课程]( http://matrix.h5jun.com/slide/show?id=111#/)
 
 






# JS类型

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/JS%E7%B1%BB%E5%9E%8B.svg "JS类型" %}



# JS类型识别

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/JS%E7%B1%BB%E5%9E%8B%E8%AF%86%E5%88%AB.png "JS类型识别" %}


<h3 style="color:red;">Object.prototype.toString可以识别标准类型以及内置对象类型,不能识别自定义类型+instanceof来判断对象类型</h3>

``` javascript
function type(obj){
  return Object.prototype.toString.call(obj).slice(8, -1).toLowerCase(); 
}
```
# 判断实例是否与原型对象之间存在关系
``` javascript 
//返回true，则表示实例中的[[Prototype]]指向了原型对象
原型对象.isPrototypeof(实例)
```

## 类型识别的作用

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JS是一种弱类型语言，类型识别可提高程序的健壮性，强类型更能够保证可靠性和稳定性，并减少潜在的错误。


# JS类型转换

<h3 style="text-align:center">JS类型转换-Underfined</h3>

| 值      | Boolean           | Number  |String  |
| ------------- |:-------------:| -----:| -----:|
| Underfined   | false |NaN |"Underfined" |

<h3 style="text-align:center">JS类型转换-Null</h3>


| 值      | Boolean           | Number  |String  |
| ------------- |:-------------:| -----:| -----:|
| Null   | false | 0 |"null" |

<h3 style="text-align:center">JS类型转换-Boolean</h3>


| 值      | Number  |String  |
| ------------- | -----:| -----:|
| true   | 1 |"null" |
| false   | 0 |"false" |

<h3 style="text-align:center">JS类型转换-String</h3>

| 值      | Boolean           | Number  |
| ------------- |:-------------:| -----:|
| 空字符串""   | false | 0 |
| 非空字符串"123"   | true | 123 |
| 非空字符串"1a"   | true | NaN |

<h3 style="text-align:center">JS类型转换-Number</h3>

| 值      | Boolean           |String  |
| ------------- |:-------------:|-----:|
| 0   | false |"0" |
| 1   | true |"1" |
| infinity   | true |"infinity" |
| NaN   | false |"NaN" |

<h3 style="text-align:center">JS类型转换-Object</h3>

| 值      | Boolean           | Number  |String  |
| ------------- |:-------------:| -----:| -----:|
| {}   | true | NaN |"[object Object]" |

# 动态的访问对象的属性和方法

``` javascript
//访问object.properyName
object['properyName']
//访问object.methodName(arg1)
object['methodName'](arg1)
//根据行为来访问,或者可以拼接字符串
element[(isIE ? 'add' : 'remove')+'ClassName']();
```

# 立即执行表达式

``` javascript
    //立即执行表达式
    ;(function(){}(。。。))
    //立即执行表达式,()这个叫分组运算符，返回里面的函数，最后面的()表示执行该函数。
    (function myfunc(){})();
```
# 模块模式
主要是为了编写自包含，不透明的JS代码，它不会对外暴露内部的一些细节。

![](http://7xid80.com1.z0.glb.clouddn.com/JS对象.PNG)

``` javascript    
    //代码结构
    var obj=(function(){          
             }()           
            )();
    //demo
    var Person=( function(){
                    //私有的属性,只有私有方法才可以访问
                    var age=24;
                    //私有方法
                    this.getAge = function(){
                        return age;
                    }
                 }()
               )();
    //公有的方法：
    Person.prototype.sayHi = function()    { console.log("HI"); } 
    //公有的属性
    Person.prototype.legs=2;
    //静态的属性
    Person.population = 0;
```
# 克隆对象

``` javascript 
//如果A对象是从B对象克隆而来的，那么B对象就是A对象的原型
//ECMAScript提供了Object.create方法来克隆对象
var a=Object.create(b);
//在不支持Object.create方法的浏览器中，可以使用如下代码
Object.create=Object.create||function(obj){
   var F=function(){};
   F.prototype=obj;
   return new F();
}
```

# 判断属性在实例中还是原型中

``` javascript 
//返回true,说明该属性在原型中，false说明在实例中
function hasProtypePropertype(object,name){
  //in操作符只要对象能访问到该属性就返回true,hasOwnProperty只有属性在实例中时候才返回true
  return !object.hasOwnProperty(name)&&(name in object)
}
```
# 得到某实例的原型对象

``` javascript 
Object.getPrototypeof(实例)
```
# 修改默认属性的特性
``` javascript 
//属性指数据属性、访问器属性
//数据属性：[[Configurable]]，[[Enumerable]],[[Writable]],[[Value]]
//访问器属性：[[Configurable]],[[Enumerable]],[[Get]],[[Set]]
var person={};
person.name="michael";
//定义一个属性
Object.defineProperty(属性所在的对象person，属性的名字name，描述符对象{writable:false});
//定义多个属性
Object.defineProperties();
```
# 读取属性的特性

``` javascript 
Object.getOwnPropertyDescriptor(属性所在的对象，属性名称);
```


# 判断一个属性是在实例中还是原型对象中
``` javascript 
//for-in循环时，返回的是所有能够通过对象访问的、可枚举的属性,屏蔽了不可枚举的属性
//所以包括在实例中的属性，也包括在原型对象中的属性。
for(var prop in obj){
    // 实例.hasOwnProperty(属性),只有属性存在于实例中才返回true
    if(obj.hasOwnProperty(prop)){
        // do something here
    }
}
```

# 取得对象(原型对象、实例对象)上可枚举的属性
``` javascript 
//返回一个包含所有可枚举属性的字符串数组
Object.keys(传入原型对象或者实例对象);
```
# 取得对象(原型对象、实例对象)上可/不可枚举的属性
``` javascript 
//返回一个包含所有可枚举属性的字符串数组
Object.getOwnPropertyNames(传入原型对象或者实例对象);
```
# 动态创建命名空间

``` javascript 
var MyApp={};
MyApp.namespace=function(){
   var parts=name.split(',');
   var current=MyApp;
   for(var i in parts){
       if(!current[parts[i]]){
          current[parts[i]]={};
       }
       current=current[parts[i]];
   }
};
MyApp.namespace('event');
```

# 安全的从深层数据结构取值 兼容immutable对象 若不存在则返回null

``` javascript 
import { 
  isImmutable, 
  Iterable
} from 'immutable' 

// 兼容3.8.1及以下的immutable
const _isImmutable = obj => 
  isImmutable 
  ? isImmutable(obj) 
  : Iterable.isIterable(obj)

// 获取数据类型
const _getObjType = obj => 
  Object.prototype.toString.call(obj).slice(8, -1)

// key为数组
const _getArrayObj = (keys, obj) => 
  keys.reduce((prev, curr) => {
    if (!prev) return null
    return _isImmutable(prev)
    ? (prev.get(curr) || null)
    : (prev[curr] || null)
  }, obj)

// key为字符串
const _getStringObj = (key, obj) => 
  _isImmutable(obj)
  ? (obj.get(key) || null)
  : (obj[key] || null)

 /** 安全的从深层数据结构取值 兼容immutable对象 若不存在则返回null
  *  @keys 取值数组或字符串 例如 ['a', 'b', 0] || 'a'
  *  @obj 将要取值的对象 
  **/
export default function safelyGet (keys, obj) {
  if (!obj) return null
  const paramsType = _getObjType(keys)
  if (paramsType === 'Array') {
    return _getArrayObj(keys, obj)
  } else if (paramsType === 'String') {
    return _getStringObj(keys, obj)
  } else return null
}

// test
// const a = { b: { c: 1, d: 2, e: [3, 4] }, f: 5 }
// safelyGet('f', a) -> 5
// safelyGet(['b', 'e', 0], a) -> 3
// safelyGet(['b', 'c', 'd', 'e', 'f'], a) -> null


```
