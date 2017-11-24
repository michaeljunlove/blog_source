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
title: Maven项目管理构建工具
date: 2015-03-26 18:38:44
tags: [Maven]
categories: [工具]

---
搞JAVA，那么就不可避免地要用到Maven，就好像玩Node,就少不了npm
<!-- more -->
***
# 相关网站

 * [Maven官网](http://maven.apache.org/)
 
# 什么是Maven

>Maven是基于项目对象模型（POM），可以通过一小段描述信息来管理项目的构建、报告和文档的软件项目管理工具。


# 安装Maven

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.首先去Maven的官网下载Maven
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/Maven.png "Maven" %}

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.解压后如下图所示
>`bin`目录包含了`mvn`的运行脚本
`boot`目录包含了一个类加载器的框架
`conf`目录是配置文件目录
`lib`目录下包含了`Maven`运行时所用到的所有的类库，包括一些第三方类库

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/maven1.png "解压后" %}

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.配置Maven环境变量
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.1、计算机-右键-属性-高级系统设置-环境变量
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.2、新建`M2_HOME`环境变量，值为Maven的安装目录
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.3、编辑`Path`环境变量，在尾部加入`；%M2_HOME%\bin`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.4、验证是否配置成功。在终端处输入`mvn -v`出现如下图所示即表示配置成功了。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/maven2.png "Maven环境变量配置成功" %}

# POM.XML

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;POM.XML相当于package.json文件，指明包含的依赖。


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;modelVersion： 这个XML文件所使用的POM格式的版本
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;groupId： 相当于这个project的所有者或者机构的一个标识，一般是com.company.xxx这种格式
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;artifactId：  这个project最后所生成的文档(jar、war)的名字，比如对于junit这个开源的project，它的artifactId就是junit
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;packaging： 这个project的打包的类型，一般是war、jar等值
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;version： project的版本
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name： project的名字，生成文档等内容的时候会用的这个名字

# 常用Maven命令

|命令      | 描述         | 
| ------------- |:-------------:| 
| mvn -v     | 查看maven版本 |
| mvn compile   | 编译     |  
| mvn test | 测试    | 
| mvn package | 打包   | 
| mvn clean | 删除target目录  | 
| mvn archetype:generate | 按照提示进行选择创建目录 | 


# 自动创建目录

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;自动创建目录除了使用`mvn archetype:generate`按照提示创建目录也可以按如下命令一次性自动创建目录

``` java
mvn archetype:generate -DgroupId=项目名 
                       -DartifactId=项目名-模块名 
                       -Dversion=版本号 
                       -Dpackage=代码所在的包名称
```

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/maven%E7%9B%AE%E5%BD%95%E7%BB%93%E6%9E%84.gif "Maven标准目录结构" %}
