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
title: React学习笔记
date: 2015-10-20 18:38:44
tags: [React]
categories: [大前端技术栈]

---
这篇讲React的，可能不适合初学者吧，至少我认为是不适合的，行文逻辑没有做到循序渐近,但是相应的知识点应该都涉及到了的。函数式编程是React的核心

<!-- more -->
***
# 学习的网站

 * [阮一峰-React 入门实例教程](http://www.ruanyifeng.com/blog/2015/03/react.html)
 
 * [React 中文网 ]( http://reactjs.cn/react/index.html)
 
 * [React组件如何划分]( http://reactjs.cn/react/docs/thinking-in-react.html)
 
 * [redux-devtools]( https://github.com/gaearon/redux-devtools)
 
 * [【第567期】通往全栈工程师的捷径 —— React](  https://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651220482&idx=1&sn=63e0a1d4a2fd65831fed724b996a677e&mpshare=1&scene=1&srcid=1218XkX5exsUecfLqXIcVcSc&pass_ticket=kviaocubuXtmkTsC44Yy4rwaoWS05jsRxDt4AaNZ4Z1TdKtSPopUrBTRniU8kLZc#rd)
 
 * [【第792期】React 源码剖析系列－生命周期的管理艺术](  https://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651224539&idx=1&sn=8e46ca905375c8bce273881fe7069c6b&chksm=bd49a05f8a3e2949b8e2336dd28558e1791eb1787c5022fa5e5f8c3508dd550243d00c0fbb5d&mpshare=1&scene=1&srcid=1218dMq8sS2iPFBwwGYSA8TI&pass_ticket=kviaocubuXtmkTsC44Yy4rwaoWS05jsRxDt4AaNZ4Z1TdKtSPopUrBTRniU8kLZc#rd)
 

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/react.png "React生命周期整体流程图" %}

 

# React简介

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在Web开发中，我们总需要将变化的数据实时反应到UI上，这时就需要对DOM进行操作。而复杂或频繁的DOM操作通常是性能瓶颈产生的原因（如何进行高性能的复杂DOM操作通常是衡量一个前端开发人员技能的重要指标）。

## React的原理

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;React为此引入了虚拟DOM（Virtual DOM）的机制：在浏览器端用Javascript实现了一套DOM API。基于React进行开发时所有的DOM构造都是通过虚拟DOM进行，每当数据变化时，React都会重新构建整个DOM树，然后React将当前整个DOM树和上一次的DOM树进行对比，得到DOM结构的区别，然后仅仅将需要变化的部分进行实际的浏览器DOM更新。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;而且React能够批处理虚拟DOM的刷新，在一个事件循环（Event Loop）内的两次数据变化会被合并，例如你连续的先将节点内容从A变成B，然后又从B变成A，React会认为UI不发生任何变化，而如果通过手动控制，这种逻辑通常是极其复杂的。尽管每一次都需要构造完整的虚拟DOM树，但是因为虚拟DOM是内存数据，性能是极高的，而对实际DOM进行操作的仅仅是Diff部分，因而能达到提高性能的目的。这样，在保证性能的同时，开发者将不再需要关注某个数据的变化如何更新到一个或多个具体的DOM元素，而只需要关心在任意一个数据状态下，整个界面是如何Render的。
## 组件化的开发思路

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;虚拟DOM不仅带来了简单的UI开发逻辑，同时也带来了组件化开发的思想。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;所谓组件，即封装起来的具有独立功能的UI部件。React推荐以组件的方式去重新思考UI构成，将UI上每一个功能相对独立的模块定义成组件，然后将小的组件通过组合或者嵌套的方式构成大的组件，最终完成整体UI的构建。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/react介绍.png "React介绍" %}




# JSX

## 什么是JSX

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JSX（Javascript XML）是一种在React组件内部构建标签的类XML语法,JSX=HTML+JS,使用JSX可以提高组件的可读性。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JSX是Facebook为React框架开发的一套语法糖，语法糖是指计算机语言中添加的某种语法，这种语法对语言的功能并没有影响，但是更方便程序员使用。通常来说使用语法糖能够增加程序的可读性，从而减少程序代码出错的机会。

## JSX的特点
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/JSX特点.png "JSX特点" %}

## JSX的语法
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.JSX代码要放在&lt;script type="text/jsx">和 &lt;/script>之间

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.HTML 语言直接写在 JavaScript 语言之中，不加任何引号，它允许 HTML 与 JavaScript 的混写

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.遇到 HTML 标签（以 < 开头），就用 HTML 规则解析；遇到代码块（以 { 开头），就用 JavaScript 规则解析

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.JSX将2个花括号之间{name}的内容渲染为动态值,如果这个变量（比如name）是一个数组，则遍历展开数组。{}这个叫取值表达式

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.注释可以添加在JSX的HTML语言中，用{}把注释包起来。单行注释用`//`,多行注释用`/* */`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6.条件判断，在{}中不能使用语句，可以使用求值表达式。要想在组件中添加条件判断，有4种方法（在最后附录里）。
# 组件

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在React中，构建页面的基础元素的是组件，其实组件相当于具有JS表达能力的HTML元素。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;组件的设计目的是为了提高代码的复用率，降低测试难度和代码的复杂度，使得代码模块化。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;本质上，组件就是一个Javascript函数，它接受属性和状态作为参数，并输出渲染好的HTML。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;React鼓励开发者为每一个关注点创造一个独立的组件，并把所有的逻辑和标签封装在其中。组件的创建应遵循单一功能原则，指的是，理想状态下一个组件应该只做一件事，假如它功能逐渐变大就需要被拆分成更小的子组件。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.自定义的组件，首字母要大写，说明是自定义的组件。DOM组件的首字母是小写。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.React.createClass方法用来创建一个组件，render方法用于将模板转为HTML语言。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.添加组件属性，有一个地方需要注意，就是 class 属性需要写成 className ，for 属性需要写成 htmlFor

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.组件的命名采用驼峰命名格式

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.可以在组件中使用立即执行表达式

# 非DOM属性

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_非DOM属性.png "非DOM属性" %}

## Key

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key是一个可选的唯一标识符。在程序的运行过程中呢，一个组件可能会在组件树中调整位置（比如:在用户搜索的时候，列表中的物品会被增加或者删除），存在情况，组件可能不需要被销毁并重新创建。通过给组件设置一个独一无二的键，并确保它在一个渲染周期中保持一致，使得React能够更智能地决定应该重用一个组件，还是销毁并创建一个组件，进而提升渲染性能。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;一个组件的内部的Key不可以相同

## ref

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ref允许父组件在render方法之外保持对一个子组件的一个引用。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;使用this.refs获得本组件的所有ref

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通过引用获取到的这个对象被成为支持实例。它不是真正的DOM，而是React在需要的时候，用来创建DOM的一个描述对象。通过`this.refs.ref的属性值.getDOMNode()`来访问真实的DOM节点。

## dangerouslySetInnerHTML
有时候，我们需要把HTML的内容设置成字符创，尤其是使用了字符串操作DOM的第三方库的时候。为了提升React的互操作性，才有这么一个属性。
``` javascript
<script type="text/jsx">
        var rawHTML={
            __html:"<h1>hello michael!</h1>"
        };

        React.render(
                <div dangerouslySetInnerHTML={rawHTML}></div>,
                document.getElementById('example')
        );
</script>
```
    
## React的Diff算法用来计算2个组件之间的差异。

1.先判断2个节点是否相同。比如：`div`与`div`是相同的节点，`div`与`p`是不同的节点，或者自己定义的组件的名字是否是同一个组件名。比如：`HelloMessage`与`HelloMessage`是同一个组件。`HelloMessage`与`HelloWorld`是不同的组件。

2.判断完节点是否相同后，如果节点不同，则重新生成一个新的节点。
如果节点相同，则判断这个节点是自己定义的节点还是DOM标准的节点。

3.然后，在比较节点的属性，如果节点的属性相同，则结束比较。如果属性不同，则对属性进行操作，比如：多了一个属性，则加入这个属性，少了一个属性，则删掉这个属性。

4.重新渲染。把组件的新的状态传递到组件中
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_diff算法.png "Diff算法" %}



# 生命周期

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;组件在本质上就是一个状态机，输入确定，输出也确定。在状态发生转换的时候，会触发不同的钩子函数，从而让开发者有机会做出响应。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_组件的生命周期.png "组件的生命周期" %}
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_初始化.png "组件的初始化" %}
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_运行中.png "组件的运行中" %}
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_销毁.png "组件的销毁" %}



# 属性和状态

## 属性
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;属性就是props，是properties的缩写。主要作用是把任意类型的数据传递给组件。一个组件不可以自己修改自己的属性。在 React 中，数据流是自上而下单向的从父节点传递到子节点，子组件只需要从父节点提供的 props 中获取数据并渲染即可。如果顶层组件的某个 prop 改变了，React 会递归地向下遍历整棵组件数，重新渲染所有使用这个属性的组件。对于组件来说,props永远是只读的。React 有一个 PropTypes 属性校验工具，经过简单的配置即可。当使用者传入的参数不满足校验规则时，React 会给出非常详细的警告，方便定位问题。


属性的调用方法有如下三种：
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_%20属性的用法.png "属性的用法" %}


## 状态

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;状态就是state，每一个组件都可以拥有自己的状态。组件就是一个有限状态机。state 一般和事件一起使用。
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_状态的用法.png "属性和状态的相似点" %}

## 属性和状态的相似点
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_属性和状态的相似点.png "属性和状态的相似点" %}

## 属性和状态的区别：
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_属性和状态的区别.png "属性和状态的区别" %}


组件在运行时候，需要修改的数据就是状态，除此之外，就是属性。

# 事件

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;对于用户的操作，React通过将事件处理器绑定到组件上来处理事件。在事件被触发的同时，更新组件的内部的状态。组件内部的状态的更新将会导致重绘。
# 数据流

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在React中，数据的流向是单向的，从父组件传递到子组件。如果顶层组件的某个prop改变了，React会递归地向下遍历整棵树，重新渲染所有使用这个属性的组件。

# 组建的复合

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;复合讲的是通过结合小巧、简单的的组件和数据对象，构造强大而复杂的组件。

## 1.组件嵌套:组件嵌套的本质是父子关系。

父组件通过属性和子组件进行通信。
子组件和父组件的通信是一种间接的通信方式。父组件通过事件处理函数把属性传递给子组件。子组件如果触发了事件，就可以调用父组件的事件处理函数。这样就间接的实现了子组件和父组件的通信。这种方式叫做委托。
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/React_组件的嵌套.png "组件的嵌套" %}

父组件通过定义子组件的props来和子组件进行通信，子组件如果想要和父组件通信，则通过委托的方式，即父组件嵌套子组件，父组件的处理函数通过属性的方式赋值组子组件，如在父组件中插入：`<CommentForm onCommentSubmit={this.handleCommentSubmit} />`。子组件CommentForm中通过触发事件，委托调用父组件的处理函数，如：`this.props.onCommentSubmit({author: author, text: text});`从而实现把值传给父组件。





## 2.mixin

mixin允许我们定义可以在多个组件中共用的方法。目的是横向抽离出组件的相似代码。其实，mixin就是一个对象，里面有一些通用的代码。


## 条件判断的4种写法
``` javascript
<script type="text/jsx">
        //方法一，使用三元表达式,因为HelloMessage这个标签没有name属性，所以最后显示Hello React
        var HelloMessage=React.createClass({
            render:function(){
                return <h1>Hello {this.props.name?this.props.name:'React'}</h1>
            }
        });
        React.render(
                <HelloMessage/>,
                document.getElementById('example')
        );
        //方法二，设置一个变量并在属性中引用它,可以使用函数给这个变量赋值,输出Hello michael
        var HelloMessage=React.createClass({
            render:function(){
                var name=this.props.name;
                return <h1>Hello {name}</h1>
            }
        });
        React.render(
                <HelloMessage name="michael"/>,
                document.getElementById('example')
        );
         //方法三，在{}中直接调用函数
        var HelloMessage=React.createClass({
            getName:function(){
                if(this.props.name){
                    return this.props.name;
                }else{
                    return 'michael'
                }
            },
            render:function(){

                return <h1>Hello {this.getName()}</h1>
            }
        });
        React.render(
                <HelloMessage name="michael"/>,
                document.getElementById('example')
        );
        //方法四，使用||或者&&逻辑运算符
        var HelloMessage=React.createClass({
            render:function(){

                return <h1>Hello {this.props.name||'world'}</h1>
            }
        });
        React.render(
                <HelloMessage name="michael"/>,
                document.getElementById('example')
        );
</script>
```


# ES6下的REACT

为了使React能在更多的不同环境下更快、更容易构建。于是在React 0.14 把react分成了react和react-dom两个部分。这样就为web版的react和移动端的React Native共享组件铺平了道路。也就是说我们可以跨平台使用相同的react组件。
  
# 一般组价的写法

```
import React, { Component } from 'react'
import PropTypes from 'prop-types';

export default class ComponentName extends Component {

    //props属性类型检查
    static propTypes = {

    }

    //props属性默认类型
    static defaultProps ={

    }

    //构造函数
    constructor(props){
        super(props);
        this.state={};
    }

    //render执行前执行一次
    componentWillMount (){

    }

    //render执行后执行一次
    componentDidMount (){

    }

    //父组件更新属性，子组件会接受到新的属性，在这里更新state
    componentWillReceiveProps (nextProps){
        this.setState({});
    }

    //_开头的私有方法
    _dosomething = () =>{

    }

    //handle事件处理
    handle= () =>{

    }

    //render
    render(){

    }
}
```

# 无状态组件

无状态组件在创建时始终保持一个实例，避免了不必要的检查和内存分配，做到了内部的优化，所以在合适的情况下，尽量使用无状态组件


