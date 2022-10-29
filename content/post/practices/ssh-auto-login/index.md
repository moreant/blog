---
title: 'ssh 自动登录（使用 IdentityFile）'
date: '2021-09-29T23:09:11+08:00'
slug: 'ssh-auto-login'
description: '只需要 ssh name 就登录了'
image: ssh.webp
tags:
  - linux
categories:
  - practices
---

**以下指令都是在 Git Bash 中的操作。**

## 切换到用户文件夹下的 .ssh 目录。

```bash
cd ~/.ssh
```

如果没有就使用指令 `mkdir ~/.ssh` 新建一个

## 生成 ssh key。

如果你已经生成过 key，可以忽略此步。这将生成名为 `id_rsa.pub` 的 **公钥** 和 `id_rsa` 的 **私钥**。

```bash
ssh-keygen
```

可以加上 `-f keyname` 生成一个名为 `keyname` 的 key

## 把公钥文件拷贝到指定的服务器

```bash
ssh-copy-id root@hostname
```

可以加上 `-i keyname` 指定拷贝到服务器的密钥

## 配置服务器别名

这个步骤是可选的，可以省略输入用户名和主机名。  
新建 config 文件。

```bash  
touch ~/.ssh/config  
```  

文件内填入以下内容，注意缩进！
```ini
HOST sshname
    HostName hostname
    ## 如果用户是 root，可以不指定
    user myname 
    ## 如果使用的不是默认的key，需要指定 key 的路径
    IdentityFile ~/.ssh/keyname
```

之后就可以在 Git Bash 中用 `ssh sshname` 登录了

> 参考资料：  
> https://segmentfault.com/q/1010000002445731
