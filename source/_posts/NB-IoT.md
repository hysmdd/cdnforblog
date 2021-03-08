---
title: NB-IoT技术架构
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 通信技术
date: 2020-03-07 15:00:00
comments: true
tags:  
	- 通信技术
	- 无线技术
	- 通信原理
---

NB-IoT技术学习笔记

<!-- more -->

## 5G的发展方向

```
高速率，高带宽： LTE、LTE-A

低速率、低成本、低功耗、广覆盖：物联网
```

## 频谱应用

```
主流的FDD频段都支持NB-IoT：900MHz、1800MHz、800MHz
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307141143.png)



## NB-IoT网络架构

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307141251.png)

### NB-IoT数据传输方案

    NB-IoT主要用于传送低速率的小数据包，从传输数据格式来看，可以传输三种数据类型：IP，Non-IP，SMS（短消息）。
    
    NB-IoT是从LTE系统演进而来，为提升小数据的传输效率，NB-loT系统支持两种优化的传输方案，包括控制面优化传输方案（简称CP方案）和用户面优化传输方案（简称UP方案）。


## 3GPP  5G  NR协议标准

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307142223.png)



## 5G频率范围

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307142712.png)



## 5GNR常见的帧结构配置

```
以u=1,子载波间隔为30KHz为例，单个时隙长度为0.5ms
```



## SS Block组成

```
一个SS block 包含PSS/SSS/PBCH,用于下行同步信号和广播信号的发送。

小区搜索是UE接入网络，为用户提供各种业务的基础
```



## 物理信号与天线端口

    上行链路的天线端口：
    天线端口0（起始号）用于PUSCH的DM-RS
    天线端口1000（起始号）用于SRS
    天线端口2000（起始号）用于PUCCH的DM-RS
    天线端口4000用于PRACH。
    
    下行链路的天线端口：
    天线端口1000（起始号）用于PDSCH的DM-RS
    天线端口2000（起始号）用于PDCCH的DM-RS
    天线端口3000（起始号）用于CSI-RS
    天线端口4000（起始号）用于SS/PBCH