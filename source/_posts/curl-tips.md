---
title: curl备忘录
date: 2025-03-18 23:33:11
tags:
  - curl
  - cheat_sheet
---

# curl备忘录

## 一、curl是什么？
curl是一个基于命令行的网络工具，可以用来发送HTTP请求。

## 二、常用命令
1、发送GET请求
``` shell
curl www.baidu.com
```

2、输出请求各阶段耗时
``` shell
curl -o /dev/null -s -w "DNS解析: %{time_namelookup}s\n连接建立: %{time_connect}s\nSSL握手: %{time_appconnect}s\n服务器响应: %{time_starttransfer}s\n总时间: %{time_total}s\n" https://example.com

```

3、输出header
``` shell
curl -I www.baidu.com # 只输出header
curl -i www.baidu.com # 输出header和body
```
