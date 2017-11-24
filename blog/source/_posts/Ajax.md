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
title: Ajax
date: 2015-03-25 18:38:44
tags: [JS]
categories: [大前端技术栈]

---
经常用到的Ajax，本科做毕设的时候第一次写原生的Ajax,向服务器端发送JSON格式的游戏存档数据，现在想想那会太low了，会用Ajax都算是大神了，呵呵。现在基本上都调用Jquery了。
<!-- more -->
***
# 学习网站

* [Promise实现AJAX](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)

# Ajax


{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/AJAX01.png "XHR" %}

# 调用步骤
``` javascript
//创建XHR对象,IE的不能这样创建
var request=new XMLHttpRequest();
//open方法(要发送的请求的类型，请求的URL，是否异步发送请求的布尔值)
request.open("GET","get.php",true);
//send方法接受一个参数，即要作为请求主体发送的数据,如果不需要通过请求主体发送数据，则传入null
request.send(null);
//readyState属性的值变化时都会触发onreadystatechange
//request.status指明响应的HTTP状态
request.onreadystatechange=function(){
   if(request.readyState===4&&request.status===200){
      //获得字符串形式的响应数据
      request.responseText
      //获得XML形式的响应数据
      request.responseXML
      //获得所有响应报头
      request.getAllResponseHeader();
      //查询响应中的某个字段值
      request.getResponseHeader();
   }
}
```

# readyState属性
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/AJAX02.png "readyState" %}


# onreadystatechange

# Promise实现AJAX
```
function $http(url){
  var core = {
    ajax : function (method, url, args) {
      var promise = new Promise( function (resolve, reject) {
          var client = new XMLHttpRequest();
          var uri = url;

        if (args && (method === 'POST' || method === 'PUT')) {
          uri += '?';
          var argcount = 0;
          for (var key in args) {
            if (args.hasOwnProperty(key)) {
              if (argcount++) {
                uri += '&';
              }
              uri += encodeURIComponent(key) + '=' + encodeURIComponent(args[key]);
            }
          }
        }

        client.open(method, uri);
        client.send();
        client.onload = function () {
          if (this.status >= 200 && this.status < 300) {
            resolve(this.response);
          } else {
            reject(this.statusText);
          }
        };
        client.onerror = function () {
          reject(this.statusText);
        };
      });

      // Return the promise
      return promise;
    }
  };
  return {
    'get' : function(args) {
      return core.ajax('GET', url, args);
    },
    'post' : function(args) {
      return core.ajax('POST', url, args);
    },
    'put' : function(args) {
      return core.ajax('PUT', url, args);
    },
    'delete' : function(args) {
      return core.ajax('DELETE', url, args);
    }
  };
};

```

# XHR2
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;XHR2已经实现了跨域访问，但是IE10以下的版本都不支持。

## 使用XHR2实现异步上传

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;优点：支持H5的浏览器原生支持，不需要安装插件，交互性好。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;缺点：受浏览器支持的限制。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;表单数据序列化在WEB开发中经常用到，为此XHR2引入了FormData对象。

### 1.创建FormData对象，放入待上传的文件
```
var data=new FormData();
data.append("myfile",$("#myfile"[0].files[0]));
```

### 2.创建XHR对象

```
var xhr=new XMLHttpRequest();
```

### 3.绑定progress、load、error等事件监听传输过程并在页面动态显示交互信息

```
//xhr和xhr.upload都有progress事件
//xhr.progress代表的是下载的进度
//xhr.upload.onprogress代表的是上传的进度。
xhr.upload.onprogress=function(event){
  //判断长度是否可以计算
  if(event.lengthComputable){
     //event.loaded代表当前已经上传完成的量，event.total代表本次上传总的数据量
     var present=Math.round(event.loaded*100/event.total);
     console.log(present);
  }
}
```

```
//传输开始事件
xhr.onloadstart=function(event){
  console.log("load start");
  $("#upprog").text("开始上传");
  $("#stopbtn").one("click",function(){
     xhr.abort();     
  });
}
```
```
//onload上传成功完成事件
xhr.onload=function(){
   console.log(xhr.responseText);
   var ret=JSON.parse(xhr.responseText);
}
//onerror事件
xhr.onerror=function(){
   console.log("发生错误");
}
//onabord事件
xhr.onabord=function(){
   console.log("上传终止");
}
//onloadend传输事件，不管成功失败，都会触发
xhr.onloadend=function(){
   console.log("上传结束");
}
```
### 4.通过XHR操作将FormData对象发送到服务器，实现文件上传
```
xhr.open('POST','url',true);
xhr.send(data);
```

