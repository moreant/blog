---
title: 'Docker Hub 加速镜像'
date: '2023-10-28T15:42:00+08:00'
slug: 'docker-mirrors'
description: '使用镜像是每个中国程序员不得不学会的技巧'
image: docker-mirrors.webp
tags:
  - Docker
  - mirrors
categories:
  - memory
---

## 1. 配置镜像地址

不推荐阿里云的，因为阿里云的镜像不是实时同步的，有时候会出现 latest tag 与官方源的 latest 差了几个月的情况。其他的镜像源可以在资料参考中找到。

直接执行下面的命令即可。

```bash
sudo tee /etc/docker/daemon.json <<-'EOF'
{
    "registry-mirrors": [
        "https://docker.m.daocloud.io"
    ]
}
EOF
```

## 2. 刷新配置

```bash
sudo systemctl daemon-reload
```

## 3. 刷新配置

重启 Docker

```bash
sudo systemctl restart docker
```

## 参考资料

> [国内的 Docker Hub 镜像加速器，由国内教育机构与各大云服务商提供的镜像加速服务 | Dockerized 实践](https://gist.github.com/y0ngb1n/7e8f16af3242c7815e7ca2f0833d3ea6)
