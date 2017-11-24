clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/工大全景.jpg
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大全景.jpg
coverCaption: "俯瞰工大"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大全景.jpg
comments: false
title: JS继承
date: 2015-07-08 18:38:44
tags: [JS]
categories: [大前端技术栈]

---
**前言**：虽然本篇主要是讲JS继承的，但是讲继承，也逃不开函数，对象，原型等这些基本概念,所以基本上都会涉猎到了。The part that is good is not original, and the part that is original is not good.----十八世纪英国文学家约翰逊博士
<!-- more -->
***

<img src="http://7xid80.com1.z0.glb.clouddn.com/JS_OOP.png" width="600px"  height="200px" alt="面向对象编程" align=center/>

* 继承：许多的OO语言都支持2种继承方式：接口继承与实现继承。继承是实现多态性最常用的手段。JavaScript 没有提供传统的面向对象语言中的类式继承，而是通过原型委托的方式来实现对象与对象之间的继承。基于原型链的委托机制是原型继承的本质。原型编程中的一个重要特性是当对象无法响应某个请求的时候，会把该请求委托给它的原型。

* 封装：目的是为了将信息隐藏，隐藏数据，隐藏实现的细节，设计细节等。许多的语言通过private,public,protected来实现提供不同的访问权限。JS由于没有提供关键字的支持，我们只能通函数来实现创建作用域。

* 多态：背后的思想是将“做什么”和“谁去做以及怎样去做”分离开来，也就是把不变的部分隔离开来，把可变的部分封装起来。这样同一个操作作用于不同的对象上面的时候，可以产生不同的解释和不同的执行结果。将行为分布在各个对象中，让各个对象各自负责自己的行为，这是面向对象设计的优点。



# 原型对象，构造函数，实例对象

![](http://7xid80.com1.z0.glb.clouddn.com/JS学习路线.png)

## JavaScript原型编程的基本规则
* 所有的数据都是对象
* 要得到一个对象，不是通过实例化类，而是找到一个对象作为原型并克隆它
* 对象会记住它的原型是哪个
* 如果对象无法响应某个请求，它会把这个请求委托给它自己的原型

## 创建对象的几种方式的比较
* 工厂模式创建对象的问题在于没有解决对象识别问题，即怎样知道一个对象的类型。
* 构造函数模式创建对象虽然解决了虽然解决了对象识别问题，但是其问题在于每个方法都要在每个实例上重新创建一遍。即不同实例上的同名函数是不相等的。
* 原型模式创建对象的好处是所有对象实例共享原型对象的属性和方法。有2个缺点：一是省略了为构造函数传递初始化参数这一环节，结果所有实例在默认情况下都将取得相同的属性值。二是原型中的所有属性是被很多实例共享的，对于属性是函数，属性是基本值，都没啥大影响，但是对于引用类型，在引用类型上的所有操作将在所有实例都共享。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;要想把`JS继承`讲清楚，就要先把`原型对象`，`构造函数`，`实例对象`这三者之间的关系先理清楚，这个很重要，只有先理清楚了他们三者之间的关系，才可以把JS的继承理解好。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JS的继承是主要靠`原型链`实现的，`原型链`是什么东西呢？

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在讲解`原型链`之前，让我们先把上面提到的`原型对象`，`构造函数`，`实例对象`这三个名词先理清楚，因为要理清楚`原型链`这个概念，离不开这3个名词。

让我们通过一个简单的例子来理解一下吧

``` javascript
    function Person(){}
    var Person1=new Person();
    var Person2=new Person();
    //也可以这样玩，Person1.constructor===Person
    var Person3=new Person1.constructor();
```
  
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;上面的代码创建了1个Person函数（这个Person函数就是构造函数），然后new了2个Person对象（这2个Person对象就是实例对象）。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在JS中，无论什么时候，只要你创建了一个函数，那么这个函数就有一个`prototype`属性，`prototype`的中文意思是`原型`，这个`prototype`属性是一个指针，指向函数的`原型对象`的。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`原型对象`的作用是主要用来包含可以由特定类型的所有实例共享的属性和方法。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当我们用关键字`new`来创建一个实例对象时，实例对象中的所包含的属性和方法都来自`原型对象`。

什么是`原型对象`呢？

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;我个人的理解是可以把这个`原型对象`看成这个函数的`"基因"`。一旦我们对这个基因做了一些修改，那么这些修改会马上体现到所有的`实例对象`上。`原型对象`存在的价值是可以让所有的`实例对象`可以共享原型对象所包含的属性和方法。（对于这句话，如果现在没有理解，没关系，继续往下看，就会明白了的）。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;所有的原型对象都会有一个`constructor`属性是指向该`原型对象`所对应的构造函数的，`原型对象`的其他方法都是从`object`对象继承过来的。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当我们调用构造函数，使用new操作符创建了一个实例对象以后，这个`实例对象`的内部将包含一个指针，这个指针叫做[[Prototype]]（我看有的书上也叫`_proto_`）指向构造函数的`原型对象`。
上述描述的原理如下图所示：

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/JS原型.png "JS中的原型对象，构造函数，实例对象" %}
 
 从上面这幅图中，我们可以看到：
 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;每个构造函数都有一个原型对象，原型对象又包含一个指向构造函数的指针`constructor`，然后呢，每个通过构造函数new出来的实例呀，都包含一个指向原型对象的指针`[[Prototype]]`。这样，构造函数，原型对象，实例，这三者之间就构成了一条最简单的原型链了。


{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/原型链1.png "原型链" %}
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OK，看到这里，应该都明白了原型对象，构造函数，实例对象，原型链这些基本概念了吧。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;实例对象可以访问保存在原型对象中的值，但却不能通过实例对象去重写原型对象中的值。值得注意的是比如用对象字面量来重写原型对象将会切断现有原型与之前已经创建好的实例对象之间的联系。


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;下面正式进入我们的主题：继承。


# 继承实现方案1--原型链

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;如果我们让子类的原型对象指向父类的实例，那么这条原型链就延长了。如下图所示：

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/原型链2.png "JS原型继承中的原型链" %}


代码实现如下：
``` javascript
    //定义父类
    function SuperClass(){
       this.name="父类";
       this.color=["red","blue","green"];
       this.sayColor=function(){
           alert(this.color);
       }
    }
    //定义子类
    function SubClass(){
       this.name="子类" ;  
    }
    //子类继承自父类
    SubClass.prototype=new SuperClass();
    //由于SubClass继承了SuperClass的所有内容，constructor值也被复制了,我们需要重置constructor值，使其指向新的子类，如果没有这一步，则通过SubClass创建的对象就会报告说他们是通过SuperClass类创建过来的。
    SubClass.prototype.constructor=SubClass;
    //创建一个子类的实例A
    var subclassA=new SubClass();
    //创建一个子类的实例B
    var subclassB=new SubClass();
    //输出color属性
    subclassA.sayColor();//red blue green
    subclassB.sayColor();//red blue green
    //加入一个black颜色到color数组
    subclassA.color.push("black");
    //输出color属性
    subclassA.sayColor();//red blue green black
    subclassB.sayColor();//red blue green black
```
    
原型链的弊端:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.不支持多重继承（算是一个特点吧，也不能说是弊端）
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.如果父类的属性中有引用类型时（如本例中的color属性），子类的所有实例都会共享这个属性。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.在创建子类型的实例的时候，不能向父类的构造函数传递参数

# 继承实现方案2--借用构造函数

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在讲解借用构造函数之前，先讲一下`object masquerading`，翻译成中文就是对象冒充，因为也和这个比较相关嘛，所以就一起讲一下啦。
``` javascript
     //定义父类
    function ClassA(color){
      this.color=color;
      this.sayColor=function(){
          alert(this.color);
      }
    }
    //定义子类
    function ClassB(color,Name){
      //the name of a function is just a pointer to it
      this.newMethod = ClassA;
      //调用newMethod方法
      this.newMethod(color);
      //deletes the reference to ClassA so that it cannot be called later on.
      delete this.newMethod;
      //定义子类特有的方法和属性，所有新属性和新方法都必须在删除了新方法的代码行后定义
      this.name = Name;
      this.sayName = function () {
          alert(this.name);
      };
    }
    //创建一个实例
    var instance=new ClassB("red","michael");
    instance.sayColor();//red
    instance.sayName();//michael
```


    
对象冒充的特点：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.可以实现多重继承。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;对象冒充在开发者开始理解了函数的工作方式，尤其是如何在函数环境中使用 this 关键字后才发展出来。随后，由于这种继承方法的流行，ECMAScript 的第三版为 Function 对象加入了两个方法，即 call() 和 apply()。全局函数apply和call可以用来改变函数中this的指向。

``` javascript
    function Parent(age){
        this.name = ['mike','jack','smith'];
        this.age = age;
    }
    function Child(age){
        Parent.call(this,age);
    }
    var test1 = new Child(21);
    var test2 = new Child(22);
    alert(test1.age+"  "+test2.age);//21 22
    alert(test1.name+"  "+test2.name);//mike,jack,smith    mike,jack,smith
    test1.name.push('bill');
    alert(test1.name+"  "+test2.name);//mike,jack,smith,bill mike,jack,smith
```
  
    

借用构造函数的弊端：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.方法都在构造函数中定义，函数复用无从谈起，父类的原型中定义的方法对子类是不可见的。

# 继承实现方案3--组合继承

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;组合继承把原型链和借用构造函数技术组合到一块，其思想是：使用原型链实现对原型属性和方法的继承，通过借用构造函数来实现实例属性的继承。这样，既通过在原型上定义方法实现了函数复用，又保证每个实例都有它自己的属性。


``` javascript
    function Parent(age){
        this.name = ['mike','jack','smith'];
        this.age = age;
    }
    Parent.prototype.run = function () {
        return this.name  + ' are both' + this.age;
    };
    function Child(age){
        //继承属性
        Parent.call(this,age);//对象冒充，给超类型传参
    }
    //原型链继承，用来继承方法
    Child.prototype = new Parent();
    Child.prototype.constructor=Parent;
    var test = new Child(21);//写new Parent(21)也行
    alert(test.run());//mike,jack,smith are both21
```
    
   
  


