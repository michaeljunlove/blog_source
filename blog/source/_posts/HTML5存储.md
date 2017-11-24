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
title: HTML5存储
date: 2015-09-17 18:38:44
tags: [HTML5]
categories: [大前端技术栈]

---

本篇主要讲HTML5存储的东西,涉及Cookies、localStorage、sessionStorage

<!-- more -->
***
# H5之前的存储方式--Cookies


我们知道HTTP是无状态的，在H5之前呢，为了记录用户的状态信息，是通过Cookies来实现的。

Cookies实际上就是一小段文本信息，放在用户的硬盘上。Chrom-Resources-Cookies 可以查看Cookies

Cookies的应用场合如：
  1. 安全性要求不高的场合为了避免客户重复输入名字和密码的这种身份验证
  2. 放入购物车

Cookies的缺点如下图所示，主要是

  1. Cookies在每个HTTP请求头上都会携带着
  2. 对于每个域名，最多只能在客户端存放4K大小的Cookie
  3. 如果当用户访问子域名的时候，会携带着主域名的Cookies


Cookies呀，其实在我看来，太LOW了，一点也不好玩，也不安全，跳过吧，不细讲了。

<div style="color:red;font-size:20px">
cookie的作用域是domain本身以及domain下的所有子域名.
cookie无法设置除当前域名或者其父域名之外的其他domain.
</div>


比如：A网站有个超链接到B网站，当点击该超链接时，无法从A网站携带A网站的cookie到B网站，因为A网站与B网站为不同的域名下。即cookie无法跨域。

# H5存储的目标


 <img src="http://7xid80.com1.z0.glb.clouddn.com/H5存储的目标.png" width="400px"  height="300px" alt="H5存储的目标" align=center/>



# H5存储

H5存储主要分为以下几种：

<img src="http://7xid80.com1.z0.glb.clouddn.com/具体的H5存储.png" width="600px"  height="400px" alt="H5存储" align=center/>
 <img src="http://7xid80.com1.z0.glb.clouddn.com/H5存储的区别.png" width="400px"  height="400px" alt="H5存储的区别" align=center/> 

## 一.本地存储
1. localStorage是永久存在的，不过期的，除非你手动删除掉。
2. sessionStorage是当你重新打开页面，关闭浏览器，那么sessionstorage就消失了。
3. 存储大小为5MB
基本上，主流浏览器都是支持本地存储的。
### 下面，我们来看看本地存储都可以存放哪些东西吧。
 <img src="http://7xid80.com1.z0.glb.clouddn.com/H5本地存储.png" width="600px"  height="400px" alt="H5本地存储都可以存哪些东西呢" align=center/>
### 看下API吧
 <img src="http://7xid80.com1.z0.glb.clouddn.com/H5本地存储API.png" width="300px"  height="400px" alt="H5本地存储API" align=center/>
### 本地存储的使用场景
 <img src="http://7xid80.com1.z0.glb.clouddn.com/H5本地存储的使用场景.png" width="500px"  height="400px" alt="H5本地存储使用场景" align=center/>
### 本地存储还是有一些注意事项的。
 <img src="http://7xid80.com1.z0.glb.clouddn.com/H5本地存储的限制.png" width="400px"  height="400px" alt="H5本地存储的限制" align=center/> 





