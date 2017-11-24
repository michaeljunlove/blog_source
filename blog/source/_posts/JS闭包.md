clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/工大图书馆.jpeg
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大图书馆.jpeg
coverCaption: "图书馆"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大图书馆.jpeg
comments: false
title: JS闭包
date: 2015-04-01 18:38:44
tags: [JS]
categories: [大前端技术栈]

---

JS是我比较喜欢的一门语言，它比较自由，有个性，当然也很任性。（主要是这门语言没有被强加一个严格而刻板的语法结构）闭包是JS语言的一个难点，也是它的特色，很多高级应用都要依靠闭包实现。第一次使用闭包是在做一款H5的游戏的时候。
<!-- more -->
***
# 学习网站

* [Mozilla教程](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)
 
* [ruanyf教程]( http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)

* [segmentfault教程]( http://segmentfault.com/a/1190000000652891)

* [Philip Roberts: Help, I’m stuck in an event-loop.](https://vimeo.com/96425312)







# 变量作用域

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E5%8F%98%E9%87%8F%E4%BD%9C%E7%94%A8%E5%9F%9F.png "变量作用域" %}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在介绍闭包之前，先讲一下变量作用域做一下铺垫。JS是一门编译语言，使用的是静态作用域，静态作用域又称词法作用域，由程序定义的位置决定，与代码执行的顺序无关。我们知道在JS变量作用域中一共就存在2种作用域，一种是全局作用域，还有一种是局部作用域，在JS中是 **不存在** 块级作用域的（即花括号封闭起来的那种作用域）。

1.全局作用域

``` javascript
var n=100;
function f1(){
       alert(n);
}
f1(); // 100，函数内部可以直接读取全局变量
```
    

2.局部作用域

``` javascript
function f1(){
//需要注意的是，函数内部声明变量的时候，一定要使用var命令。如果不用的话，你实际上声明了一个全局变量
  var n=100;
}
alert(n); // error，函数外部无法读取函数内的局部变量
```



举个例子吧：

``` javascript
var scope='global';
var f=function(){
       console.log(scope);//undefined
       var scope='f';
}
f();
```
  


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当调用f()函数的时候，没有输出global,而是undefined.这是因为这里存在变量提升，在调用console.log(scope)的时候，console.log先访问f函数体内的作用域，然后在其作用域内搜索到了scope的变量,因为变量提升，所以值为undefined，所以就没有沿着作用域链向上去查找全局的scope变量了，换言之，全局的scope变量就被f（）函数体内的局部的scope变量覆盖了，但是执行到console.log的时候，scope还没有定义，或者说初始化，所以就是undefined了。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;其实，对于我们开发者来说，在访问未定义的变量或者访问定义了，但没有初始化的变量的时候，获得的值都是undefined的。
   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;需要指出的是，上文已经提到了JS的作用域是静态作用域，又叫做词法作用域，是定义的时候决定了的，而不是调用的时候确定的。看到这，也许你还不是很理解，OK，我们再来看个小例子吧。

``` javascript
var scope='top';
var f1=function(){
        console.log(scope);
}    
var f2=function(){
       var scope='f2';
       f1();
}
f2();//top
```

    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在这个例子中，通过f2调用f1，在查找scope定义时，找到的是父作用域中定义的scope变量，而不是在f2中的scope变量。这说明了作用域的嵌套关系不是在调用的时候确定的，而是在定义的时候就已经确定好了。

# 词法环境
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;词法环境是描述静态作用域的一种数据结构。由以下两部分组成：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.环境记录(形参、变量、函数等)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.对外部的词法环境的引用，叫outer。最外层的词法环境，其outer为null

# 从外部读取局部变量

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;请相信你肯定会有如下的需求：在实际的项目过程中，因为这个或者那个原因，你肯定会遇到从外部读取局部变量的这种情况,而且还要求这个局部变量不能因为随着函数一执行完毕就被垃圾回收机制回收。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;如何做到呢？这个就是闭包存在的价值了。闭包是函数式编程中的概念。

# 什么是闭包

严格定义：闭包是由函数（环境）及其封闭的自由变量组成的集合体
* 1.闭包是指有权访问另一个函数作用域中变量的函数。
* 2.闭包是指函数有自由独立的变量。
* 3.闭包允许将函数与其所操作的某些数据（环境）关连起来。

# 闭包的创建

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;创建闭包的常见方式，就是在一个函数内部创建另一个函数。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;例如，我们创建了一个函数`f1`,然后在`f1`的内部创建了另外的一个函数`f2`,这样函数`f2`所在的环境就可以访问所有的外部环境了（包括`f1`所在的环境以及全局环境）。     

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这里主要涉及到JS的作用域链的知识：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;作用域链的用途是保证对执行环境有权访问的所有变量和函数的有序访问。作用域链的前端始终是当前执行的代码所在环境的变量对象，作用域链中的下一个变量对象来自当前环境的外部环境。搜索过程是从作用域链的前端开始，一层一层向后回溯。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;每个环境都可以向上搜索作用域链来查询变量和函数名，但是任何环境都不能通过向下搜索作用域链而进入另外一个执行环境（这就是为什么在局部作用域中，函数外部无法读取函数内的局部变量的原因）
``` javascript   
    function f1(){
       var n=100;
       function f2(){
           n++;
           alert(n); 
       }
       return f2;
    }
    var result=f1();
    result(); // 101
    result(); // 102
    result=null;//n被回收了
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;再看下面这个例子也是关于闭包的：
``` javascript   
var func=function(){
    var a=1;
    return function(){
        a++;
        alert(a);
    }
}
var f=func();
f();//2
f();//3
f();//4
f();//5
```

# 闭包的用途

<p style="color:red;">1.保存变量的现场</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;如实现局部变量的累加，正如上面的例子所示

<p style="color:red;">2.封装</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;模拟私有成员（成员属性或者成员方法）（模块模式：使用闭包来定义公共函数，且其可以访问私有函数和变量。 ）

``` javascript  
    var Counter = (function() {
       var privateCounter = 0;
       function changeBy(val) {
         privateCounter += val;
       }
      return {
          increment: function() {
              changeBy(1);
          },
          decrement: function() {
              changeBy(-1);
          },
          value: function() {
              return privateCounter;
          }
      }   
     })();
    alert(Counter.value()); /* 提示 0 */
    Counter.increment();
    Counter.increment();
    alert(Counter.value()); /* 提示 2 */
    Counter.decrement();
    alert(Counter.value()); /* 提示 1 */
```
# 面试过程中被问到的闭包相关题目
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;下面这个ul，如何点击每一列的时候`alert`其`index`?
``` javascript  
<ul id=”test”>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;如果采用下面这种写法是行不通的，因为`li`节点的`onclick`事件是被异步触发的，当事件被触发的时候，`for`循环早已经结束了，而这时变量`i`的值已经是3，所以在`li`的`onclick`事件函数中顺着作用域链从内到外查找变量`i`时，找到的值总是3
``` javascript  
var lis = document.getElementById("test").children;
for (var i = 0, l = lis.length; i < l; i++) {
    lis[i].onclick=function(){
       alert(i);
    }
}
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;解决方案：在闭包的帮助下，把每次循环的`i`的值都封闭起来，当事件函数中顺着作用域链中从内到外查找变量i时，会先找到被封闭在闭包环境中的`i`

``` javascript  
function $(id) {
    return document.getElementById(id);
}
//方法一
var lis = $("test").children;
for (var i = 0, l = lis.length; i < l; i++) {
    lis[i].setAttribute("index", i);
    lis[i].onclick = function() {
        alert(this.getAttribute("index"));
    }
}
//方法二,
var lis_lis = $("test").getElementsByTagName("li");
for (var i = 0, l = lis_lis.length; i < l; i++) {
    (function(i){
       lis[i].onclick=function(){
          alert(i);
       }
    })(i);
}
```




