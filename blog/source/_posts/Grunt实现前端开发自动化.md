clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/工大图书馆暗色调.jpg
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大图书馆暗色调.jpg
coverCaption: "工大图书馆"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大图书馆暗色调.jpg
comments: false
title: Grunt实现前端开发自动化
date: 2015-10-22 18:38:44
tags: [Grunt]
categories: [大前端技术栈]

---
Grunt是前端开发对相对任务进行自动化的任务执行工具,利用Grunt我们就可以对连接多个JS文件后的Minify(压缩)处理等作业进行自动化处理。
<!-- more -->
***
# 学习网站

 * [Grunt中文网](http://www.gruntjs.net/)


# Grunt的产生背景

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Grunt是一个执行任务的工具，在把脚本放到生产环境中之前，要做很多重复性的任务，Grunt把这些重复性的任务都自动化了。

举个例子吧：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;无论是CSS3还是JS，规模一旦变大，仅在一个文件中维护会变得非常麻烦。因此，通常会分割成多个文件。但是分割成多个文件后，浏览器读取JS或者CSS3的时候，HTTP请求就会增加，相应的响应时间就会下降。所以呢，要在项目正式上线之前，对分割后的文件进行连接操作，然后把连接后的文件返回给客户端.



# 安装Grunt命令行（CLI）工具
``` javascript
sudo npm install -g grunt-cli  
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;grunt 命令就被加入到你的系统路径中了，以后就可以在任何目录下执行此命令了。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Grunt CLI的任务很简单：调用与Gruntfile在同一目录中 Grunt。这样带来的好处是，允许你在同一个系统上同时安装多个版本的 Grunt。   

# 准备好package.json

``` javascript
    {
     "name": "my-project-name",
     "version": "0.1.0",
     "devDependencies": {    	
      }
    }
```

# 进入项目的目录中安装Grunt

``` javascript
    //安装后端的Grunt,--save-dev会把grunt加入到package.json的devDependencies中
    sudo npm install grunt --save-dev 
    //查看帮助
    grunt --help
    //查看版本号
    grunt --version
```
    
    
# 在项目的目录中创建如下三个文件夹

``` javascript
    dist
    src
    test
```
    

# 进入项目的目录中安装Grunt

``` javascript
//主要用来自动化任务运行
sudo npm install grunt-contrib-watch --save-dev
//主要用来单元测试
sudo npm install grunt-contrib-qunit --save-dev
//uglifyJS主要用来对JS文件进行压缩
sudo npm install grunt-contrib-uglify --save-dev
//主要用来合并
sudo npm install grunt-contrib-concat --save-dev
//主要用来linting
sudo npm install grunt-contrib-jshint --save-dev
```
   

# 压缩
## 准备好Gruntfile.js
``` javascript
module.exports = function(grunt) {
    // Project configuration.
    grunt.initConfig({
    uglify:{
      dist:{
        files:{
          'dist/output.min.js':['src/sample01.js','src/sample02.js']
        }
      }
    }});
    //用来从插件中读取任务,加载包含 "uglify" 任务的插件。
    grunt.loadNpmTasks('grunt-contrib-uglify');
    // 默认被执行的任务列表。
    grunt.registerTask('default', ['uglify']);
};

```



## 准备好sample01.js,放在src目录下

``` javascript
    var hello=function (user){
	    console.log("Hello,"+user.name);
    }
```
    
## 准备好sample02.js，放在src目录下


``` javascript
(function (){
		var user={"name":"naoya"};
		hello(user);
})(); 
```

	
## 执行grunt

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;可以发现在dist目录下有一个output.min.js，里面的内容就是sample01.js和sample02.js压缩后放在同一个JS文件中的代码

``` javascript
var hello=function(a){console.log(
"Hello,"+a.name)};!function(){var a={name:"naoya"};hello(a)}(); 
```

    
有一个叫做JSMin的模块也可以对代码进行压缩&nbsp;&nbsp;&nbsp;[JSMin网站](http://www.crockford.com/javascript/jsmin.html)
安装jsmin模块

``` javascript
    sudo npm install -g jsmin
```

要对一个文件进行压缩很简单，只要输入如下命令,就可以把michael.js压缩成michael.min.js

``` javascript
    jsmin -o michael.min.js  michael.js
```



