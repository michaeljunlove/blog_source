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
title: ES6之Promise
date: 2016-06-02 18:38:44
tags: [Promise]
categories: [大前端技术栈]

---
Promise入门
<!-- more -->
***
# 学习网站

 * [阮一峰_Promise对象](http://es6.ruanyifeng.com/#docs/promise)(基础)

 * [JavaScript Promise迷你书（中文版）](http://liubin.org/promises-book/)(推荐)
 
 * [MDN_Promise](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)
 
 * [廖雪峰_Promise](  http://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/0014345008539155e93fc16046d4bb7854943814c4f9dc2000)
 
 * [bluebirdjs官方api](http://bluebirdjs.com/docs/api-reference.html)


# 目前Promise的实现库

1. * [q](https://github.com/kriskowal/q)
2. * [bluebirdjs异步库]( http://bluebirdjs.com/docs/why-bluebird.html)
3. * [co]( https://github.com/tj/co)
4. * [when]( https://github.com/cujojs/when)

# Promise诞生的背景
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;一谈到JavaScript的异步处理，大家肯定会立刻想到回调函数和事件。但是事件的特点是，如果你错过了它，再去监听，是得不到结果的，而回调存在以下问题：

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.回调函数嵌套，导致代码不够直观，就是常说的 Callback Hell。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.如果几个异步操作之间并没有前后顺序之分（例如不需要前一个请求的结果作为后一个请求的参数）时，同样需要等待上一个操作完成再实行下一个操作。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Promise是把类似的异步处理对象和处理规则进行规范化,并按照采用统一的接口来编写，而采取规定方法之外的写法都会出错,promise的功能是可以将复杂的异步处理轻松地进行模式化,Promise最大的好处是在异步执行的流程中，把执行代码和处理结果的代码清晰地分离了.一个 Promise 对象可以理解为一次将要执行的异步操作。

# 什么是Promise

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;用白话版本来解释就是把你的异步操作用Promise对象包装一下，这样就规范化了异步的处理流程,然后通过 then 和 catch 来分别注册成功回调函数和失败回调函数。

# 创建Promise对象，Promise新建后就会立即执行
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Promise新建后就会立即执行。resolve函数的参数一般都是异步执行成功后的结果，也可能是另一个Promise实例(即是另一个异步操作)，reject函数的参数通常是Error对象的实例。
``` javascript
var promise = new Promise(function(resolve, reject) {
    // 异步处理
    // 处理结束后、 resolve(成功要返回的值) / reject(失败要返回的值)
});
```
# new Promise的快捷方式


``` javascript
Promise.resolve(value);
Promise.reject(error)
```

# thenable

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;thenable指的是一个具有 .then 方法的对象。Promise.resolve 方法另一个作用就是将 thenable 对象转换为promise对象。即使一个对象具有 .then 方法，也不一定就能作为ES6 Promises对象使用，转换是有条件的。

# then 和 catch、resolve和reject

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;promise对象,注册这个promise对象执行成功时和失败时相应的回调函数.这两个函数都接受Promise对象传出的值作为参数。Promise实例new成以后，用then方法分别指定Resolved状态和Reject状态的回调函数

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;resolve函数的参数除了正常的值以外，还可能是另一个Promise实例，表示异步操作的结果有可能是一个值，也有可能是另一个异步操作

``` markdown
	var p1 = new Promise(function (resolve, reject) {
	});
	var p2 = new Promise(function (resolve, reject) {
	  resolve(p1);
	})
```
## then 中指定的方法调用是异步进行的

## 每次调用then都会返回一个新创建的promise对象

## promise chain传参数使用return 


``` markdown
Promise对象名().then(function (value) {
    console.log(value);  
}).catch(function (error) {
    console.log(error);
});
```


# Promise.all 和 Promise.race

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Promise.all 接收一个 promise对象的数组作为参数，当这个数组里的所有promise对象全部变为resolve或reject状态的时候，它才会去调用 .then 方法。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Promise.race 接收一个promise对象数组为参数，只要有一个promise对象进入 FulFilled 或者 Rejected 状态的话，就会继续进行后面的处理。

# Promise.props
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;处理一个 promise 的 map 集合。只要有一个失败，所有的执行都结束。
``` markdown
Promise.props({
 pictures: getPictures(),
 comments: getComments(),
 tweets: getTweets()
}).then(function(result) {
 console.log(result.tweets, result.pictures, result.comments);
});
```
# Promise缺点

1.无法取消Promise，一旦新建它就会立即执行，无法中途取消
2.如果不设置回调函数，Promise内部抛出的错误，不会反应到外部
3.当一个Promise对象处于Pending状态时，无法得知目前进展到哪一个阶段（刚刚开始还是即将完成）


# 原生实现Promise

``` javascript
我们要满足状态只能三种状态：PENDING,FULFILLED,REJECTED三种状态，
且状态只能由PENDING=>FULFILLED,或者PENDING=>REJECTED

var PENDING = 0;
var FULFILLED = 1;
var REJECTED = 2;

value状态为执行成功事件的入参，deferreds保存着状态改变之后的需要处理的函数以及promise子节点，
构造函数里面应该包含这三个属性的初始化

function Promise(callback) {
	this.status = PENDING;
	this.value = null;
	this.defferd = [];
        setTimeout(
          callback.bind(this, this.resolve.bind(this),this.reject.bind(this)),
        0);
}
            
Promise.prototype = {
        constructor: Promise,
        //触发改变promise状态到FULFILLED
        resolve: function (result) {
                    this.status = FULFILLED;
                    this.value = result;
                    this.done();
        },
        //触发改变promise状态到REJECTED
        reject: function (error) {
                    this.status = REJECTED;
                    this.value = error;
        },
        //处理defferd
        handle: function (fn) {
                    if (!fn) {
                        return;
                    }
                    var value = this.value;
                    var t = this.status;
                    var p;
                    if (t == PENDING) {
                         this.defferd.push(fn);
                    } else {
                        if (t == FULFILLED && typeof fn.onfulfiled == 'function') {
                            p = fn.onfulfiled(value);
                        }
                        if (t == REJECTED && typeof fn.onrejected == 'function') {
                            p = fn.onrejected(value);
                        }
                    var promise = fn.promise;
                    if (promise) {
                        if (p && p.constructor == Promise) {
                            p.defferd = promise.defferd;
                        } else {
                            p = this;
                            p.defferd = promise.defferd;
                            this.done();
                        }
                    }
                    }
       },
       //触发promise defferd里面需要执行的函数
       done: function () {
                    var status = this.status;
                    if (status == PENDING) {
                        return;
                    }
                    var defferd = this.defferd;
                    for (var i = 0; i < defferd.length; i++) {
                        this.handle(defferd[i]);
                    }
        },
        //储存then函数里面的事件返回promise对象,defferd函数当前promise对象里面      
        then: function (success, fail) {
                   var o = {
                        onfulfiled: success,
                        onrejected: fail
                    };
                    var status = this.status;
                    o.promise = new this.constructor(function () {
            
                    });
                    if (status == PENDING) {
                        this.defferd.push(o);
                    } else if (status == FULFILLED || status == REJECTED) {
                        this.handle(o);
                    }
                    return o.promise;
        }
};
```
