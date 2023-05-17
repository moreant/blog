---
title: 'IDEA 项目启动报错 Command line is too long'
slug: 'fix-idea-project-startup-error-command-line-is-too-long'
date: 2021-07-15T10:10:00+08:00
description: 推荐使用 JAR 的方法
tags:
  - Java
categories:
  - dev
---

## 最简单的方法
在错误信息中直接点击 JAR，IDEA 就会自动帮你添加配置，再次启动即可。
![](notifications.webp)

## 纯 GUI 的方法

最近又发现了一个新的办法，不需要记命令。具体方法如下

1. On the edit configuration menu, click on modify options
2. And then select Shorten command line
3. Select JAR manifest option, apply & run

![](setting.webp)

原帖地址： https://stackoverflow.com/a/69349044/13621750

## 直接修改配置文件的方法

在项目的 .idea/workspace.xml 文件中，找到

```xml
<component name="PropertiesComponent">
```

下面添加一行

```xml
<property name="dynamic.classpath" value="true" />
```