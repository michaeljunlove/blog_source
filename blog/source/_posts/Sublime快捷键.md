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
title: Sublime快捷键
date: 2015-05-07 18:38:44
tags: [Sublime]
categories: [工具]

---
Sublime这款编辑器在MAC下的快捷键
<!-- more -->
***
# 学习网站

 * [sublimetext官网](http://www.sublimetext.com/)
 * [sublimetext插件](https://packagecontrol.io/)
 * [sublimetext教学视频](http://code.tutsplus.com/courses/perfect-workflow-in-sublime-text-2)
 * [sublimetext慕课网教程](http://www.imooc.com/learn/333)
 * [sublimetext包管理]( https://packagecontrol.io/)
 
# 安装包
Sublime安装包挺恶心的，因为墙的原因，无法获取到下面这个文件会一直报如下图所示的错误。
``` markdown
https://packagecontrol.io/channel_v3.json.
```
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/sublime.png "sublime报错" %}
## 解决方案如下
我们可以自己先翻墙把这个文件下载下来，然后再本地启动一个服务器。最后，修改配置文件。
## 如何安装包
 
``` markdown
//1.shift+command+p
//2.输入install
//3.输入包名称
```
# 各种常用的包
| 包名称       | 作用         | 
| ------------- |:-------------:| 
| SyncedSideBar | 搜索到对应的文件时，左边的树会自动定位到该文件 | 
   

# 使用命令行启动

``` markdown
vi .zshrc
//加入
alias subl="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"
//使用
subl .
```



# 搜索
| 描述        | 使用说明         | 
| ------------- |:-------------:| 
| 搜索当前工程下文件中包含的字符串    | shift+command+f| 
| 搜索当前文件中包含的字符串    | command+f| 
| 搜索当前文件中的函数名  | command+r| 

# 打开/前往

| 描述        | 使用说明         | 
| ------------- |:-------------:| 
| 打开一个文件夹     | commmand+o | 
| 打开一个新的页面    | commmand+n | 
| 打开一个新的窗口    | commmand+shift+n | 
| 前往文件    | commmand+t/commmand+p| 
| 前往当前文件的行号   | control+g | 
| 打开命令面板  | shift+command+p | 
| toggle左侧目录树  | command+k+b | 
| 在页面之间跳转 | control+tab| 
| 在浏览器中打开 | control+shift+enter| 


# 编辑

| 描述        | 使用说明         | 
| ------------- |:-------------:| 
| 多点编辑    | 按commmand键标记多点编辑处 | 
| 多行合并  | commmand+j | 
| 缩减一个级别  | commmand+} | 
| 退回缩减一个级别  | commmand+{ | 
| 选择当前行  | commmand+l | 
| 在当前行的下面开辟一个新行  | commmand+回车 | 
| 在当前行的上面开辟一个新行  | commmand+shift+回车 | 
| 块选择 | 按住option键，拖动鼠标要选择的块 | 
| 跳出多点编辑模式 | esc | 
| 回到行首 | commmand+左箭头 | 
| 回到行尾 | commmand+右箭头 | 
| 放大字体  | command+加号| 
| 缩小字体  | command+减号| 
| 规范缩进  | shift+tab| 