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
title: JS设计模式之单例模式
date: 2016-03-19 18:38:44
tags: [JS]
categories: [设计模式]

---
一直就想好好整理JS设计模式这块的东西了，JS设计模式这块我感觉应该是JS基础里面的最高峰了，今晚先来个最简单的单例模式吧
<!-- more -->
***
# 学习网站

 * [看极客学院视频的网站](http://www.sunnyos.com/video/jike.html)
 
 * [极客学院单例模式视频](http://www.jikexueyuan.com/course/673.html)

# 设计模式

>设计模式是一套被反复使用、多数人知晓的、进过分类编目的、代码设计经验总结。目的是为了可重用代码、让代码更容易被他人理解、保证代码的可靠性。

# 单例模式

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;单例模式和核心是：保证一个类仅有一个实例，并提供一个访问它的全局访问点。

# 应用场景

>一般用在配置文件、工具类、线程池、日志对象、全局缓存、浏览器中的window对象、登入浮窗等这些只需要创建一次就够了，可以反复使用的场景。

# 创建单例模式

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;创建单例模式，很简单，用一个变量来标志当前是否已经为某个类创建过对象，如果是，则在下一次获取该对象的实例时，直接返回之前创建好的对象。需要注意的是JS这门语言，创建一个全局变量即是一个单例了，但我们应当尽量减少全局变量的使用，因为全局变量很容易造成命名空间的污染，如果需要，也要把它的污染降到最低，免得在多人协作开发过程中被人覆盖了。

# 惰性单例

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;惰性单例指的是在需要用到的时候才创建对象单例。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;为了实现复用，需要将`创建单例对象`这一行为和`管理单例对象`这一行为分开，实现单一职责原则。
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E5%8D%95%E4%BE%8B%E6%A8%A1%E5%BC%8F.png "单例模式" %}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;以下代码`getSingleton`函数专门用来`管理单例对象`这一行为的，通过传入`创建单例对象`的函数`fn`来实现，`getSingleton`函数返回一个新函数，并且用`result`这个闭包来保存`fn`的计算结果。

``` javascript
 var getSingleton=function(fn){
     var result;
     return function(){
         return result||(result=fn.apply(this,arguments));
     }
 }
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;假设我们需要创建一个DIV的单例对象
``` javascript
  function createDiv(){
     var div=document.createElement('div');
     document.body.appendChild(div);
     return div;
  }
  //生成一个Div实例
  var creatSingleDiv=getSingleton(createDiv);
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;假设我们需要创建一个iframe的单例对象
``` javascript
  function createIframe(){
     var iframe=document.createElement('iframe');
     document.body.appendChild(iframe);
     return iframe;
  }
  //生成一个iframe实例
  var creatSingleIframe=getSingleton(createIframe);
```

