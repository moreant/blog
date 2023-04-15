---
title: 'SSH 自动登录'
date: '2021-09-29T23:09:11+08:00'
slug: 'automatic-ssh-login-based-on-identityfile'
description: '只需要 ssh name 就登录了'
image: ssh.webp
tags:
  - Linux
categories:
  - practices
---

**注意，以下指令都是在 Git Bash 中的操作。**

## 切换到用户文件夹下的 .ssh 目录。

```bash
cd ~/.ssh
```

如果提示没有文件夹就创建一个
```bash
mkdir ~/.ssh
```

## 生成 ssh key

默认生成名为 `id_rsa.pub` 的 **公钥** 与 `id_rsa` 的 **私钥**，如果你先前已经生成过 key，可以忽略此步。
如果你不想覆盖默认的秘钥，可以加上 `-f keyname` 生成一个名为 `keyname` 的密钥对。

```bash
ssh-keygen [-f keyname]
```

## 把公钥文件拷贝到指定的服务器

请将 user 与 hostname 替换为你的用户名与服务器地址。
```bash
ssh-copy-id <user>@<hostname> [-i keyname]
```

## 配置服务器别名(可选)
拷贝到服务器后就能自动登录了，但是配置别名后可以直接输入别名登录主机，不需要再输入用户名与服务器地址了。

首先新建 config 文件。

```bash
touch ~/.ssh/config
```

文件内填入以下内容，注意缩进！

```ini
HOST <aliasname>
    HostName <hostname>
    ## 如果用户是 root，可以不指定
    user <myname>
    ## 如果使用的不是默认的key，需要指定 key 的路径
    [IdentityFile ~/.ssh/keyname]
```

之后就可以在 Git Bash 中用 `ssh aliasname` 登录了

> 参考资料：  
> https://segmentfault.com/q/1010000002445731
