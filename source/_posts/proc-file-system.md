---
title: /proc文件系统详解
date: 2023-04-26 00:19:31
tags:
  - linux
    proc

---

在Linux下有一个神奇的文件系统：/proc，通过它可以查看内核运行状态以及控制内核的执行逻辑，许多好用的命令都是依赖它来实现的，例如：pmap(/proc/pid/smap)、netstat等。  

但是它包含的东西太多了，刚开始可能会一头雾水，完全不知道该怎么使用它，所以这里就对它进行一个整理总结。

# 一、内存相关

### 1、/proc/sys/vm/drop_caches

可以通过修改该文件的值控制内核对于cache的处理逻辑，可选值有三个，各自的含义如下：

```
1: free pagecache
2: free dentries and inodes
3: free pagecache dentries and inodes

可以通过以下命令来修改其值：echo 1 > /proc/sys/vm/drop_caches
由于执行改造会导致脏数据丢失，因此建议修改该值之前先执行sync命令，将内存中的脏页写入disk，避免数据丢失
```

### 2、

# 二、网络相关

### 1、/proc/sys/net/ipv4/ip_forward

该文件的值控制当前机器是否支持包转发，所有路由器内核都会开启该选项，如果想要把一个Linux机器改为支持转发功能，就需要开启该参数。

### 2、



