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
title: NVM包管理工具
date: 2016-12-29 18:38:44
tags: [NVM]
categories: [工具]

---
nvm是node版本管理工具
<!-- more -->
***
# 学习网站

 * [NVM文档](https://github.com/creationix/nvm)
 
 * [N：node版本管理工具]( https://github.com/tj/n)
 



# 什么是nvm
nvm是node版本管理工具

# 安装nvm

``` javascript
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.4/install.sh | bash
```

# 查看nvm版本号

``` javascript
nvm --version
//
0.31.4
```

# 更改镜像为淘宝的镜像

``` javascript
vi .zshrc
//拷贝如下代码
export NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node
```

# 查看可用的node版本

``` javascript
nvm ls-remote
```

# 安装对应的node版本

``` javascript
nvm install v6.9.1
```
# 切换并设置默认的node版本

``` javascript
nvm use default v6.9.1
```

# 查看本地已经安装的node版本
``` javascript
nvm ls
```

# 查看目前的node版本
``` javascript
nvm current
```