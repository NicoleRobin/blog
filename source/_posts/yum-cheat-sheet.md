---
title: yum_cheat_sheet
date: 2024-11-02 19:29:41
tags:
    - yum
    - cheat_sheet
---

# yum备忘录
## 一、yum是什么？
yum是一个基于rpm包的包管理器，主要红帽系列系统在使用。
## 二、常用命令
1、查看所有包仓库列表  
```
yum repolist
```
2、安装包仓库列表  
```
安装MySQL官方仓库
rpm -ivh mysql80-community-release-el7-1.noarch.rpm
```