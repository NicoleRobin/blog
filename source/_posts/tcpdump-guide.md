---
title: tcpdump使用指南
date: 2023-01-08 00:09:58
tags: 
  - tcpdump
  - 使用指南
---

- [[使用指南]]
- ### 1、运行下面命令从所有网卡中捕获数据包：
- `tcpdump -i any`
- ### 2、从指定网卡中捕获数据包
- `tcpdum -i eth0`
- ### 3、指定网卡、IP地址、写入文件
- `tcpdump -i eth0 host 10.19.150.242 -w datadump.cap`
- ### 4、指定网卡、源IP及目的IP、写入文件
- `tcpdump -i eth0 src host 10.10.100.19 and dst host 10.10.100.153 -w datadump.cap`
- ### 5、指定网卡、源IP或目的IP、写入文件
- `tcpdump -i eth0 src host 10.10.100.19 or dst host 10.10.100.153 -w datadump.cap`
- ### 6、指定网卡、tcp端口及源IP及目的IP、写入文件
- `tcpdump -i eth0 tcp port 52312 and src host 10.10.100.19 and dst host 10.10.100.153 -w datadump.cap`
- ### 7、指定网卡、排除IP、写入文件
- `tcpdump -i eth0 host !10.10.100.19 and !10.10.100.153 -w datadump.cap`
- ### 8、只抓取syn包
- `tcpdump -i eth0 tcp[13] == 2 -w datadump.cap`
- 上面命令这么写的原因是tcp头包含20个字节的固定长度的数据，其中控制位位于第13个字节（从0开始计算），而如果控制位包含SYN的话，tcp头的第13个字节的值就是2，即tcp[13] == 2。
- ### 9、
