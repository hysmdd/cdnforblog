---
title: LTE信道及协议栈分析
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 通信技术
date: 2020-03-07 13:00:00
music:
  type: song  
  id: 477754663
comments: true
tags:  
	- 通信技术
	- 无线技术
	- 通信原理
---

LTE信道及协议栈分析学习笔记

<!-- more -->

## 无线帧结构-FDD制式

```
1个无线帧Tf=207200Ts=10ms

每个10ms无线帧被分为10个子帧

每个子帧包含两个时隙，每时隙长0.5ms

Ts=1/（15000*2048)是基本时间单元

任何一个子帧即可以作为上行，也可以作为下行
```



## 无线帧结构-TDD制式

```
1个无线帧Tf=307200Ts=10ms

每个10ms无线帧包括2个长度为5ms的半帧，每个半帧由4个数据子帧和1个特殊子帧组成

特殊子帧包括3个特殊时隙：DWPTS，GP和UpPTS，总长度为1ms

支持5ms和10ms上下行切换点

子帧0、5和DWPTS总是用于下行发送
```



## LTE信道及协议栈分析(物理层)

### RE

```
最小的资源单位，时域上为1个符号，频域上为1个子载波用（k,l）标记
```

### RB

```
业务信道的资源单位，时域上为1个时隙，频域上为12个子载波
```

## PCM的主要步骤

```
抽样、量化、编码
```

