---
title: "解决 Git Bash 中文乱码"
date: 2021-11-07T23:06:06+08:00
slug: "git-cn-code"
image: p1.png
---


## 1. git log 乱码
`git log` 出现乱码，直接更新到最新版本即可，打开 Git Bash 输入以下内容更新。  

```bash
git update-git-for-windows
```


## 2. git bash 中文输入异常  

git bash 输入中文之后删除的话会出现异常，如下  
![](p1.png)

解决办法如下，在 bash 中执行以下指令编辑 ~/.bashrc 文件
```bash
touch ~/.bashr
```
粘贴以下内容
```bash
export LC_ALL=zh_CN.UTF-8
```
按 `Esc` 键退出编辑模式，按 `:` 键盘进入指令模式，输入 `x` 回车，保存并退出。  

重启 git bash 即可正常输入中文。
