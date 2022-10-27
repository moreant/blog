---
title: "IDEA 项目启动报错 Command line is too long"
slug: "idea-command-line-is-too-long"
date: 2021-07-15T10:10:00+08:00
description: 推荐使用 JAR 的方法
tags: 
    - java
categories:
    - dev
---

## 直接修改配置文件的方法
在项目的 .idea/workspace.xml 文件中，找到 

```xml
<component name="PropertiesComponent">
```  

下面添加一行

```xml
<property name="dynamic.classpath" value="true" />
```  

## JAR 的方法 （推荐）
最近又发现了一个新的办法，不需要记命令。具体方法如下

1. On the edit configuration menu, click on modify options
2. And then select Shorten command line
3. Select JAR manifest option, apply & run

![](http://store.tptp.net/md/2022/10/1f6d1128de0e86b4f856ec7ece111bb0.png)

原帖地址： https://stackoverflow.com/a/69349044/13621750
