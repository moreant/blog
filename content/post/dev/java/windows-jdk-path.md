---
title: 'Windows JDK 环境变量配置'
slug: 'windows-jdk-path'
date: 2022-04-25T10:18:22+08:00
description: Windows 真麻烦
tags:
  - Java
categories:
  - dev
---

系统变量新建 JAVA_HOME,值是 jdk 路径

```
C:\java-se-8u41-ri
```

Path 加上，如果上一个没分号就加上分号。如果是 Windows10 就不用带分号，写两条。

```
%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
```
