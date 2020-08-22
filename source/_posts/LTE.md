---
title: LTE系统概述
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 通信技术
date: 2020-03-07 12:25:00
music:
  type: song  
  id: 531295576
comments: true
tags:  
	- 通信技术
	- 无线技术
	- 通信原理
---

4G系统概述学习笔记

<!-- more -->

## LTE网络架构

**LTE通过<red>大容量</red>、<red>快速响应</red>、<red>高速率</red>和<red>更好的Qos</red>提升用户体验。**



![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307120439.png)

```
E-UTRAN中只有一种网元—eNode B

全IP化

演进分组核心网------EPC

媒体面控制面分离

演进分组系统—EPS

与传统网络互通
```

```
UE与eNode B之间的接口是Uu接口
eNode B与MME之间的接口是S1-MME接口
eNode B与S-GW之间的接口是S1-U
eNode B与eNode B之间的接口是X2
MME与HSS之间的接口是S6a
MME与S-GW之间的接口是S11
S-GW与P-GW之间的接口是S5/S8
PCRF与P-GW之间的接口是Gx
```

```
Uu口也叫X1口，X2口相当于3G的Iur接口。
```



## LTE网元功能

### eNodeB

```
（Mobility Management Entity,移动管理实体）无线资源管理，IP头压缩和用户数据流加密，UE附着时的MME选择，用户面数据向S-GW的路由，寻呼消息和广播信息的调度和发送，移动性测量和测量报告的配置。
```

### MME

```
（Mobility Management Entity,移动管理实体）MME为控制面功能实体，临时存缝用户数据的服务器，负责管理和存储UE相关信息，比如UE用户标识、移动性管理状来用户安全参数，为用户分配临时标识。当UE驻扎在该跟踪区域或者该网络时负责对该用户进行鉴权，处理MME和UE之间的所有非接入层消息。
```

### SGW

```
（Serving Gateway,服务网关）SGW为用户面实体，负责用户面数据路由处理，终结处于空闲状态的UE（用户终端设备）的下行数据，管理和存储UE的承载信息，比如IP承载业务参数和网络内部路由信息。
```

### PGW

```
（PDN Gateway,分组数据网网关）PGW负责UE接入PDN的网关，分配用户IP地址，同时是3GPP和非3GPP接入系统的移动性锚点。用户在同一时刻能够接入多个PDN GW。
```

### HSS

```
（Home Subscriber Server,归属用户服务器）HSS存储并管理用户签约数据，包括用户鉴权信息、位置信息及路由信息。
```

### PCRF

```
（Policy and Charging Rule Functionality,策略和计费规则功能实体）PCRF功能实体主要根据业务信息和用户签约信息以及运营商的配置信息产生控制用户数据传递的QoS（Quality of Service，服务质量）规则以及计费规则。该功能实体也可以控制接入网中承载的建立和释放。
```

## LTE接口与协议

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307122645.png)

​	

## LTE主要网络标识

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307122830.png)

### PLMN  ID

```
PLMN ID是PLMN的全局唯一标识，由MCC+MNC两部分组成。
```

### IMSI

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307122929.png)

### IMEI

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307123006.png)

### MSISDN

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307123319.png)

### GUTI

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307123504.png)

### TAI

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307123610.png)

### ECGI

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307123642.png)

## LTE关键技术-多址技术

```
LTE系统下行多址方式为正交频分多址（OFDMA），上行为基于正交频分复用（OFDM）传输技术的单载波频分多址（SC-FDMA）。
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307132303.png)

### OFDMA特点

```
最大支持64  QAM

通过CP解决多径干扰

兼容MIMO
```

### SC-FDMA特点

```
最大支持64  QAM

单载波调制降低峰均比（PAPR）

FDMA可通过FFT实现
```

## LTE关键技术-MIMO

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307133013.png)

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307133428.png)

## LTE关键技术-多阶调制技术

```
LTE支持BPSK，QPSK，16QAM，64QAM，256QAM。

当前上行支持64QAM，下行支持256QAM。
```

## LTE关键技术- 链路自适应技术

### 速率控制

```
AMC：

- 时域AMC

- 频域AMC

- 空域AMC
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images20200307133936.png)

### 功率控制

```
功率控制可以很好的避免小区内用户间的干扰。
```

## LTE关键技术-干扰消除技术

### 功率控制

```
小区间功率控制：一种通过告知其它小区本小区loT信息，控制本小区loT的方法。

小区内功率控制：补偿路损和阴影衰落，节省终端的发射功率，尽量降低对其他小区的干扰，使得loT保持在一定的水平之下。
```

## LTE关键技术-载波聚合

```
载波聚合是指基站根据UE能力将2个或更多载波进行聚合

每一聚合的载波称为分量载波

协议设计最多支持5个的载波聚合在一起以支持更大的传输带宽（最大为100MHz)。
```

