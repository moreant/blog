---
title: "IDEA 项目启动报错 Command line is too long"
slug: "idea-command-line-is-too-long"
date: 2021-07-15T02:10:00+08:00
description: PropertiesComponent 添加 <property name="dynamic.classpath" value="true" />
---

在项目的 .idea/workspace.xml 文件中，找到 

`<component name="PropertiesComponent">`

下面添加一行

`<property name="dynamic.classpath" value="true" />`