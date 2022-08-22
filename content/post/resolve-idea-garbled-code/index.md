---
title: "解决 IDEA JVM 编译中文乱码"
date: 2022-08-22T13:12:55+08:00
slug: "resolve-idea-jvm-build-chinese-garbled-code"
description: ""
image: idea-jvm-build-chinese-garbled-code.png
tags: 
    - java
    - IDEA 
categories:
    - dev
---

## 1. 打开自定义 VM 配置  
Help -> Edit Custom VM Options...  
  
![](edit_custom_vm_options.png)  

## 2. 输入以下内容  

```ini
-Dfile.encoding=UTF-8
```

## 3. 重启 IDEA  
File -> Invalidate Caches... -> Just restart
