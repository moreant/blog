---
title: "ssh自动登录"
date: "2021-09-29T23:09:11+08:00"
slug: "ssh-auto-login"
description: "只需要 ssh name 就登录了"
image: ssh-logo.png
tags: 
    - linux
categories:
    - dev
---

 ~/.ssh 到ssh目录 如果没有就新建一个  
生成指定的文件名 keyname  
```bash
ssh-keygen -f keyname
```
把公钥文件拷贝到指定的服务器  
```bash
ssh-copy-id -i keyname.pub root@hostname 
``` 

在.ssh/config 配置文件中加上连接配置即可  
```
HOST sshname
    HostName hostname
    user root
    IdentityFile ~/.ssh/keyname
```

之后就可以用 ssh sshname 登录了

> 来源：  
> https://segmentfault.com/q/1010000002445731

