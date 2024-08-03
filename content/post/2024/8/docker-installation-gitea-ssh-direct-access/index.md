---
title: 'Docker 安装 Gitea 之 SSH 直通'
slug: 'docker-installation-gitea-ssh-direct-access'
image: 'docker-installation-gitea-ssh-direct-access.webp'
date: 2024-08-04T07:02:00+08:00
description: ssh 直通是一种通过 ssh 协议访问 git 仓库的方式，不需要额外的 git 用户，也不需要配置 ssh key。
tags:
  - Gitea
categories:
  - practices
---

## 引言

- `Docker` 容器化的部署方式不仅可以磨平各种系统的差异，还可以隔绝宿主机环境，避免对宿主机造成影响。
- `Gitea` 是一个比 Gitlab 更加轻量级的 Git 仓库管理系统，它提供了一套完整的 Git 仓库管理功能，包括代码托管、问题跟踪、Wiki、CI/CD 等功能。

## 安装

[使用 Docker 安装 | Gitea Documentation](https://docs.gitea.com/zh-cn/installation/install-with-docker)

首先官方的安装文档就已经非常详尽，但我还是踩坑了。

## 踩坑

1. 记得重建容器，因为修改了 `docker-compose.yml` ，需要重新启动容器。

2. 在设置 authorized_keys 时需要注意权限。我是用 root 用户创建的，导致在用户在添加 SSH 公钥的时候出现了 `AddPublicKey, addKey: permission denied` 异常。

执行以下命令解决：

```bash
chown -R git:git /home/git/.ssh
```

> 参考资料  
> [Permission denied (publickey) · Issue #21861 · go-gitea/gitea](https://github.com/go-gitea/gitea/issues/21861#issuecomment-1343785295)
