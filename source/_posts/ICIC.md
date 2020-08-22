---
title: ICIC
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 通信技术
date: 2020-05-12 14:11:21
music:
	type: song
	id: 1436709403
comments: true
tags:  
	- 通信技术
	- 无线技术
	- 通信原理
---

小区间干扰协调（Inter Cell Interference Coordination，ICIC）是用来解决同频组网时，小区间干扰的技术。

<!-- more -->

## 干扰抑制的3种类型

- 干扰随机化：加扰、交织、跳频
- 干扰消除：波束赋形、IRC
- 干扰协调：ICIC
  - 资源调度方式
  - 资源调度周期

<br>

## 小区间干扰抑制技术

{% note success, 小区间的干扰主要来自于同频组网带来的同频干扰。 %}

<br>

### 小区间干扰抑制技术

- 干扰随机化技术
- 干扰消除技术
- 干扰协调技术（ICIC）

### 小区间干扰随机化技术：加扰

- LTE系统充分使用序列的随机化避免小区间干扰
- 一般情况下，加扰在信道编码之后、数据调制之前进行，即比特级的加扰。

### 小区间干扰随机化技术：跳频

- 目前LTE上下行都支持跳频传输，通过跳频传输可以随机化小区间的干扰。
- 除了PBCH之外，其他下行物理控制信道的资源映射均与小区id有关
- PDSCH、PUSCH以及PUCCH采用子帧内跳频传输
- PUSCH可以采用子帧间的跳频传输

### 小区间干扰消除技术：发射端波束赋形

- 提高期望用户的信号强度
- 降低信号对其他用户的干扰
- 已经知道被干扰用户的方位，可以主动降低对该方向辐射能量

### 小区间干扰消除技术：IRC

{% note success, 接收端利用多根天线对接收信号进行加权，抑制强干扰，称为IRC。 %}

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200512134430.png)

### 小区间干扰协调：ICIC

- 是一种考虑多个小区中资源使用和负载等情况而进行的多小区无线资源管理方案。
- 基本思想：通过管理无线资源使得小区间干扰得到控制。
- 限制的无线资源：
  - 时频资源
  - 一定时频资源上的功率资源
- 是目前研究的一项热门技术，可以应用于各种宽带的业务。

<br>

### 小区间干扰协调ICIC的实现方式

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200512135150.png)

<br>

<hr>

- 静态ICIC：对无线资源的使用重新配置的时间以天为单位。几乎不需要基站之间交互信息。
- 半静态ICIC：对无线资源的使用重新配置的时间以秒为单位。基站之间信息传递的频率类似。
- 动态ICIC：对无线资源的使用重新配置的时间以10ms或百毫秒为单位，基站之间信息传递的频率类似。
- 协调调度：对无线资源的使用重新配置的时间以TTI为单位，由于x2接口的时延限制，在基站间无法实时传递信息，协调调度在LTE-advanced阶段实现。

<br>

### ICIC方案对应关系图

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200512140530.png)

### ICIC解决方案-基于SFR半静态ICIC

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200512140648.png)

