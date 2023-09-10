---
title: '一键安装 Docker'
date: 2023-03-03T00:02:22+08:00
slug: 'install-docker'
image: install-docker.webp
categories:
  - practices
tags:
  - Linux
  - Docker
---

## 一键安装

使用 get-docker 脚本可以快速的安装 Docker ，无论是 x86 还是 ARM 都能支持。

```bash
# 获取脚本
curl -fsSL https://get.docker.com -o get-docker.sh
# 执行
sudo sh get-docker.sh
# Executing docker install script, commit: 7cae5f8b0decc17d6571f9f52eb840fbc13b2737
```

## 添加用户组

如果你是非 root 用户，执行 docker 指令时都需要加上 sudo。可以将当前用户添加进 docker 用户组来避免每次都要输入 sudo。

```bash
# 将当前用户添加进 docker 用户组
sudo usermod -aG docker ${USER}
# 切换当前用户，刷新用户组
su - ${USER}
# 输出当前用户组，预期能看到 docker
groups
```

可以使用 systemctl 指令查看 Docker 的运行状态，看到绿色的 active (running) 说明运行正常。

```bash
systemctl status docker
```

接下来运行 Hello Docker 来测试一下，欢迎进入 Docker 的世界！

```bash
docker run hello-world
# Hello from Docker!
```

> 参考资料：  
> [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)  
> [Getting started with Docker for Arm on Linux | Docker](https://www.docker.com/blog/getting-started-with-docker-for-arm-on-linux/)
