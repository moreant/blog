---
title: 'Vim 强制保存'
date: 2023-02-20T00:00:00+08:00
slug: 'vim-force-save'
image: vim-force-save.webp
description: 'w !sudo tee %'
tags:
  - Vim
categories:
  - memory
---

```bash
w !sudo tee %
```

w： 表示保存文件

！： 表示执行外部命令

tee： linux 命令，这个有点复杂，可以查看 linux 命令帮助

%： 在执行外部命令时，%会扩展成当前文件名；这个%区别于替换时的%，替换时%的意义是代表整个文件，而不是文件名

上述方式非常完美的解决了不能保存只读文件的问题，但毕竟命令还是有些长，为了避免每次输入一长串的命令，可以将它映射为一个简单的命令加到 .vimrc 中：

```bash
" Allow saving of files as sudo when I forgot to start vim using sudo.
 cmap w!! w !sudo tee > /dev/null %
```

这样，简单的运行:w!!即可。命令后半部分> /dev/null 作用为显式的丢掉标准输出的内容。

> 来源  
> [Vim 强制保存只读文件的方法](http://kuanghy.github.io/2015/12/30/sudo-vim)
