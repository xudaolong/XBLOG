---
title: intellj-idea-maven-Web项目-+-tomcat-的搭建
date: 2016-09-11
categories: 
- intellj-idea
---

> 新入职公司,对公司内部的系统进行搭建,在此进行记录

> 思路如下

``  导入 maven 项目 相关的jar 包-->关联相关的框架 --> 配置tomcat 的处理 ``

> 导入项目,选择maven框架,一直点next

> 进入之后更新jar包,和导入必要的包


![下载maven包](http://upload-images.jianshu.io/upload_images/80378-a522c56b975d7f0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> 然后添加相关联的框架,如Spring


![Spring.png](http://upload-images.jianshu.io/upload_images/80378-914a950a58d6a196.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> 配置tomcat 

![tomcat.png](http://upload-images.jianshu.io/upload_images/80378-e97aa9047f65208f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 点开项目结构,依次步骤


![指定classes路径](http://upload-images.jianshu.io/upload_images/80378-fecec8e1a9a14166.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![编译输出class路径](http://upload-images.jianshu.io/upload_images/80378-b57965a47e5cbf08.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![添加TOMCAT以及必要的jar包](http://upload-images.jianshu.io/upload_images/80378-925ff6a2239606c1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![设置Artifacts](http://upload-images.jianshu.io/upload_images/80378-95271924955f9926.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)












