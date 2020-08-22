---
title: MIMO
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 通信技术
date: 2020-05-11 21:21:21
music:
	type: song
	id: 1433434738
comments: true
mathjax: true
tags:  
	- 通信技术
	- 无线技术
	- 通信原理
---

多进多出（MIMO）是为极大地提高信道容量，在发送端和接收端都使用多根天线，在收发之间构成多个信道的天线系统。MIMO系统的一个明显特点就是具有极高的频谱利用效率，在对现有频谱资源充分利用的基础上通过利用空间资源来获取可靠性与有效性两方面增益，其代价是增加了发送端与接收端的处理复杂度。大规模MIMO技术采用大量天线来服务数量相对较少的用户，可以有效提高频谱效率。

<!-- more -->

## MIMO的定义

{%  folding  Multiple  Input  Multiple  Output，多输入多输出。 %}

{% note success, 在多个天线上分别发送多个数据流 %}

{% note success, 利用多径衰落，在不增加带宽和天线发射功率的情况下，提高信道容量及频谱利用率，或提高数据的传输质量。 %}

{%  endfolding %}



## MIMO的优点

<red>**MIMO多种模式带来多种增益。**</red>

- 分集增益
- 波束赋形增益
- 空间复用增益

<red>**频谱效率**</red>

要求TD-LTE的下行频率速率达到5bps/Hz（Rel-10为30bps/Hz），上行频谱速率达到2.5bps/Hz（Rel-10为15bps/Hz）

<hr>

{% note success, MIMO天线收发分集：提高通信质量。 %}

{% note success, 发射分集技术提高系统下行链路性能。 %}

![开环模式中的STTD分集](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200511140050.png)

<hr>

{% note success, MIMO天线空间复用：提高系统容量  %}

MU-MIMO：基站将占用相同时频资源的多个数据流发送给不同用户

下行同时支持SU-MIMO和MU-MIMO

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200511154807.png)

<hr>

{% note success, MIMO天线波束赋形：增强抗干扰能力 %}

传统的波束赋形：

- 小间距的天线阵列，使用较多天线单元
- 提高峰值速率，小区覆盖，降低小区间的干扰

<hr>

## LTE创新技术：双流波束赋形

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200511211824.png)

<hr>

## MIMO优点总结

发送分集：提高可靠性，不能提升数据速率

波束赋形：降低干扰，能提升数据速率

空分复用：多个数据流传输，可提升数据速率

<hr>

## TD-LTE中MIMO的应用（PDSCH 传输方案）

| 传输模式 | PDSCH传输方案  | 优点                                 | 典型应用方案               |
| :------: | :------------- | ------------------------------------ | -------------------------- |
|   TM1    | 单天线传输模式 | 产生的CRS开销小                      | 各类场景                   |
|   TM2    | 发送分集       | 提高链路传输质量，提高小区覆盖半径   | 作为其他MIMO模式的回退模式 |
|   TM3    | 开环空间复用   | 提高小区平均频谱效率和峰值速率       | 高速移动场景               |
|   TM4    | 闭环空间复用   | 提高小区平均频谱效率和峰值速率       | 低速移动场景               |
|   TM5    | 多用户MIMO     | 提高小区平均频谱效率和峰值速率       | 密集城区                   |
|   TM6    | Rank=1的预编码 | 提高小区的覆盖                       | 仅支持rank=1的传输         |
|   TM7    | 单流波束赋形   | 提高链路传输质量，提高小区覆盖半径   | 郊区、大范围覆盖场景       |
|   TM8    | 双流波束赋形   | 提高小区覆盖，提升小区中心用户吞吐量 | 小区中心吞吐量需求大的场景 |

<hr>

## TM1：单天线端口传输

- 最简单的传输方案
- PDSCH使用单天线端口传输时，根据Port0上的CRS进行解调。

{% note success, Port0上的小区专用参考信号的标识是R0。%}

<hr>

## TM2：发送分集

- 用于增强小区覆盖。
- 作为TM3/4/5/6/7的回退模式
- LTE中的实现方式SFBC+FSTD。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200511191836.png)

<hr>

## TM3：开环空间复用

- 一种大延迟（CDD）空间复用，接收端不需给发射端反馈预编码矩阵信息。
- 用于提高小区平均频谱效率和峰值速率。
- 适用于高速移动场景。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200511192143.png)

<hr>

## TM4：闭环空间复用

- 发送端需要给接收端反馈预编码矩阵信息。
- 用于提高小区平均频谱效率和峰值速率。
- 适用于低速移动场景。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200511192325.png)

<hr>

## TM5：多用户MIMO

- 只支持每个用户单层的传输，而且最大支持两层。
- 用于提高小区平均频谱效率和峰值速率。

<hr>

## TM6：闭环RANK=1的预编码

- 用于增强小区覆盖。
- 尽可能减小承载相关的控制信令。
- 仅支持rank=1的传输。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200511192647.png)

<hr>

## TM7：单流波束赋形

- PDSCH是依据port5上DRS进行解调的。
- 用于提高小区边缘用户的覆盖。
- 单流波束赋形是基于专用导频的非码本波束赋形。
- 主要用于TD-LTE系统。

<hr>

## TM8：双流波束赋形

- 双流波束赋形将波束赋形技术与空间复用技术相结合。
- 既提高小区边缘用户的覆盖，也可以提升小区中心用户的吞吐量。
- 双流波束赋形是基于专用导频的非码本波束赋形。
- 双流波束赋形是TD-LTE  Rel-9中的增强型技术。

<hr>

## 终端LTE多天线

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200511205924.png)

