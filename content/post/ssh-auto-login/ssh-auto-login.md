---
title: "Vite 项目启动 esbuild 异常"
date: 2021-08-30T01:23:15+08:00
slug: "ssh-auto-login"
description: "ssh自动登录"
image: ssh-logo.jpg
tags: 
    - linux
categories:
    - dev
---

 ~/.ssh 到ssh目录 如果没有就新建一个
ssh-keygen -f keyname 生成指定的文件名 keyname
ssh-copy-id -i keyname.pub root@hostname 把公钥文件拷贝到指定的服务器
在.ssh/config 配置文件中加上连接配置即可

```
HOST sshname
    HostName hostname
    user root
    IdentityFile ~/.ssh/keyname
```

之后就可以用 ssh sshname 登录了