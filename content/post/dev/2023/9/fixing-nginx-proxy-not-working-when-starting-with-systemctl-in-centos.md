---
title: '修复 CentOS 中使用 Systemctl 启动 Nginx 无法反代理的问题'
date: '2023-09-16T23:17:00+08:00'
slug: 'fixing-nginx-proxy-not-working-when-starting-with-systemctl-in-centos'
description: '通过 semange 添加反代端口解决'
tags:
  - Nginx
  - CentOS
categories:
  - dev
---

## 问题描述
最近几次在 CentOS 启动后 Nginx 并没有开机启动，于是我就想着使用 Systemctl 来启动 Nginx。但是启动后发现 Nginx 并没有反代理成功，访问后端接口会返回 502。

Google 了一波，发现是 `SELinux` 的配置阻止了 Nginx 代理后端端口，可以通过 `semanage` 添加需要反代的端口解决。

## 解决步骤
### 1. 安装 semanage

```bash
yum install policycoreutils-python
```

可以执行一下 `semanage` 看看是否安装成功，如果返回帮助信息说明安装成功。
```bash
semanage
```

### 2. 添加需要反代理的端口
首先检查一下需要反代理的端口是否已经添加到了 http_port_t 中，如果有说明不是这个问题，你可以尝试其他方法解决。
```bash
semanage port -l | grep http_port_t
```

如果没有，那么就需要添加了。9161 是我需要反代理的端口，你可以根据自己的情况修改。
```bash
semanage port -a -t http_port_t -p tcp 9161
```

执行完后再次检查一下是否添加成功。
```bash
semanage port -l | grep http_port_t
# http_port_t tcp 9161, 80, 81, 443, 488, 8008, 8009, 8443, 9000
```

### 3. 重载 Nginx
```bash
nginx -s reload
```

## 参考资料
> [linux - systemctl启动nginx没有加载nginx.conf配置文件？ - SegmentFault 思否](https://segmentfault.com/q/1010000004361013)  
> [\[Centos7\] 安裝 semanage (selinux工具程式) @新精讚](https://n.sfs.tw/content/index/11039)  
> [nginx - proxy_pass isn't working when SELinux is enabled, why? - Stack Overflow](https://stackoverflow.com/a/39737231)  
> [Modifying SELinux Settings for Full NGINX and NGINX Plus Functionality](https://www.nginx.com/blog/using-nginx-plus-with-selinux/#Issue-3:-NGINX-Cannot-Bind-to-Additional-Ports)  