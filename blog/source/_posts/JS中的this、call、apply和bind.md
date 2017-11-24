clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/草坪.jpg
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/草坪.jpg
coverCaption: "工大的大草坪"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/草坪.jpg
comments: false
title: JS中的this、call、apply和bind
date: 2015-10-19 18:38:44
tags: [JS]
categories: [大前端技术栈]

---
JS中的this代表的是一个函数的上下文环境，这个上下文环境在大多数的情况下指的是函数运行时封装这个函数的那个对象。重要的事情说三遍：这个上下文环境在大多数的情况下指的是函数运行时封装这个函数的那个对象，这个上下文环境在大多数的情况下指的是函数运行时封装这个函数的那个对象，这个上下文环境在大多数的情况下指的是函数运行时封装这个函数的那个对象。在JS中，由于this 是动态绑定，或称为运行期绑定的，这就导致 JS 中的 this 关键字有能力具备多重含义，带来灵活性。
<!-- more -->
# 学习网站

 * [this学习网站](http://www.imooc.com/article/1758)
 
 * [谜之this]( http://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651222118&idx=1&sn=f1cb84a1f74ab48534aa5a20a25e1c89&scene=0#wechat_redirect)
 
 * [【第765期】你不懂JS：this豁然开朗！](https://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651223924&idx=1&sn=d04be77d8a1e59a5cac285128161e7f1&chksm=bd49aef08a3e27e69ab27f47ea151d462620810ef05cbb558ce9418c507f01c24d9e13ed7d95&mpshare=1&scene=1&srcid=1213OZLnZYWGp2dFmwJQMtUW&pass_ticket=NDJ2BXY%2BoEeV2TlaS4UM22%2FTJzoxzETApfvGMlHwmKlnm%2F%2FHnpymyAySn0sUqojI#rd)
  


 * [MDN_bind](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
 
 * [MDN_this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this
)
  
# this的应用场景
this的应用场景大致分为以下4种
* 作为普通函数调用
* 作为对象的方法调用
* 作为构造器调用
* call或apply调用
    
# 1.作为普通函数调用---this指window对象（全局上下文）

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当不通过任何对象单独调用一个函数的时候，this指的是全局的window对象

``` javascript
alert(this===window);//true;   
//因为运行doit这个函数的对象为window
function doit(){
        alert(this===window);//true;
}
doit();    
```

    
# 2.作为对象的方法调用---this指包含这个方法的那个对象

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在一个对象的方法中的this指的是该对象
``` javascript
var house={
       floors:2;
       isLocked:false;
       lock:function(){
          alert(this===house);//true;包含这个方法的那个对象
          this.isLocked=true;
       }
}
   
```
``` javascript
window.name='michaeljunlove';
var myObject={
    name:'sven',
    getName:function(){
      	  	return this.name;
    }
};
var getName=myObject.getName;
console.log(getName());  //michaeljunlove 
console.log(myObject.getName());//sven       
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<h3 style="color:red">需要注意的是对象中嵌套函数，其上下文环境是全局的window对象，而不是包含它的那个对象。</h3>
``` javascript
var apartment={
       isLocked=false;
       lock:function(){
           var that=this;//保存this的引用
           this.isLocked=true;
           //嵌套函数
           function doIt(){
             alert(this===apartment);//false;
             alert(this===window);//true;对象中的嵌套函数this指向全局的window对象
             alert(that===apartment);//true;
             //要用that来而不是this;
             that.isLocked=false;
           }           
       }
}   
```
# 3.作为构造器调用---new关键字下this指的是创建出来的对象实例
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;正因为这个特性，我们才可以在构造函数中通过this来设置所有实例对象的属性和方法。

``` javascript
function Accommodation(){
      //this指的是通过这个类创建出来的对象实例
      this.isLocked=false;
      this.lock=function(){
         this.isLocked=true;
      }
    }
var house=new Accommodation();
```

<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;需要注意的是，如果构造器显示地返回了一个object类型的对象，那么此次运算结果最终返回这个对象，而不是我们期待的this。只要构造器不显示地返回任何数据，或者是返回一个非对象类型的数据，就不会造成这个问题。
``` javascript
var MyClass=function(){
    this.name='michaeljunlove';
    return {
      name:'michael'
    }
};
var obj=new MyClass();
console.log(obj.name);//michael
```
# this实现链式调用

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通过返回上下文，实际上返回的调用这个函数的那个对象实例的引用，就可以实现链式调用了。
``` javascript
function Accommodation(){}    
Accommodation.prototype.isLocked=false;
Accommodation.prototype.lock=function(){
        this.isLocked=true;       
        return this;
}
Accommodation.prototype.unLocked=fucntion(){
        this.isLocked=false;      
        return this;
}
Accommodation.prototype.alarm=function(){
        alert("alarm");
        return this;
}
var  house=new Accommodation();
//链式调用
house.lock().alarm().unlock();
```
        
# this实现多态
``` javascript
//定义一个父类Accommodation
function Accommodation(){
      this.isLocked=false;
      this.isAlarmed=false;
}
//添加一个lock方法
Accommodation.prototype.lock=function(){
      this.isLocked=true;
}    
//定义一个子类
function House(){}
//继承自父类
House.prototype=new Accommodation();    
//多态
House.prototype.lock=function(){
//call方法将一个函数的上下文应用到另外一个函数身上
//小技巧：将当前函数的所有参数直接通过arguments这个伪数组传递给父类的函数，无需将这些参数一一列出。    

  Accommodation.prototype.lock.call(this,arguments);     
      alert(this.isLocked);//true;
}    
```

# 丢失的this
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;利用apply方法把document当做this传入getid函数，帮助修正this

``` javascript
document.getElementById=(
   function(func){
       return function(){
          func.apply(document,arguments);
       }
   }
)();
var getid=document.getElementById;
var div=getid('div1');
```
# call、apply、bind
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;call和apply的用途主要由如下几种方式
* 改变this的指向
* 借用其他对象的方法

## call和apply的区别
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;仅在于传入参数的形式不同。他们的第一个参数都是用来指定this对象的指向。如果第一个参数传入null,则代表this指向window了。
## bind和apply、call的区别
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bind不会立即调用,bind会创建一个新函数，称为绑定函数，当调用这个函数的时候，绑定函数会以创建它时传入bind（）方法的第一个参数作为this，传入bind（）方法的第二个及以后的参数加上绑定函数运行时本身的参数按照顺序作为原函数的参数来调用原函数

``` javascript
Object.call(this,obj1,obj2,obj3)
Object.apply(this,[数组])
函数.bind(函数的调用者, 普通参数1, 普通参数2, ...);
```

# arguments.callee()方法

[MDN命名函数表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/function)

[arguments.callee](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments/callee)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;功能：arguments.callee是当前被调用函数自身引用，主要用于匿名函数调用时访问函数本身，可以实现匿名函数的递归，比如用匿名函数计算某个整数阶乘这样的功能。 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;产生原因及现状：早期的js版本不允许命名函数表达式，因此不能构造一个递归的函数表达式，为此引入了arguments.callee这样一个属性，但实际上这是一个糟糕解决方案，ES3通过命名函数表达式方式解决了函数递归的问题。callee在ES5严格模式中是被禁用的。 


# 函数

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;每次看见functionName(xxx)的时候，你需要在脑海中把它替换为functionName.call(window,xxxx)，这对你理解this的指向非常重要

``` javascript
(function(name) {   
})("aa");
//等价于
(function(name) {
}).call(window, "aa");
```
    