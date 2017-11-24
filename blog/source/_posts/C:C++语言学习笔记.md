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
title: C/C++语言学习笔记
date: 2015-03-29 18:38:44
tags: [C/C++]
categories: [计算机基础]

---

C/C++语言是在本科的时候学的，因为研究方向的原因，后来就基本上没怎么写过C语言的代码了，基本上都在搞Web开发，写前端的代码和服务器端的代码。最近想写下C语言的代码，结果发现语法忘得差不多了，于是决定重新学习一下。
<!-- more -->
***

题记：熟练的编程技巧是在知识与经验不断积累的基础上培养出来的。编程是看不会的，也是听不会的，全靠代码一个一个敲出来练会的。写程序的目标是：Keep it simple and stupid。

![](http://7xid80.com1.z0.glb.clouddn.com/C语言.png)


# 终端编写C

1.首先用文本编译器写好如下代码，一个最简单的hello world!保存好，名叫hello.c
``` C
//一条预处理命令，它的作用是通知C语言编译系统在对C程序进行正式编译之前需做一些预处理工作
#include <stdio.h>
//在最新的C标准中，main函数前的类型为int而不是void.一个C程序有且只有一个主函数，即main函数。
//C程序就是执行主函数里的代码，也可以说这个主函数就是C语言中的唯一入口。
int  main(){
	//通常以按一下Tab键为一个缩进；
	printf("hello world\n ");
	//return 0 表示程序正常结束
	return 0;
}   
```

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/C.jpg "C程序结构" %}
   

  
2.然后，进入终端，到刚才编写的文件目录下，执行如下代码，进行编译操作，会产生a.out这个文件，如果不指定编译产生的文件名，所有编译后的文件名都叫a.out这个名字
``` C
   gcc hello.c
```
 

3.编译完成后，可以用ls命令查看刚才的目录，发现多了一个a.out的文件，执行a.out的命令为./a.out,前面的点斜杠是LINUX为了安全的一种手段，保证你当前的目录下和系统重名的文件不会被执行
``` C
   ./a.out
```
    
    
4.最后，就可以看到终端输出结果hello world了

# Xcode编写C++

1.选择Create a new Xcode project

{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/Xcode写C++_STEP1.png "选择Create a new Xcode project" %}
 
   
2.选择Command Line Tool 后点击NEXT
{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/Xcode写C++_STEP2.png "选择Command Line Tool" %}

3.输入工程名，选择语言为C++
{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/Xcode写C++_STEP3.png "输入工程名，选择语言为C++" %}

 

4.如果Create git repository on被选中，就反选它，我们用不到，选择好项目存放的路径
{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/Xcode写C++_STEP4.png
 "选择项目存放的路" %}
 

5.双击main.cpp，就可以编辑了
{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/Xcode写C++_STEP5.png "双击main.cpp进行编辑" %}
 
6.编辑好以后，点击运行
{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/Xcode写C++_STEP6.png "运行" %}
# 解释型语言与编译型语言的区别
{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/解释与编译.png "解释与编译" %}


解释型语言，是在运行的时候将程序翻译成机器语言，所以运行速度相对于编译型语言要慢。如：JAVA

编译型语言在程序执行之前，有一个单独的编译过程，将程序翻译成机器语言，以后执行这个程序的时候，就不用再进行翻译了。如：C

脚本语言是一种解释性的语言，脚本语言一般都有相应的脚本引擎来解释执行，脚本语言不需要编译，可以直接用，由解释器来负责解释。JAVASCRIPT,Python,PHP都是脚本语言


