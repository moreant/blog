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


## 更新
### 2025-03-25:
1. 可以使用这个脚本检查机器是否支持 Docker。

```bash
curl -sSL https://github.com/moby/moby/raw/master/contrib/check-config.sh | bash
```

### 2024-09-22:
1. 清华源有时候会同步失败，所以顺便提供一下手动安装的步骤: 

### 2024-07-22:  
1. 使用镜像源下载安装脚本。
2. 使用清华源替代 install 脚本中的两个镜像源，解决安装速度都拉胯的问题。

## 一键安装

使用 get-docker 脚本可以快速的安装 Docker ，无论是 x86 还是 ARM 都能支持。

```bash
# 使用清华源
export DOWNLOAD_URL="https://mirrors.tuna.tsinghua.edu.cn/docker-ce"
# 获取脚本
curl -fsSL https://mirror.ghproxy.com/https://mirror.ghproxy.com/https://raw.githubusercontent.com/docker/docker-install/master/install.sh -o install-docker.sh
# 执行
sudo sh install-docker.sh
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

## 手动安装
删除旧的：
```bash
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do apt-get remove -y $pkg; done
```

安装必要的依赖：
```bash
apt-get update
apt-get install ca-certificates curl gnupg
```

安装 gpg key 和源，如果是非 ubunt 系统记得改名字：
```bash
install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
```
安装 Docker 及其插件
```bash
apt-get update
apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

> 参考资料：  
> [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)  
> [Getting started with Docker for Arm on Linux | Docker](https://www.docker.com/blog/getting-started-with-docker-for-arm-on-linux/)  
> [https://get.docker.com/](https://get.docker.com/)  
> [docker-ce | 镜像站使用帮助 | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/help/docker-ce/)  
> [工具分享：检测内核配置是否支持Docker等容器 - Core-3568J - Firefly开源社区工具分享：检测内核配置是否支持Docker等容器](https://dev.t-firefly.com/thread-115083-1-1.html)