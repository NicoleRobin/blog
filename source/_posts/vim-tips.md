---
title: vim-tips
date: 2023-04-10 00:57:25
tags:
    - vim
---

# vim使用技巧

## 移动操作
```
基础操作：hjkl
ctrl+e
:num: 跳转到指定行
```
参考文档：  
```
:h motion.txt
```

## 窗口操作
```
ctrl+w s: 水平拆分窗口
ctrl+w v: 垂直拆分窗口
:split filename
:vsplit filename
:close: 关闭当前窗口
:only: 关闭除当前窗口的其他所有窗口
```

## 缓冲区操作
```
:ls: 查看所有缓冲区列表
:bnext: 切换到下一个缓冲区
:bprev: 切换到上一个缓冲区
```

## 标签页操作
```
:tabedit filename: 新建标签页并打开指定文件的缓冲区，不跟文件名则打开一个新的标签页包含一个空缓冲区
:tabclose: 关闭当前标签页
:tabonly: 关闭除当前标签页的其他标签页
gt: 切换到下一个标签页
gT: 切换到上一个标签页
```

## 文件操作
```
:edit filename: 打开文件，需指定文件的路径，相对路径或绝对路径均可
:find filename: 通过文件名打开文件而不用指定确切路径
:E: 打开当前目录，它是命令:explore的缩写形式
:Sexplore: 水平拆分窗口并在新窗口中打开当前目录
:Vexplore: 垂直拆分窗口并在新窗口中打开当前目录

```
