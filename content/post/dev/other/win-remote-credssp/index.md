---
title: "Windows 远程时提示 CredSSP 加密数据库修正。"
date: 2021-11-13T10:30:15+08:00
slug: "win-remote-credssp"
image: error-img.png
description: "gpedit.msc->加密数据库修正->易用攻击"
categories:
    - dev
---

## 1. 打开策略控制台
Win + R 打开运行，执行以下指令
```
gpedit.msc
```

打开：计算机设置->管理模板->系统->凭据分配->加密数据库修正  

![](setting-postiton.png)

修改为：已启用->易受攻击  
![](setting.png)


> 来源  
> https://www.cnblogs.com/jinanxiaolaohu/p/13111721.html