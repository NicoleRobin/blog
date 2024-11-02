---
title: docker_cheat_sheet
date: 2024-11-02 20:53:34
tags:
    - docker
    - cheat_sheet
---

# docker备忘录

## 一、docker是什么？
docker是容器虚拟化的方案。

## 二、安装docker
### 2.1、在centos上安装docker
```

sudo yum install -y yum-utils

添加docker源
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

安装
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

启动服务
sudo systemctl start docker

验证
sudo docker run hello-world
```
