---
title: 'SSH 自动登录'
date: '2021-09-29T23:09:11+08:00'
slug: 'automatic-ssh-login-based-on-identityfile'
description: '基于 IdentityFile 的 SSH 自动登录'
image: ssh.webp
tags:
  - Linux
categories:
  - practices
---

**注意，以下指令只能确保在 Git Bash 中可以执行。**

## 生成 ssh key

切换到默认的 ssh 配置目录
```bash
cd ~/.ssh
```

如果提示没有文件夹就创建一个
```bash
mkdir ~/.ssh
```

默认生成名为 `id_rsa.pub` 的 **公钥** 与 `id_rsa` 的 **私钥**，如果你先前已经生成过 key，可以忽略此步。
如果想生成另一个秘钥，可以加上 `-f keyname` 生成一个名为 `keyname` 的密钥对。

目前 ed25519 类型的密钥已被广泛使用，现在更推荐生成 ed25519 格式的密钥。长度更短，性能更强。加上 `-t ed25519` 即可生成 ed25519 格式的密钥对。  

```bash
ssh-keygen [-f keyname] [-t ed25519]
```

## 拷贝公钥到服务器

这是一个将 id_ed25519.pub 拷贝到服务器的例子。如果你使用的是默认的密钥，可以省略 `-i id_ed25519.pub`。如果你使用的是其他密钥，需要将 `id_ed25519.pub` 替换为你的密钥名。
```bash
ssh-copy-id -i id_ed25519.pub user@hostname  
```

## 配置服务器别名(可选)
拷贝到服务器后就能自动登录了，但是配置别名后可以直接输入别名登录主机，不需要再输入用户名与服务器地址了。
例如

```bash
ssh my-server
```

首先新建 config 文件。

```bash
touch ~/.ssh/config
```

文件内填入以下内容，注意缩进！

```ini
HOST my-server
    HostName 111.111.111.111
    ## 默认是 root，如果不是 root，需要指定用户名
    user user
    ## 如果使用的不是默认的key，需要指定 key 的路径，默认会寻找 id_rsa 和 id_ed25519
    [IdentityFile ~/.ssh/keyname]
```

之后就可以在 Git Bash 中用 `ssh my-server` 登录了

> 参考资料：  
> https://segmentfault.com/q/1010000002445731
