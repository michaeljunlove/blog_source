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
title: JS单元测试框架
date: 2016-07-22 18:38:44
tags: [Jasmine,Karma]
categories: [工具]

---
Jasmine是一款行为驱动开发BDD测试框架。Karma是测试框架，支持jasmine,mocha,qunit,是一个以nodejs为环境的npm模块.
<!-- more -->
***
# 学习网站

 * [Jasmine官网](http://jasmine.github.io/edge/introduction.html)
 
 * [Karma官网]( https://karma-runner.github.io/1.0/index.html)

 * [Jest官网](  http://facebook.github.io/jest/zh-Hans/)

 * [difference-between-tdd-and-bdd]( http://joshldavis.com/2013/05/27/difference-between-tdd-and-bdd/)
 

 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Jasmine是一个用来编写Javascript测试的框架，它不依赖于任何其它的javascript框架，也不需要对DOM。Karma是一个基于Node.js的JavaScript测试执行过程管理工具（Test Runner）,测试主流web浏览器，可集成到CI工具，可提供代码覆盖率报告，命令行直接控制jasmine进行接口测试。

![](http://7xid80.com1.z0.glb.clouddn.com/jasmine.png)


* lib文件夹是jasmine的源文件
* spec文件夹需要存放测试代码
* SpecRunner.html是jasmine执行结果的页面
* src文件夹里面存放的是被测js文件


| API        | 描述         | 用法 |
| ------------- |:-------------:| -----:|
| describe     | 定义测试集 | describe("描述测试内容",function(){//测试代码})  |
| it     | 定义测试用例  | it("描述测试内容",function(){//测试代码}) |
| expect |  程序断言来判断相等关系   |    expect(true).toEqual(true)  |
| beforeEach |  在测试用例执行之前的设置  |beforeEach(function() {//设置初始化});|
| afterEach | 在测试用例执行之后的设置  |  afterEach(function() {//重置初始化});|
| beforeAll | 在所有测试用例执行之前执行一次  |  beforeAll(function() {//设置初始化});|
| afterAll | 在所有测试用例执行之后执行一次  |  afterAll(function() {//重置初始化});|






 



