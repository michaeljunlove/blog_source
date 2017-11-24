clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/雨后的工大.JPG
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/雨后的工大.JPG
coverCaption: "雨后的工大-清新而自由"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/雨后的工大.JPG
comments: false
title: CSS3选择器
date: 2015-10-21 18:38:44
tags: [CSS3]
categories: [大前端技术栈]

---
选择器是CSS的根基啊，很基础的东西，要重视。
<!-- more -->
***

 * [CSS属性值语法](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Value_definition_syntax)

# CSS属性值语法


| 符号       | 含义         |
| ------------- |:-------------:|
| <属性1>空格<属性2>   |属性1和属性2都必须按顺序出现 | 
| <属性1>&&<属性2>   | 属性1和属性2都必须出现，和顺序无关 | 
| <属性1>&#124;&#124;<属性2>   | 属性1和属性2至少出现一个，和顺序无关| 
| <属性1>&#124;<属性2>   | 属性1和属性2只能出现一个| 
| []  | 组合符号| 
| + | 数量符号，可以出现一次或者多次| 
| ？| 数量符号，表示可以出现也可以不出现| 
| {2，4}| 数量符号，表示最少出现2次，最多出现4次| 
| *| 数量符号，表示可以出现0次，1次，多次| 
| #| 数量符号，表示可以出现1次或者多次，中间用逗号隔开| 


# 选择器分类
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/CSS3选择器分类.jpg "CSS3选择器分类" %}



# 基本选择器


| 选择器     | 类型          | 功能描述  |
| ------------- |:-------------:| -----:|
| *    | 通配符选择器 | 选择文档中的所有HTML元素 |
| E     | 元素选择器    |   选择指定的类型的HTML元素 |
| #id | ID选择器    |    选择指定ID属性值为“id”的元素 |
| .class| 类选择器    |    选择指定class属性值为“class”的r任意锁个元素 |
| selector1,selectorN | 群组选择器    |  将每一个选择器匹配的元素集合并 |

# 层次选择器

| 选择器     | 类型          | 功能描述  |
| ------------- |:-------------:| -----:|
| E   F   | 后代选择器 | E是F的祖先元素，E包含F，不管F是E的儿子还是孙子或者更深的包含，都会选中 |
| E > F   | 子选择器 | E是F的父元素，F为子元素，只能选择E的子元素F |
| E + F   | 相邻兄弟选择器 | E和F同辈元素，F在E的后面，并且相邻 |
| E ~ F   | 通用选择器 | 用于选择E元素相邻的后面的所有兄弟元素F |

# 伪类选择器

## 动态伪类选择器
| 选择器     | 类型          | 功能描述  |
| ------------- |:-------------:| -----:|
| E : link   | 链接伪类选择器 |  超链接没有被访问之前的效果|
| E : visited   | 链接伪类选择器 | 被访问过后的效果 |
| E : active   | 用户行为伪类选择器 | 点击激活后的效果 |
| E : hover   | 用户行为伪类选择器 | 鼠标移到上面的效果 |
| E : focus   | 用户行为伪类选择器 | 获得焦点时的效果 |

## 目标伪类选择器
| 选择器     |    功能描述  |
| ------------- | -----:|
| E : target   | 选择匹配E的所有元素，且匹配元素被相关URL指向 | 

## 语言伪类选择器 
主要用来为不同语言版本的网站相关元素设置不同的样式。如：
``` css
:lang(en) q {background: red;}
:lang(fr) {
	quotes:'«' '»';
}
```
  
		
## UI元素状态伪类选择器 
| 选择器     | 类型          | 功能描述  |
| ------------- |:-------------:| -----:|
| E : checked |选中状态伪类选择器 | 匹配选中的复选按钮或单选表单按钮元素 |
| E : enabled |启用状态伪类选择器 |匹配所有启用状态的表单元素 |
| E : disabled |不可用状态伪类选择器 |  匹配所有禁用的表单元素|

## 结构伪类选择器 
| 选择器     | 功能描述  |
| ------------- | -----:|
| E F: nth-last-child(n) | 选择元素E的倒数第n个子元素F |
| E : nth-of-type(n) | 选择父元素内具有指定类型的第n个E元素|
 | E : nth-last-of-type(n) | 选择父元素内具有指定类型的倒数第n个E元素 |
| E : first-of-type| 选择父元素内具有指定类型的第一个E元素，与 E : nth-of-type(1)相同|
| E : last-of-type| 选择父元素内具有指定类型的最后一个E元素，与 E : nth-last-of-type(1)相同|
| E : only-child| 选择父元素只包含一个子元素，且该子元素匹配E元素|
| E : only-of-type| 选择父元素只包含一个同类型的子元素，且该子元素匹配E元素|
| E : empty| 选择没有子元素的元素，且该元素不包含任何文本节点|

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/结构性伪类选择器.png "结构伪类选择器" %}


## 否定伪类选择器 
| 选择器     | 功能描述  |
| ------------- | -----:|
|E:not(F) |匹配所有除元素F外的E元素  |


# 伪元素

| 选择器     | 功能描述  |
| ------------- | -----:|
|::first-letter |用来选择文本块的第一个字母  |
|::first-line |用来匹配元素的第一行文本 |
|::before | 在标记之前可以额外插入内容的位置|
|::after | 在标记之后可以额外插入内容的位置|
|::selection | 用来匹配突出显示的文本|



# 属性选择器

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/属性选择器.png "属性选择器" %}


{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E4%B8%80%E5%9B%BE%E5%AD%A6%E4%B9%A0CSS%E9%80%89%E6%8B%A9%E7%AC%A6.jpg "CSS3选择器" %}



