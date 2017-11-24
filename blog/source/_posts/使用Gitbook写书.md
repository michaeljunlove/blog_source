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
title: 使用Gitbook写书
date: 2017-03-23 18:38:44
tags: [Gitbook]
categories: [工具]

---
Gitbook
<!-- more -->
***
# 学习网站


 * [gitbook](https://github.com/GitbookIO/gitbook)
 

# 安装Gitbook

``` markdown
npm install -g gitbook-cli
//检验是否安装成功
gitbook -V
//创建一个目录
mkdir test_gitbook
cd test_gitbook
```

# 创建目录 

``` markdown
//生成一个目录文件
touch SUMMARY.md
//输入
* [简介](README.md)
* [第一章](chapter1/README.md)
 - [第一节](chapter1/section1.md)
 - [第二节](chapter1/section2.md)
* [第二章](chapter2/README.md)
 - [第一节](chapter2/section1.md)
 - [第二节](chapter2/section2.md)
* [结束](end/README.md)
```


# 根据目录生成图书结构


``` markdown
gitbook init
```


# 本地在线预览


``` markdown
gitbook serve
```

