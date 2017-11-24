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
title: CSS画图形
date: 2016-04-10 18:38:44
tags: [CSS3]
categories: [大前端技术栈]

---
CSS3动画相关的属性
<!-- more -->
***
# DOM
 给我一个DIV标签就可以啦，后面相应的样式自己填进去就可以了。
``` markdown
    <!DOCTYPE HTML>
    <html lang="en-US">
    <head>
	<meta charset="UTF-8">
	<title>michael</title>
    <style type="text/css"></style>
    </head>
    <body>
	    <div></div>
    </body>
    </html>
```
# 画正方形

画长方形也一样，自己设置长和宽
``` markdown
    div {
      width: 100px;
      height: 100px;
      background-color: orange;
    }
```
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/CSS3画正方形.png "CSS3画正方形" %}

# 画圆
``` markdown
     div {
      width: 100px;
      height: 100px;
      background-color: orange;
      border-radius: 50%;
    }
```
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/CSS3画圆.png "CSS3画圆" %}


# 画半圆
``` markdown  
    .semicircle {
      background-color: orange;
      margin: 30px;
    }
    .top {
      width: 100px;
      height: 50px;
      border-radius: 50px 50px 0 0;
    }
    .right {
      height: 100px;
      width: 50px;
      border-radius: 0 50px 50px 0;
    }
    .bottom {
      width: 100px;
      height: 50px;
      border-radius: 0 0 50px 50px;
    }
    .left {
      width: 50px;
      height: 100px;
      border-radius: 50px 0 0 50px;
    }
 <div class="semicircle top"></div>
	<div class="semicircle right"></div>
	<div class="semicircle bottom"></div>
	<div class="semicircle left"></div>
```
 	
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/CSS3画半圆.png "CSS3半圆" %}	
# 画椭圆
``` markdown     
    .oval {
      background-color: orange;
      margin: 30px;
    }
    .hov {
      width: 100px;
      height: 50px;
      border-radius: 100px / 50px;
    }
    .ver {
      width: 50px;
      height: 100px;
      border-radius: 50px  / 100px;
    }
    <div class="oval hov"></div>
	<div class="oval ver"></div>
```
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/CSS3画椭圆.png "CSS3画椭圆" %}	


# 画扇形
``` markdown     
    .quarterCircle {
      background-color: orange;
      margin: 30px;      
    }
    .top {
      width: 100px;
      height: 100px;
      border-radius: 100px 0 0 0;
    }
    .right {
      width: 100px;
      height: 100px;
      border-radius: 0 100px 0 0;
    }
    .bottom {
      width: 100px;
      height: 100px;
      border-radius: 0 0  100px 0;
    }
    .left {
      width: 100px;
      height: 100px;
      border-radius: 0 0 0 100px;
    } 
 <div class="quarterCircle top"></div>
	<div class="quarterCircle right"></div>
	<div class="quarterCircle bottom"></div>
	<div class="quarterCircle left"></div>   
```
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/CSS3画扇形.png "CSS3画扇形" %}	



# 画三角形
``` markdown
 #triangle-up {
    	width: 0;
    	height: 0;
    	border-left: 50px solid transparent;
    	border-right: 50px solid transparent;
    	border-bottom: 100px solid orange;
	}
	#triangle-down {
    	width: 0;
    	height: 0;
    	border-left: 50px solid transparent;
    	border-right: 50px solid transparent;
    	border-top: 100px solid orange;
	}
	#triangle-left {
    	width: 0;
    	height: 0;
    	border-top: 50px solid transparent;
    	border-right: 100px solid orange;
    	border-bottom: 50px solid transparent;
	}
	#triangle-right {
    	width: 0;
    	height: 0;
    	border-top: 50px solid transparent;
    	border-left: 100px solid orange;
    	border-bottom: 50px solid transparent;
	}
	#triangle-topleft {
    	width: 0;
    	height: 0;
    	border-top: 100px solid orange;
    	border-right: 100px solid transparent;
	}
	#triangle-topright {
    	width: 0;
    	height: 0;
    	border-top: 100px solid orange;
    	border-left: 100px solid transparent;
	}
	#triangle-bottomleft {
    	width: 0;
    	height: 0;
    	border-bottom: 100px solid orange;
    	border-right: 100px solid transparent;
	}
	#triangle-bottomright {
    	width: 0;
    	height: 0;
    	border-bottom: 100px solid orange;
    	border-left: 100px solid transparent;
	}
```
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/css%E7%94%BB%E4%B8%89%E8%A7%92%E5%BD%A2.png "CSS3画三角形" %}	

# 画平行四边形
``` markdown
    #parallelogram { 
        width: 150px; 
        height: 100px; 
        -webkit-transform: skew(-20deg); 
        -moz-transform: skew(-20deg);
         -o-transform: skew(-20deg); 
         background: orange;
         margin-left:20px; 
    }
```

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/CSS3画平行四边形.png "CSS3画平行四边形" %}	








