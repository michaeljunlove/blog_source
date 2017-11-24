clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/工大图书馆.jpg
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大图书馆.jpg
coverCaption: "工大的图书馆"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大图书馆.jpg
comments: false
title: Chrome开发人员调试技巧
date: 2015-08-05 18:38:44
tags: [Chrome]
categories: [工具]

---
前端开发人员必备的调试技巧
<!-- more -->
***

# 官方帮助手册（需要翻墙）


* 1.[编辑样式和DOM](https://developer.chrome.com/devtools/docs/dom-and-styles)

* 2.[javascript 调试](https://developer.chrome.com/devtools/docs/javascript-debugging)

* 3.[移动端调试](https://developer.chrome.com/devtools/docs/device-mode)

* 4.[chrome使用教程](https://github.com/michaeljunlove/JokerChrome)

* 5.[Chrome开发者工具不完全指南](http://web.jobbole.com/82558/)

* 6.[Chrome 控制台console的用法](http://www.tuicool.com/articles/bAvAVjN)

* 7.[Chrome DevTools中文手册](https://www.gitbook.com/book/leeon/devtools/details)

* 8.[JavaScript常见调试方法](http://caibaojian.com/toutiao/5615)

* 9.[150 个 GIF展示如何使用 Chrome DevTools](https://umaar.com/dev-tips/)








# 怎样打开Chrome开发者工具？

### 1.开发者可以在页面上通过`鼠标右键`，选择`审查元素`，来打开Chrome的开发者工具

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom01.png "审查元素" %}

### 2.Windows下的用户可以直接按`F12`来打开
### 3.MAC下的用户可以直接按`⌘-Option-J`或者`⌘-Option-I`来打开

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Anyway，Chrome开发者工具的样子如下图所示，知道它长的什么样就好啦。
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom02.png "Chrome开发者工具" %}


简单介绍一下各个板块的功能， Chrome一共提供了8大组工具：

| 标签页      | 说明          | 
| ------------- |:-------------:| 
| Elements     | 可以看到chrome渲染页面所需要的的HTML、CSS和DOM对象。此外，还可以编辑这些内容更改页面显示效果； | 
| Network      | 可以看到页面向服务器请求了哪些资源、资源的大小以及加载资源花费的时间，当然也能看到哪些资源不能成功加载。此外，还可以查看HTTP的请求头，返回内容等      |  
| Sources | 主要用来调试js    |   
| Timeline | 提供了加载页面时花费时间的完整分析，所有事件，从下载资源到处理Javascript，计算CSS样式等花费的时间都展示在Timeline中   |  
| Profiles | 查看 CPU 执行时间与内存占用等信息    |  
| Resources | 对本地缓存（IndexedDB、Web SQL、Cookie、应用程序缓存、Web Storage）中的数据进行确认及编辑  |  
| Resources | 分析页面加载的过程，进而提供减少页面加载时间、提升响应速度的方案   |  
| Console | 显示各种警告与错误信息，并且提供了shell用来和文档、开发者工具交互   | 
# 开发小技巧

1.WEB前端开发人员，经常会碰到清空浏览器缓存的需求，Chrome 打开 DevTools 之后，右击或者一直摁住刷新键，会出来清缓存强制刷新的功能选项( tip from Addy Osmani ) ，其中「硬性重新加载」类似于强制刷新。

2.在 Chrome 和 Safari 的开发中工具中，可以按「H」键快速隐藏元素。
 
# Console面板

Javascript控制台，在这个面板可以查看错误信息、打印调试信息（console.log()）、写一些测试脚本，还可以当作Javascript API查看用。`shift + enter`可以换行。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom_console01.png "console面板" %}

# Profiles面板

在基于WebKit的浏览器中，我们可以通过在代码中加入下面2行代码来分析当执行到某几行特定的代码时开始性能分析，执行完性能分析后就停止性能分析
1.开始性能分析：`console.profile("begin")`
2.结束性能分析：`console.profileEnd();`

# Timeline面板

Timeline可以显示出每个函数被调用的次数，以及这些函数调用所花费的时间。

# Elements面板

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通过点击搜索按钮，然后再把鼠标移动到你想要查看的内容上，再左键单击就可以找到这部分内容对应的DOM节点了。
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom_Element.gif "查找对应的DOM节点" %}


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;右边的CSS面板可以直接在上面修改
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom_Element_css.png "修改样式" %}
# 假设我们对于不熟悉的项目，就算你给了我源码，我也不知道去哪查看那些调用逻辑，比如：在点击的瞬间，如何查看都调用了哪些函数

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Break on可以对某个元素进行监听，在JS对元素的属性或者HTML进行修改的时候，直接触发断点，跳转到对改元素进行修改的JS代码处
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom_find_function.gif "通过DOM断点找执行函数" %}



# 修改 JavaScript 文件中的代码

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;开发人员可直接对开发者工具的 Source 面板中的代码进行修改，并将其保存，使浏览器在下次执行该段脚本时，直接加载最新修改的版本

# Sources面板下设置条件断点

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SourcesPanel 的左边是内容源，包括页面中的各种资源。其中，又分 Sources 和 Content scripts。Sources 就是页面本身包含的各种资源，它是按照页面中出现的域来组织的，这是我们要关注的。异步加载的 js 文件，在加载后也会出现在这里的。Content scripts 是 Chrome 的一种扩展程序，它是按照扩展的ID来组织的，这类扩展实际也是嵌入在页面中的资源，它们也可以读写DOM。编写、调试这类扩展的开发者才要关心它们，如果你的浏览器没安装任何扩展，那么Content scripts 就看不到任何东西。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Pause/Resume script execution：暂停/恢复脚本执行（程序执行到下一断点停止）。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step over next function call：执行到下一步的函数调用（跳到下一行）。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step into next function call：进入当前函数。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step out of current function：跳出当前执行函数。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Deactive/Active all breakpoints：关闭/开启所有断点（不会取消）。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Pause on exceptions：异常情况自动断点设置。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Chrome 开发者工具提供了断点设置、删除与断点存储等基本功能。同时，开发者工具也提供了设置条件断点的功能，使开发者可以控制该断点只有在满足某一条件时才会被触发。
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom_Sources.png "Sources面板" %}

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom_breakpoint.png "断点面板" %}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;使用Ctrl + G 可以跳转到文件或者是文件中的第几行。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom_breakpoint.gif "设置条件断点" %}



# 移动端开发调试
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom_mobil.png "移动端开发调试" %}



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在控制台中可以直接模拟手机、调整UA、修改网络连接状态.还可以调用chrom的模拟重力传感器。
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/chrom_mobil02.png "移动端开发调试" %}



