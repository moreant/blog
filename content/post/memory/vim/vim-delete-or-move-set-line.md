---
title: 'vim 指令状态下删除或移动指定行'
date: 2022-11-13T16:45:20+08:00
slug: 'vim-delete-or-move-set-line'
description: '5,10d'
tags:
  - Vim
categories:
  - memory
---

以下内容皆为指令状态下的操作，即需要先输入 `:`

## 删除

删除第 5 行

```vim
5d
```

删除第 5 行至第 10 行

```vim
5,10d
```

删除当前行至第 10 行

```vim
.,10d
```

删除当前行至末尾行

```vim
.,$d
```

删除当前文件所有行

```vim
$d
```

## 移动

移动一行
```vim
5 v 20
```

移动多行
```vim
5,10 v 20
```

## 复制

复制一行
```vim
5 co 20
```

复制多行
```vim
5,10 co 20
```
