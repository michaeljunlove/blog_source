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
title: Chales使用指南
date: 2017-03-23 18:38:44
tags: [Charles]
categories: [工具]

---
Chales使用指南
<!-- more -->
***
# 学习网站


 * [Charles官网(需翻墙)](https://www.charlesproxy.com/)
 
 * [抓包教程](http://www.jianshu.com/p/5539599c7a25)
 
 * [Charles 从入门到精通]( http://blog.devtang.com/2015/11/14/charles-introduction/)
 
 * [charles是如何抓取https数据包的](http://legendtkl.com/2015/11/30/charles-https/)

 * [charles持续破解教程]( http://charles.iiilab.com/)

 



# Charles简介

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Charles 是在 Mac 下常用的网络封包截取工具，在做移动开发时，我们为了调试与服务器端的网络通讯协议，常常需要截取网络封包来分析。



# 需求一：把线上代码代理到本地、调试线上bug

1.首先移动端设置HTTP代理，设置好服务器的IP地址，即你本地电脑在局域网中的IP，端口号为8888。

2.在移动端访问对应的网页，让Chales抓取到该请求。设置
<div style="display:flex;justify-content: center;">
<img  width=400px height= 400px src="http://7xid80.com1.z0.glb.clouddn.com/charles1.png" />
</div>

3.设置Map Remote
<div style="display:flex;justify-content: center;">
<img  width=400px height= 400px src="http://7xid80.com1.z0.glb.clouddn.com/charles2.png" />
</div>

4.设置好以后，在APP内访问对应的链接，就会重定向到本地的开发环境了。

# 需求二：截取移动设备中的 Https 通讯信息

1.MAC上点击 Charles 的顶部菜单，选择 “Help” -> “SSL Proxying” -> “Install Charles Root Certificate”，然后输入系统的帐号密码，即可在 KeyChain 看到添加好的证书。

<div style="display:flex;justify-content: center;">
<img  width=300px height="300px" src="http://7xid80.com1.z0.glb.clouddn.com/https.png" alt="电脑安装SSL证书"/>
</div><br/>


2.在钥匙串中对该证书进行信任

<div style="display:flex;justify-content: center;">
<img  width=300px height="300px" src="http://7xid80.com1.z0.glb.clouddn.com/https2.png" alt="对该证书进行信任"/>
</div><br/>

3.“Help” -> “SSL Proxying” -> “Install Charles Root Certificate on a Mobile Device”
<div style="display:flex;justify-content: center;">
<img  src="http://7xid80.com1.z0.glb.clouddn.com/https3.png?id=2" alt="电脑安装SSL证书"/>
</div><br/>


4.手机连接代理到MAC电脑上，设置好服务器的IP地址，即你本地电脑在局域网中的IP，端口号为8888。打开手机上的浏览器访问chls.pro/ssl下载，安装证书到手机上。

5.通用->关于本机->证书信任设置->CA勾选（不然去抓https的包，会一直报unknown。证书一定要和电脑匹配） 