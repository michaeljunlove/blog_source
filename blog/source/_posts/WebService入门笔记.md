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
title: WebService入门笔记
date: 2015-03-23 18:38:44
tags: [WebService,SOAP,REST]
categories: [计算机基础]

---
WebService入门笔记
<!-- more -->
***
# 相关网站


 *  [国内的WebXml网站](http://www.webxml.com.cn/zh_cn/index.aspx)
 *  [ProgrammableableWeb网站](http://www.programmableweb.com/)
 *  [国外的一个关于SOAP服务的网站](http://www.service-repository.com/)
 *  [mashape网站](https://www.mashape.com/)
 *  [jersey网站]( https://jersey.java.net/)
 *  [resteasy官网]( http://resteasy.jboss.org/)(需翻墙)
 

# 什么是WebService

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WebService，又叫Web服务，顾名思义，就是基于WEB的服务。它使用Web(HTTP)方式，接收和响应外部系统的某种请求，从而实现远程调用。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;带有学术味道的定义是Web服务是一个能够完成某个特定功能的资源（软件或硬件资源），它同时还具有非功能属性（服务质量、如执行时间、费用等）。

举个例子吧：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;一个韩国人和一个日本人如果要想相互交流，怎么办呢？一个说韩语，一个说日语，他们没办法交流啊，但是如果这2个人都会说通用的英语，那么他们就可以使用英语进行交流了，对不对？

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;其实，在计算机领域呢，这个韩国人就好比JAVA语言，日本人就好比C#语言,要想JAVA和C#可以相互交流，这个担当英语的通用的语言的角色在我们现在这个例子中就是SOAP协议中是XML语言了，REST是HTTP协议。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;其实，说白了，WebService就是不同应用之间的跨平台、跨语言的调用。有了这个WebService，我们的Web应用程序就不再是孤立的了，不再是只和数据库进行交互的操作了，而是2个应用程序的远程调用，不是一个封闭的系统了。

# 目前的WebService
     
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WebService是一种思想，目前实现WebService这个思想的技术方案有以下2种方案：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.SOAP
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.REST

# 什么是SOAP-Simple Object Access protocol 简单对像访问协议。
 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SOAP干嘛用的呢？它是运行在HTTP协议基础之上的协议。其实就是在HTTP协议上传输XML文件，就变成了SOAP协议。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SOAP = 在HTTP的基础上+XML数据。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;要发布一个SOAP服务，JDK的版本一定要在1.6.0_21以后才可以。

# Web服务描述语言--WSDL

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WSDL是什么东西呢？你想啊，如果我们要使用一样东西，总要先看下使用说明书吧，不然我哪知道这玩意如何使用呢，对不对？所以啊，WSDL扮演的角色就是我们要调用的SOAP服务的使用说明书，就好像药品的使用说明书一样，我们看了以后才会知道怎么使用，WSDL通过XML的表现形式告诉我们服务所在的地址，服务提供的方法，服务提供的方法的输入参数是哪些，输出参数是哪些等等，这里就不细讲wsdl的细节啦。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WSDL=服务发布地址+?wsdl


# 什么是REST

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;REST 在 2000 年由 Roy Fielding 在博士论文中提出，他是 HTTP 规范 1.0 和 1.1 版的首席作者之一。REST其实并不是什么协议也不是什么标准，而是将Http协议的设计初衷作了诠释。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;REST 中重要的两个概念就是资源定位和资源操作，而HTTP 协议恰好完整的提供了这两个要点，HTTP 协议中的URI 可以完成资源定位，GET、POST、OPTION等方法可以完成资源操作，因此REST 完全依赖HTTP 协议就可以完成Web 服务，而不像SOAP 协议那样只利用HTTP 的传输特性，定位与操作由SOAP 协议自身完成，也正是由于SOAP 消息的存在，使得SOAP 笨重。你也可以说REST 充分利用了HTTP 协议的特性，而不是像SOAP 那样只利用了其传输这一特性（事实上大多数人提到HTTP 协议就只会想到它能用于数据传输）。更多信息请移步：

* [REST博士论文](http://wenku.baidu.com/link?url=ja10_kWoADfUHjFpfE0qF-YW4nduuthN-y-_aUuRu4CfSqwbqTA4IioMriPSHCBhcR9Kffw2xOIx6n9aH4j-3-GRitjWB4iGqM7GQGRHqX_)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在 JAX-RS 规范之前，已经有 Restlet 和 RestEasy 之类的框架，可以帮助实现 RESTful Web 服务，但是它们不够直观。Jersey 是 JAX-RS 的参考实现，它包含以下三个主要部分

>核心服务器（Core Server）：通过提供 JSR 311 中标准化的注释和 API 标准化，您可以用直观的方式开发 RESTful Web 服务。

>核心客户端（Core Client）：Jersey 客户端 API 帮助您与 REST 服务轻松通信。

>集成（Integration）：Jersey 还提供可以轻松集成 Spring、Guice、Apache Abdera 的库。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JAX-RS是JAVA EE6 引入的一个新技术。 JAX-RS即Java API for RESTful Web Services，是一个Java 编程语言的应用程序接口，支持按照表述性状态转移（REST）架构风格创建Web服务。JAX-RS使用了Java SE5引入的Java标注来简化Web服务的客户端和服务端的开发和部署。

# 使用JDK发布第一个SOAP服务

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Java API for XML Web Services（JAX-WS）是Java程序设计语言一个用来创建Web服务的API。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;开发环境：Myeclipes 10，JDK 1.7.0_15

1.首先，在Myeclipes下创建一个Java Project，工程名就叫firstWS吧。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/使用JDK发布soap服务1.jpg "使用JDK发布soap服务1" %}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;工程结构如下图所示:
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/使用JDK发布soap服务2.jpg "使用JDK发布soap服务2" %}

2.然后随便创建一个包吧，包名就叫bag了。在bag这个包内创建一个名叫HelloService的CLASS。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;工程结构如下图所示:
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/使用JDK发布soap服务3.jpg "使用JDK发布soap服务3" %}

3.HelloService的代码如下所示，这里就不讲解了，注释写的很清楚了。

``` java
package bag;
import javax.jws.WebMethod;
import javax.jws.WebService;
import javax.xml.ws.Endpoint;
/**
 * 这是一个要发布成WEB服务的类，所以要加注解@WebService
 * WebService将JAVA类标记为Web Service或者将JAVA接口标记为Web Service接口
 * @WebMethod(exclude=true)，可以阻止一个服务对外公开。
 * 如果一个类上，被添加了@WebService注解，则必须此类至少有一个可以公开的方法，否则将会启动失败。
 */
@WebService
public class HelloService {
	 /**
	  * sayHello是一个有效的方法，只要一个方法不是静态的，或者不是final的，那么就是有效的原子服务
	  * 
	  */
	 public String sayHello(String name){
            return "hello"+name;
       }
	 @WebMethod(exclude=true)
	 public String sayHello2(String name){
			return "hello " + name;
		}
	 public static void main(String[] args) {
			 /**
			  * Endpoint.publish的参数1是服务发布的地址，参数2是服务的实现者
			  * EndPoint发布完成服务以后，将会独立的线程运行。所以，publish之后的代码，可以正常执行
			  */
			Endpoint.publish("http://192.168.1.83:8080/hello", new HelloService());
			System.out.println("Server ready...");
	  }
}
```

4.这样，当我们运行这段JAVA代码的时候，一个SOAP服务就成功发布了，用户可以在浏览器中输入服务的发布的地址+?wsdl就可以查看到这个SOAP服务的WSDL了。OK,第一个SOAP服务就讲到这里吧。


# 使用jersey开发第一个REST服务

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;开发环境：Myeclipes 10，JDK 1.7.0_15

使用eclipes的用户可以参考[使用jersey构建RESTful服务](http://blog.csdn.net/kkkloveyou/article/details/21391033)这篇文章，步骤基本大同小异。

步骤一：先去[jersey网站]( https://jersey.java.net/)这个网站下载jersey的包，下载后解压后如下图所示：

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/Jersey1.png "使用jersey开发第一个REST服务1" %}

步骤二：新建一个Web Project,名字随便取一个，我这边叫JerseyRest,步骤如下图所示:

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/Jersey2.png "使用jersey开发第一个REST服务2" %}

步骤三：整个工程的目录如下图所示，把jersey文件夹下的api、ext、lib文件夹下的jar包都放到项目的lib下；

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/Jersey3.png "使用jersey开发第一个REST服务3" %}
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;放完jar包都放到项目的lib后的画面如下图所示：

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/Jersey4.png "使用jersey开发第一个REST服务4" %}

步骤四：OK,基本的准备工作都完成了，下面我们开始写程序吧。新建一个包叫bag(名字随便取，开心就好)，在bag这个包下面创建一个Class文件叫HelloResource.整个目录结构如下图所示：

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/Jersey5.png "使用jersey开发第一个REST服务5" %}

步骤五：你可以把下面的代码替换到HelloResource里面的内容

``` java
package bag;  
import javax.ws.rs.GET;  
import javax.ws.rs.Path;  
import javax.ws.rs.Produces;  
import javax.ws.rs.PathParam;  
import javax.ws.rs.core.MediaType;  
@Path("/hello")  
public class HelloResource {  
    @GET  
    @Produces(MediaType.TEXT_PLAIN)  
    public String sayHello() {  
        return "Hello World!" ;  
    }      
    @GET  
    @Path("/{param}")    
    @Produces("text/plain;charset=UTF-8")  
    public String sayHelloToUTF8(@PathParam("param") String username) {  
        return "Hello " + username;  
   }      
}  
```
步骤六：复制下面的内容到web.xml。

``` java
<servlet>    
    <servlet-name>Way REST Service</servlet-name>  
 <servlet-class>org.glassfish.jersey.servlet.ServletContainer</servlet-class>  
      <init-param>    
    <param-name>jersey.config.server.provider.packages</param-name>  
        <param-value>bag</param-value>  
       </init-param>  
   <load-on-startup>1</load-on-startup>  
 </servlet>    
 <servlet-mapping>  
   <servlet-name>Way REST Service</servlet-name>  
   <url-pattern>/rest/*</url-pattern>  
 </servlet-mapping>  
```
步骤7：部署项目到Tomcat下面，启动服务。然后访问下面链接就可以了,浏览器会输出Hello World。
``` markdown
http://localhost:8080/JerseyRest/rest/hello
```
如果在上面的访问链接后面加上/michael，则输出Hello michael.
``` markdown
http://localhost:8080/JerseyRest/rest/hello/michael
```
OK,使用jersey开发第一个REST服务就讲到这里吧。


# 服务注册流程

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;进入`云服务平台`以后，点击`云服务注册`，出现如下图所示的画面，默认的选项是去注册REST服务，服务提供方也可选择SOAP服务，注册SOAP服务只需输入该SOAP服务的WSDL即可，云服务平台会解析出该WSDL所包含的所有原子服务，本篇不细讲SOAP服务的注册流程，主要以REST服务为主。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/webservice01.png "SOAP服务和REST服务注册流程01" %}

点击下一步，出现如下图所示的界面，现对该界面进行说明

1.服务中文名称：填写一个该REST服务的中文名字，长度没有限制，简单明了，能够说明该原子服务的作用即可。

2.服务英文名称：填写一个该REST服务的英文名字，长度没有限制，那会老师让我放这么一个字段的，因为国内的服务计算领域基本没有啥发展进度，国外的基本上都是英文的，所以就放了这个字段。

3.服务功能描述：对该REST服务的详细描述。

4.服务所属领域：填写该REST服务的所属的领域。
  现规定如下：
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.1负责起重机的`张振杰`这个地方填写`起重机`
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.2负责扶梯的`叶成龙`这个地方填写`扶梯`
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.3负责电梯的`陈烘`这个地方填写`电梯`

5.服务所属来源：大家统一填写`云制造`

6.OK,接下来讲最重要的部分：服务地址、接受格式、查询方式、发送方式。云服务平台目前主要实现了`PathParam`和`QueryParam`这两种比较常用的服务接口。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6.1服务地址：服务地址是代表这个REST服务的通用的一个API，包含了用`{参数名}`表示的输入参数。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6.2接受格式：有2个值可选，`text/plain`和`text/json`,`text/plain`表示接受的是纯文本的格式，`text/json`表示接受的是json格式的

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6.3查询方式：`PathParam`和`QueryParam`这2种

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6.4发送方式：`GET`、`POST`、`PUT`、`DELETE`。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;举个例子吧,下面这个链接可以查到都有哪些Github用户关注了我的Github账号。

``` markdown
https://api.github.com/users/michaeljunlove/followers
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;上面链接中的`michaeljunlove`为我的Github用户名，这个部分在下面的链接中是可变的部分，相当于输入参数。于是，我把`michaeljunlove`这部分用`{user}`来表示这是一个输入参数，规定死了对于于是，我们的服务地址就诞生了，服务地址是代表这个REST服务的通用的一个API，如下所示。接收格式(MIME)选择`text/json`,查询方式选择`PathParam`，发送方式选择`GET`即可。

``` markdown
https://api.github.com/users/{user}/followers
```

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/webservice02.png "SOAP服务和REST服务注册流程02" %}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;填写完上面的信息以后，我们点击下一步，出现如下所示界面，填写服务输入参数信息。需要注意的是，这里的输入参数必须和服务地址中的`{user}`相对应，以之前举例的Github跟随者为例，这里就必须填`user`,然后输入该参数的中文含义即可，如果有多个输入参数，可以点击右上角的添加参数按钮。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/webservice03.png "SOAP服务和REST服务注册流程03" %}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;点击下一步，填写该REST服务的输出参数的类型和中文含义。填写完以后，点击提交即可。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/webservice04.png
 "SOAP服务和REST服务注册流程04" %}







