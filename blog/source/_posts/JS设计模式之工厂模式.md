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
title: JS设计模式之工厂模式
date: 2016-05-04 18:38:44
tags: [JS]
categories: [设计模式]

---
工厂模式主要定义了一个用于创建对象的接口，其本质是封装了创建对象的实现细节，对象的创建处理过程被予以抽象。
<!-- more -->
***
# 学习网站

 * [免费看极客学院视频](http://www.sunnyos.com/video/jike.html)

 * [极客学院JS设计模式之工厂模式](http://www.jikexueyuan.com/course/655.html)
 



# 简单工厂模式

``` javascript
//先定义一个创建工厂的对象
var FormFieldFactory={
	//makeField方法使用以下2个选项
	//type,定义所创建的表单域对象的类型
	//displayText,定义表单域的placeholder文本或者按钮上所显示的文本
	makeField:function(options){
		var options=options||{},
		    type=options.type||"text",
		    displayText=options.displayText||"",
		    field;
        //根据type来选择创建对应的对象
		switch(type){
			case"text":
			    field=new TextField(displayText);
			    break;
			case"email":
			    field=new EmailField(displayText);
			    break;
			case"button":
			    field=new ButtonField(displayText);
			    break;
			default:
			    field=new TextField(displayText);
			    break;
		}
		return  field;
	}
};
//定义各个组件部分的类
function TextField(displayText){
	this.displayText=displayText;
}
TextField.prototype.getElement=function(){
	var textField=document.createElement("input");
	textField.setAttribute("type","text");
	textField.setAttribute("placeholder",this.displayText);
	return textField;
}
function EmailField(displayText){
	this.displayText=displayText;

}
EmailField.prototype.getElement=function(){
	var EmailField=document.createElement("input");
	EmailField.setAttribute("type","email");
	EmailField.setAttribute("placeholder",this.displayText);
	return EmailField;
}
function ButtonField(displayText){
    this.displayText=displayText;
}
ButtonField.prototype.getElement=function(){
	var button=document.createElement("button");
	button.setAttribute("type","submit");
	button.innerHTML=this.displayText;
	return button;
}
```

## 使用工厂模式

``` javascript
/使用工厂模式
var textField=FormFieldFactory.makeField({
    type:"text",
    displayText:"Enter the first line of your address"
});
var emailField=FormFieldFactory.makeField({
    type:"email",
    displayText:"Enter your email address"
});
var buttonField=FormFieldFactory.makeField({
    type:"button",
    displayText:"submit"
});
//加载DOM到当前页面
window.addEventListener("load",function(){
	var bodyElement=document.body;
	bodyElement.appendChild(textField.getElement());
	bodyElement.appendChild(emailField.getElement());
	bodyElement.appendChild(buttonField.getElement());
});
```
# 抽象工厂模式

``` markdown
1.文本1
```


