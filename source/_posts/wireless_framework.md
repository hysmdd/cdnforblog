---
title: 5G无线网络架构演进
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 通信技术
date: 2020-04-09 11:25:00
comments: true
tags:  
	- 通信技术
	- 无线技术
	- 通信原理
---

了解移动通信网络发展

熟悉接入网架构演进策略

熟悉5G网元接口功能

掌握5G组网特性与应用

<!-- more -->

##  移动通信发展历程

### 移动通信标准发展历程

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200407095820.png)

### RAN网络架构变迁

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408132416.png)

### 3G-4G的演进

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408132644.png)

### 4G-5G的演进

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408132814.png)

## 5G接入网架构演进

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408133503.png)

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408133546.png)

```
演进G的gNB，也可以是LTE  eNB升级后的ng-eNB。采用gNB与5GC组网时，对应架构Option  2。将LTE  eNB需升级到ng-eNB后连接到5G核心网，对应架构Option  5。

对于拥有较丰富、优质的Sub-6GHz频谱资源作为覆盖，同时又有足够的高频频谱资源来增强容量的运营商，选择Option  2独立组网是一个比较好的选择。
```



![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408134106.png)



```
4G基站（eNB）和5G基站（gNB）公用4G核心网（EPC），LTE  eNB和5G gNB用户面可以直接连接到EPC，控制面则仅经由LTE eNB连接到EPC。用户面可以分别经由LTE eNB、EPC或者gNB进行分流。优势在于不需要新增5G核心网，利用运营商现有4G网络基础设施快速部署5G，抢占覆盖和热点。但是5G信令全走4G通道，有4G核心网信令过载风险，因此该阶段主要解决初期的5G覆盖。
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408134927.png)

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408135117.png)

### 组网部署方式比较和运营商选择

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408135306.png)

### 5G接入网方案部署

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408135831.png)

### CU-DU划分

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408140119.png)

### CU-DU方案策略比较

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408140304.png)

### 5G基站部署

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408140458.png)

### 5G传输部署

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408140706.png)

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408140804.png)



## 5G网元与接口功能

### 5G接入网架构概述

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408182932.png)

### 4G/5G共核心网网元与接口

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408183138.png)

### 网元功能-UPF

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408183404.png)

### 网元功能-SMF

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408183500.png)

### 网元功能-AMF

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408183558.png)

### 网元功能-gNB/en-gNB

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408183644.png)

### 接口概述-NG

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408183824.png)

### NG接口协议-总览

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408184052.png)

### 接口NG-C协议与功能

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408184414.png)

### 接口NG-U协议与功能

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408184555.png)

### 接口概述-Xn

```
接口定义：ng-eNB/gNB与ng-eNB/gNB之间的接口
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408184827.png)

### Xn接口协议-总览

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408184915.png)

### 接口Xn-U协议与功能

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408185046.png)

### 接口概述-F1

```
接口定义：gNB-CU与gNB-DU之间的接口，包括F1-C和F1-U。
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408185232.png)

### F1接口协议-总览

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408185350.png)

### 接口F1-C协议与功能

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408190004.png)

### 接口F1-U协议与功能

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408190403.png)

### 接口概述-E1

```
接口定义：gNB-CU-CP与gNB-CU-UP之间的接口，目前只有E1-C接口。
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408190658.png)

### 接口E1-C协议与功能

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408191240.png)

### 接口概述-Radio  UU

```
接口定义：UE与gNB及网络之间的接口。
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408191547.png)

### Radio  UU口控制面协议栈

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408191759.png)

## 5G无线组网与应用

### C-RAN概念演进

```
C-RAN的概念：“Centralization，Collaborative，Cloud，Clean”无线接入云网络架构。
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408205638.png)

### C-RAN推进目标

根据工作内容的独立性，可分为5个具体的工作组：

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408223223.png)

### C-RAN部署的三种方式

根据不同的业务和部署场景，C-RAN的架构总体可以分为CU和DU两级，但是实际部署可以出现CU、DU和RRU分离的三级配置，也可以出现RRU直接连入中心节点。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200408223602.png)

### C-RAN场景部署-eMBB

Case 1：基于多连接的部署用于网络容量和覆盖的提升。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200409132236.png)

```
典型的部署场景包括：
·一个宏站覆盖一个宏小区，一个微站覆盖一个微小区，一个宏站可以连接一个或多个微站。宏微小区可以同频或者异频。
·对于宏基站，DU和AAU通常分离，但对于微站，DU和AAU可以分离也可以集成在一起；
·对于宏站，CU、DU可以部署在一起，对于微站，CU和DU的连接一般需要专门的fronthaul连接，根据具体的技术应用对fronthaul的时延有不同的需求，如果无线承载需要合并，则时延要求一般小于5ms，否则需求可以放松一些。
```

Case  2：基于基站协同管理的服务与小区间干扰协调和高密度业务的需求

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200409132058.png)

```
相关的部署需求包括：
·所有AAU需要和DU池通过直接光纤或高速传输网络连接，时延要求一般在微秒量级。
·DU池支持的小区数目可以达到数十至数百个。
·CU和DU的连接一般通过传输网络，时延要求则没有RU和DU的fronthaul连接严格。
```

Case  3：基于时延差异性的部署优化

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200409132501.png)

```
·高实时大带宽的业务如视频和虚拟现实业务：为了保证高效的时延控制，需要高速传输网络或光纤直连AAU，数据统一传输到中心机房进行处理，减少中间的流程，同时DU和CU则可以部署在同一位置，网络实体则合而为一。
·低实时语音等一般业务：在这种场景下，带宽和实时性要求不高，实时功能DU可以部署在站点侧，多个DU通过fronthaul连接到一个CU，非实时功能CU可以部署在中心机房。
```

### C-RAN场景部署-mMTC

Case：垂直行业和机器通信需求-物联网的集中化管控

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200409132728.png)

```
物联网的集中化管控：可以让多个DU或者AAU连接到一个CU，由CU进行区域物联网的集中管控。由于物联网业务实时性要求不高，可以将CU和核心网进行共平台部署，减少无线网和核心网的信令的交互，减少机房的数量。
```

### C-RAN场景部署-uRLLC

Case：低时延高可靠需求-车联网

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200409132939.png)

```
·基于高实时通信的自动驾驶：将RAN的实时处理DU和非实时处理功能单元CU部署在更加靠近用户的位置，并配置相应的服务器和业务网关，进而满足特定的时延和可靠性需求。
·基于高可靠需求的公共安全应急通信：在涉及到公共安全的通信业务时，通常需要高可靠性，一般采取广播方式，多小区传送相同信息，因此多个DU需要连接相同的CU做重复的数据传输。
·高移动性的业务支持：当UE处于高速移动时，比如在无人机控制场景，为了减少切换，可以让多个DU共享一个逻辑小区，CU对这个逻辑小区做集中控制，在DU间移动无需切换。
```

### C-RAN场景部署总结

基于网络切片的三大场景部署

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200409133235.png)

```
从功能上,实时处理单元和非实时处理单元需要各有分工
从实体上,RRU冋以部分和DU耦合,DU也可以和CU耦合,实现部分功能的转移
从部署上,RRU、DU、CU的地理位置可以灵活部署
从对业务的支持上,必须种统的架构去满足eMBB,MTC,URL等不同的业务特点
```

