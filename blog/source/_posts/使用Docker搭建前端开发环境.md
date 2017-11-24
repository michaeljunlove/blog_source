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
title: 使用Docker搭建前端开发环境
date: 2017-06-04 18:38:44
tags: [Docker]
categories: [工具]

---
Docker
<!-- more -->
***
# 学习网站


 * [Docker国外官网](https://www.docker.com/)
 * [Docker中文网](http://www.docker.org.cn/index.html)
 * [Docker Hub]( https://hub.docker.com/)
 * [网易蜂巢]( https://c.163.com/hub#/m/home/)




# 前言

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在大前端的环境下，作为新员工入职，当你领到新电脑时，首先你需要搭建项目所需的开发环境，不同的项目，所依赖的开发环境各有不同。如：Chrome、Postman、盗版 PS、Charles、Node, Webpack、Yarn、Sublime等基本上是必不可少的(此处省去各类插件)。现实情况是当你的开发环境所依赖的环境越多，我们在本地搭建一套环境成本就越高，即浪费时间又浪费精力，搞不好中间过程中还会遇到一些其他的坑,基本上一天下来啥也干不了了，都浪费在开发环境的搭建上了。作为一个码农，怎么可以把宝贵的时间，放在这些无聊的事上呢，所以，就有必要利用工具的手段来简化这个过程。OK,这个工具的名字叫Docker.之前早就听闻此技术，但都没有好好研究过，所以写此篇博客，以一个Docker菜鸟的视角一起来看一下Docker在前端领域的应用。

# 什么是Docker

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Docker是容器技术的一种，它运行于Linux宿主机之上，每个运行的容器都是相互隔离的，也被称为轻量级虚拟技术或容器型虚拟技术。Docker只要构建一次，即可在各种平台上运行,支持Windows、Macos、Linux。Docker解决了运行环境不一致所带来的问题。（Build once，run anything in anywhere at anytime）。


{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/docker.png "docker" %}


1.镜像（Image）：集装箱.联合文件系统UNFS
2.仓库（Repository）：超级码头.
3.容器(Container)：运行程序的地方.容器的本质就是一个进程。

用Docker运行程序的过程，就是去仓库把镜像拉倒本地，然后用一条命令把镜像运行起来，变成容器。

# MAC安装Docker

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;MAC下安装Docker有2种方式。

1.[Docker for Mac下载地址](https://download.docker.com/mac/beta/Docker.dmg)

2.使用Docker Toolbox安装（没尝试过）

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/docker%20version.png "docker version" %}


#  Docker相关命令

{% image  center clear https://img.alicdn.com/tps/TB1UifkLpXXXXXAXXXXXXXXXXXX-756-395.svg "docker" %}


| 命令        | 作用         | 
| ------------- |:-------------:|
| docker pull  nginx    | 从仓库下载镜像到本地 | 
| docker images    |   查看本机都有哪些镜像   | 
| docker ps | 查看目前正在本机上运行的容器    |  
| docker run  nginx |    运行nginx镜像 |
| docker exec -it 容器的名字或id bash|进入到已经启动的容器中 |
| docker rm c2cec4bd43a7|删除某容器 |
| docker rmi c2cec4bd43a7|删除某镜像|

# Dockerfile


{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/Cmd_logic.png "docker" %}


