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
title: JAVA面试题
date: 2015-03-23 18:38:44
tags: [JAVA]
categories: [计算机基础]

---
JAVA面试题
<!-- more -->
***
# 访问权限
| 权限        | 同一类         | 同一包  |不同包的子类  |所有类  |
| ------------- |:-------------:| -----:| -----:|-----:|
| public     | 允许| 允许 |允许  |允许  |
| protected    | 允许      |   允许|允许  |不允许 |
| 默认（缺省） | 允许      |   允许 |不允许  |不允许  |
| private | 允许      |  不允许 |不允许  |不允许  |

# 继承
``` java
1.继承原则：子类只继承父类中非private的成员变量
2.隐藏原则：子类的成员变量和父类的成员变量同名时，父类的成员变量被覆盖
3.super表示对某个类的父类的引用
4.构造方法不存在继承关系
```
# 构造方法
``` java
1.如果子类没有构造方法，则它调用父类吴参数构造方法.
2.如果子类有构造方法，则在创建子类的对象时，先执行父类的构造方法，再执行自己的构造方法
3.对于父类中包含有参数的构造方法，子类可以通过在自己构造方法中使用super关键字来引用，而且必须是子类构造方法中的
```
# static
``` java
1.static 用来修饰类的变量，它在所有实例之间是共享的，在加载该类时，只分配一次空间，并初始化。
2.static 修饰的类方法称为静态方法，可以直接被调用，不需要产生实例
3.静态方法不能访问所属类的非静态变量和方法
4.父类的静态方法不能被子类覆盖为非静态方法
```
# final
``` java
1.final修饰的类，称为最终类，不能被继承
2.final修饰的方法，不能被其所在类的子类覆盖
3.final修饰方法的参数，表示该方法不期望被传进来的参数有任何改变
4.final修饰基本变量，即表示常量，值无法改变
```

# switch
``` java
1.使用switch语句时，要注意表达式必须是符合byte、char、short、int类型的表达式，而不能使用浮点类型或者long类型，也不能是字符串类型
2.switch语句将表达式的值和每个case语句中的常量值进行比较，如果匹配成功，则执行该case子句中的常量值后的语句，知道遇到break语句为止
3.case子句中常量的类型必须与表达式的类型相同，而且每个case子句中常量的值必须不同
4.default子句是可选的，当表达式的值与任一case子句中的值都不匹配的时候就执行default后的语句
```
# 面向对象编程的三大特性是什么，请简要阐述

``` java
1.封装
-增加内部实现部分的可替换性
-减少类之间的耦合关系，方便模块划分
-保证类内部数据之间的一致性，提高软件的可靠性
2.继承
3.多态
-静态多态性（方法重载）：同一类中允许多个同名方法，参数的个数、类型、顺序不同
-动态多态性（方法覆盖）：方法名、返回值、参数形态完全一样
```
# java内存模型

``` java

```
# String、StringBuffer与StringBuilder之间区别

``` java
1.String是字符串常量，StringBuffer和StringBuilder是字符串变量

2.三者在执行速度方面的比较：StringBuilder >  StringBuffer  >  String

3.StringBuilder是线程非安全的，StringBuffer和String是线程安全的

4.使用
如果要操作少量的数据用 =String
单线程操作字符串缓冲区 下操作大量数据 = StringBuilder
多线程操作字符串缓冲区 下操作大量数据 = StringBuffer
```

# ==和equals()区别是什么

``` java
1.对于字符串变量来说，==运算符比较两个变量本身的值，equals方法比较的是两个字符串中所包含的内容是否相等。对于对象来说，两个对象之间用==比较时，是比较其名称是否参考至同一个对象，而不是比较其内容。
2.对于非字符串类型的变量来说，“==”云运算符和“equals()”方法都用来比较其所指对象在堆内存中的首地址
```
# 接口和抽象类的区别是什么

``` java
1.接口可以多重继承，抽象类不可以
2.抽象类内部可以有实现的方法，接口则没有实现的方法
3.接口与实现它的类不构成类的继承体系，即接口不是类体系的一部分。因此，不相关的类也可以实现相同的接口。
而抽象类是属于一个类的继承体系，并且一般位于类体系的顶层。
4.接口的优势：通过实现多个接口实现多重继承，能够抽象出不相关类之间的相似性。
5.创建类体系的基类时，若不定义任何变量并无需给出给出任何方法的完整定义，则定义为接口；
必须使用方法定义或变量时，则考虑用抽象类。
```
# 如何确保N个线程可以访问N个资源同时又不导致死锁？

``` java
指定获取锁的顺序，并强制线程按照指定的顺序获取锁。
因此，如果所有的线程都是以同样的顺序加锁和释放锁，就不会出现死锁了。
```
# JDK和JRE的区别是什么？
``` java
Java运行时环境(JRE)是将要执行Java程序的Java虚拟机。它同时也包含了执行applet需要的浏览器插件。
Java开发工具包(JDK)是完整的Java软件开发包，包含了JRE，编译器和其他的工具(比如：JavaDoc，Java调试器)，可以让开发者开发、编译、执行Java应用程序。
```
# 进程与线程的区别
``` java
单个CPU一次只能运行一个任务
进程是系统进行资源分配和调度的一个独立单位。
线程是进程的一个实体，是CPU调度和分派的基本单位。
1.一个进程可以包括多个线程
2.一个进程的内存空间是共享的，每个线程都可以使用这些共享内存
3.一个线程使用某些共享内存时，其他线程必须等它结束，才能使用这一块内存
4.调度：线程作为调度和分配的基本单位，进程作为拥有资源的基本单位。
5.并发性：不仅进程之间可以并发执行，同一个进程的多个线程之间也可以并发执行。
6.拥有资源：进程是拥有资源的一个独立单位，线程不拥有系统资源，但可以访问隶属于进程的资源。
7.系统开销：在创建或撤销进程的时候，由于系统都要为之分配和回收资源，导致系统的明显大于创建或撤销线程时的开销。同样，多进程的程序要比多线程的程序在进程切换时，耗费的资源较大，效率要差些。

```
# sleep和wait有什么区别
``` java
1.sleep()方法，属于Thread类中的.wait()方法，是属于Object类中的。
2.sleep必须捕获异常，而wait，notify和notifyAll不需要捕获异常 
3.sleep方法没有释放锁，而 wait 方法释放了锁，使得其他线程可以使用同步控制块或者方法。
4.wait，notify和notifyAll只能在同步控制方法或者同步控制块里面使用，而sleep可以在任何地方使用（使用范围）
```
# synchronized

``` java
Java语言中,每一个对象有一把锁,线程可以使用synchronized关键字来获取对象上的锁。
当synchronized用来修饰一个方法或者一个代码块的时候，能够保证在同一时刻最多只有一个线程执行该段代码。
synchronized是Java中的关键字，是一种同步锁。它修饰的对象有以下几种： 
1. 修饰一个代码块，被修饰的代码块称为同步语句块，
其作用的范围是大括号{}括起来的代码，作用的对象是调用这个代码块的对象； 
2. 修饰一个方法，被修饰的方法称为同步方法，
其作用的范围是整个方法，作用的对象是调用这个方法的对象； 
3. 修改一个静态的方法，其作用的范围是整个静态方法，作用的对象是这个类的所有对象； 
4. 修改一个类，其作用的范围是synchronized后面括号括起来的部分，作用主的对象是这个类的所有对象。
```
# 多线程实现方式

``` java
1.继承Thread类，重写该类的run()方法。

public class MyThread extends Thread {  
　　public void run() {  
　　	System.out.println("MyThread.run()");  
　　}  
}
//创建一个新的线程  myThread1  此线程进入新建状态
MyThread myThread1 = new MyThread();  
//创建一个新的线程  myThread2  此线程进入新建状态
MyThread myThread2 = new MyThread(); 
//调用start()方法使得线程进入就绪状态
myThread1.start();  
//调用start()方法使得线程进入就绪状态
myThread2.start(); 

2.实现Runnable接口，并重写该接口的run()方法

class MyThread implements Runnable {
    public void run() {
    	System.out.println("MyThread.run()");  
    }
}
//创建一个MyThread实现类的对象
MyThread myThread = new MyThread(); 
//将myThread作为Thread target创建新的线程 
Thread thread = new Thread(myThread); 
//调用start()方法使得线程进入就绪状态 
thread.start();  

3.使用Callable和Future接口创建线程.有返回值
```

# HashMap和HashTable的区别，及其实现原理

``` java
test
```
