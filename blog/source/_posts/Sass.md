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
title: Sass
date: 2016-05-28 18:38:44
tags: [Markdown]
categories: [工具]

---
CSS 预处理器定义了一种新的语言，其基本思想是，用一种专门的编程语言，为 CSS 增加了一些编程的特性，将 CSS 作为目标生成文件，然后开发者就只要使用这种语言进行编码工作。
<!-- more -->
***
# 学习网站

 * [Sass官网](http://sass-lang.com/)
 
 * [慕课网Sass入门篇](http://www.imooc.com/learn/311)

# Sass简介

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Sass 是采用 Ruby 语言编写的一款 CSS 预处理语言，它诞生于2007年，是最大的成熟的 CSS 预处理语言。由于 Sass 是基于 Ruby 写出来，所以其延续了 Ruby 的书写规范。在书写 Sass 时不带有大括号和分号，其主要是依靠严格的缩进方式来控制的。

# demo

``` markdown
$font-stack: Helvetica, sans-serif  //定义变量
$primary-color: #333 //定义变量
body
  font: 100% $font-stack
  color: $primary-color
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;编译出来的 CSS
``` markdown
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}
```
# 安装Sass

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;因为sass依赖于ruby环境，所以装sass之前先确认装了ruby。MAC下通过`ruby -v`查看是否安装了ruby.

``` javascript
sudo gem install sass
```
结果发现报错： Unable to download data from https://rubygems.org/

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/sass%E5%AE%89%E8%A3%85%E6%8A%A5%E9%94%99.png "sass安装报错" %}


解决方案：
``` javascript
gem sources --remove https://rubygems.org/
gem sources -a https://ruby.taobao.org/
gem sources -l
//显示
*** CURRENT SOURCES ***
https://ruby.taobao.org/
```

# 升级sass版本

``` javascript
gem update sass
```

# 查看sass版本

``` javascript
sass -v
//Sass 3.4.22 (Selective Steve)
```
# 卸载（删除）Sass

``` markdown
gem uninstall sass
```
