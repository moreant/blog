---
title: '解决控制台输出 unsafe-eval 错误'
date: 2022-11-14T23:48:22+08:00
slug: 'unsafe-eval'
image: error_console.jpg
categories:
  - dev
tags:
  - Nginx
---

## 前情提要

之前测试环境一直使用的都是用 vue-cli 的 `production` 模式构建的，由于需要区分测试和正式环境的配置文件，测试环境就改用 `test` 模式来构建了。随后就出现了这个问题。

## 特征描述

1. 首屏加载无限 Loading - 推测是有 js 文件没能正常加载
2. 控制台报错  
   `Uncaught EvalError: Refused to evaluate a string as JavaScript because 'unsafe-eval' is not an allowed source of script in the following Content Security Policy directive: "default-src 'self' http: https: ws: wss: data: blob: 'unsafe-inline'".`

## 解决思路

看报错描述貌似是某个安全策略导致的。  
搜索带有单引号的关键字，确定是因为响应头（Response Header）中的 `Content-Security-Policy` 安全规则导致浏览器根据规则阻止了 JS 文件的加载。

这个安全规则可以通过 HTML 中的 meta 标签携带，当然更多的是通过 Nginx 统一设置的。测试环境的 Nginx 配置是在 `nginxconfig.io` 这个网站生成的，里面的 `security.conf` 里有：

`default-src 'self' http: https: ws: wss: data: blob: 'unsafe-inline'; frame-ancestors 'self';`

里面没有配置 `'unsafe-eval'` 指令值，所以 JS 函数无法正常加载，导致首屏无限 Loading。

## 解决方案

因为这个是测试环境出现的问题，直接注释掉这个响应头配置就行了。  
正式环境的构建文件里没有使用到 eval 函数，自然不会被这个规则阻止。

## 相关参考

> [Content Security Policy 入门教程 - 阮一峰的网络日志](https://www.ruanyifeng.com/blog/2016/09/csp.html)  
> [NGINXConfig | DigitalOcean](https://www.digitalocean.com/community/tools/nginx?global.app.lang=zhCN)  
> [Content-Security-Policy - HTTP | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Security-Policy)
