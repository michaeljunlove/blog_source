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
title: AngularJS学习笔记
date: 2016-05-14 18:38:44
tags: [AngularJS]
categories: [大前端技术栈]

---
AngularJS是一个JS框架，通过ng-directives扩展了HTML，通过expression绑定数据到HTML，它使得开发SPA更加容易。马上要去阿里实习了，主管让我准备一下AngluarJS相关的知识，AngularJS之前研一的时候自学过，只停留在了解其设计思想的程度，没有在实际的项目中使用过，实验室也不推崇使用新技术。
<!-- more -->
***
# 学习网站

 * [angularjs官方网站](https://angularjs.org/)
 
 * [angularjs的Github]( https://github.com/angular/angular.js)
 
 * [angularjs的入门教程](https://docs.angularjs.org/guide/index)
 
 * [ng-book]( https://www.ng-book.com/)
 
 * [如何衡量一个人的 AngularJS 水平？]( https://www.zhihu.com/question/36040694)
 
 * [徐飞的博客](https://github.com/xufei/blog/issues)
 
 * [优化Angular应用的性能](https://github.com/xufei/blog/issues/23)
 
 * [angularjs的入门教程：Use AngularJS to Power Your Web Application]( http://www.yearofmoo.com/2012/08/use-angularjs-to-power-your-web-application.html?url_type=39&object_type=webpage&pos=1)
 
 * [ui-router]( https://github.com/angular-ui/ui-router)
 
 * [$translate文档](  https://angular-translate.github.io/docs/#/api/pascalprecht.translate.$translate)
 


 
 * ['this' vs $scope in AngularJS controllers]( http://stackoverflow.com/questions/11605917/this-vs-scope-in-angularjs-controllers)
 
 
 * [AngularJS: "Controller as" or "$scope"?](http://codetunnel.io/angularjs-controller-as-or-scope/)
 

 * [ui-router.stateHelper]( https://github.com/marklagendijk/ui-router.stateHelper)
 
 
 * [what-is-the-difference-between-ng-if-and-ng-show-ng-hide]( http://stackoverflow.com/questions/19177732/what-is-the-difference-between-ng-if-and-ng-show-ng-hide)

 * [Difference between the 'controller', 'link' and 'compile' functions when defining a directive](http://stackoverflow.com/questions/12546945/difference-between-the-controller-link-and-compile-functions-when-definin)
 
 * [NG2](https://github.com/gf-rd/awesome-ng2)

 * [Set element focus in angular way](http://stackoverflow.com/questions/25596399/set-element-focus-in-angular-way)
 
 
 
 
 

 
 



# 一切从模块开始

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/Angular%E6%A8%A1%E5%9D%97.png "一切从模块开始" %}

# AngularJS的特性

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.MVC
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.模块化，Module定义了 AngularJS 应用。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.双向数据绑定
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.指令系统

# 模块(M层)


``` javascript
var app=angular.module('模块名',[]);
```
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/Angular2.png "创建模块" %}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ng-app 指令定义一个 AngularJS 应用程序，该指令在SPA中只能出现一次，值为模块名。当页面加载完成时候，会执行该模块。


# 指令&表达式(V层)

## 指令
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;指令是扩展的 HTML 属性，带有前缀 ng-。只要是和DOM操作有关的都调用指令。
## 创建指令
``` javascript
app.directive('指令名', function() {
           return {  
             //配置信息                                                             
           };
});
```

## 指令配置信息
| 属性        | 描述          | 
| ------------- |:-------------:| 
| scope     | 创建独立作用域|   
| require     | 所依赖的其他指令| 
| restrict     | 指令的使用范围AEMC | 
| template     | 指令使用的模版      |   
| compile     | 编译阶段执行compile函数,compile函数一共有3个参数，分别是：element,attr,tranaclude|  
| controller     | 用来给指令暴露出public的方法供外部调用|    
| link     | 链接阶段每条指令的link函数被调用，在link中操作DOM，绑定事件监听，link主要用来处理指令内部的事务，link函数一共有4个参数，分别是：scope,element,attr,父控制器| 
| transclude | 用来显示指令的子内容，必须在template 中加入<div ng-transclude></div>表示用来存放指令嵌套的内容    |   
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E6%8C%87%E4%BB%A4%E7%9A%84restrict.png "restrict" %}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.推荐使用元素和属性的方式使用指令
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.当需要创建带有自己的模板指令的时候，使用元素名称的方式创建指令
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.当需要为已有的HTML标签增加功能的时候，使用属性的方式创建指令 
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E6%8C%87%E4%BB%A4%E7%9A%84scope%E7%BB%91%E5%AE%9A%E7%AD%96%E7%95%A5.png "scope的绑定策略" %}

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E5%86%85%E7%BD%AE%E6%8C%87%E4%BB%A4.png "内置指令" %}


## 指令的生命周期


{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E6%8C%87%E4%BB%A4%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.png "指令的生命周期" %}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;compile函数用来对模板自身进行转换，link函数负责在模型与视图之间进行动态关联。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;作用域在链接阶段才会被绑定到编译之后的link函数上
## 指令与控制器交互
``` javascript
element.bind("事件名",function(){
//方案1：scope.loadData();
//方案2：scope.$apply("loadData()");
//方案3：scope.$apply(attrs.howtoload)//howtoload这个属性必须小写，也不用加()
});
```
## 指令与指令交互
``` javascript

```
## 表达式
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;表达式写在双大括号内。使用表达式来在其书写的位置"输出"数据。双括号，两个冒号 home.text,双括号，使用两个冒号进行一次绑定


# 控制器(C层)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Controllers are where we define our app’s behavior by defining functions and values.
``` javascript
app.controller('控制器名称',function{
  //do something;
});
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;关联控制器
``` javascript
<div ng-controller="控制器名称 as 别名">
    //该控制器的作用域
</div>
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.不要试图去复用controller
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.不要在controller中操作DOM
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.不要在controller中做数据格式化
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.不要在controller中做数据过滤

# 双向数据绑定

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ng-model 指令可以将输入域的值与 AngularJS 创建的变量绑定。 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;数据模型挂在$rootScope下面。

# 路由
``` javascript
require('angular-ui-router');
```

# 服务

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.Service都是单例的
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.Service由$injector负责实例化
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.Service在整个生命周期中都存在的，可以用来共享数据
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.在需要使用的地方，利用依赖注入机制注入Service
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.自定义的Service需写在内置的Service后面
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6.命名规范：内置的Service都是以$开头，自定义Service应该避免

## 创建服务的5种方法

1.factory

``` javascript
angular.moudle('myapp').factory('serviceName',function(){
    return {//暴露一些接口}
})
```

2.service

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;service函数会在创建实例时通过new关键字来实例化服务对象

``` javascript
angular.service('serviceName',构造函数);
```

3.provider

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;所有的服务工厂都是由$provider()服务创建的额，$provider负责在运行时初始化这些提供者，提供者是一个具有$get()方法的对象，$injector通过调用$get方法创建服务实例。如果希望在config()函数中，可以对服务进行配置，必须使用provider()来定义服务。

``` javascript
angular.moudle('myapp').provider('serviceName',{
    $get:function(){
      return  {//暴露一些接口}
    }
});
```

4.constant

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;constant可以将一个已经存在的变量值注册为服务，并将其注入到应用的其他部分当中。
``` javascript
angular.moudle('myapp').constant('apiKey','122131123');
//使用
angular.moudle('myapp').controller('controllerName',function($scope,apiKey){
    $scope.apiKey= apiKey;
})
```

5.value

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;如果服务的$get方法返回的是一个常量，那就没必要定义一个包含复杂功能的完整服务，可以通过value()函数方便的注册服务。value与constant的最主要区别是：常量可以注入到配置函数中，而值不可以。通常情况下，用constant来配置数据，用value来注册服务对象或函数。

``` javascript
angular.moudle('myapp').value('apiKey','122131123');
//使用
angular.moudle('myapp').controller('controllerName',function($scope,apiKey){
    $scope.apiKey= apiKey;
})
```
# Angular启动方式

1.通过ng-app
2.通过angular.bootstrap手动启动
``` javascript
angular.element(document).ready(function(){
   angular.bootstrap(document,['模块名']);
});
```
3.不要在一个页面上用多个ng-app.多个ng-app方式启动，条件是ng-app不能嵌套。可通过angular.bootstrap手动启动。


# $on、$emit和$broadcast

1.$emit只能向parent controller传递event与data,只有$emit发出的事件是可以被中止的，$broadcast发出的不可以。

``` javascript
$scope.$on("someEvent", function(e) {
    e.stopPropagation();
});
```
2.$broadcast只能向child controller传递event与data
3.$on用于接收event与data