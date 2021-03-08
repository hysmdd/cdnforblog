---
title: OFDMA
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 通信技术
date: 2020-04-25 17:13:00
comments: true
mathjax: true
tags:  
	- 通信技术
	- 无线技术
	- 通信原理
---

TD-LTE核心技术

频分多址技术之OFDMA/SC-FDMA

<!-- more -->

## OFDMA的优点

- 时域上抵抗多径衰落
- 频域上抵抗频率选择性衰落，简化接收机的信道均衡操作

<br>

{% note success, 码元的长度越长，符号间的干扰（ISI）就越低。%}

{% note success, 码元的长度越长，码元速率就越低。 %}

<br>

## OFDM循环前缀CP

CP能够克服时延拓展，最大限度消除符号间干扰（ISI）。CP越长，能够抵抗的多径时延越长，但相应的，系统开销也越大。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200425155542.png)

{% note success, I指的是OFDM符号的编码 %}

<br>

{% note success, LTE系统中最小的时间单位叫作基本的时间单位。%}

{% note success, 一个子帧可以划分成14个OFDM符号，14个OFDM符号可以划分成2个时隙，1个时隙就是7个OFDM符号 %}

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200425161403.png)

<br>

CP使一个符号周期内因多径产生的波形为完整的正弦波，因此不同子载波对应的时域信号与其多径积分总为0，消除载波间干扰（ICI）。

<br>

## OFDM定义

{% note success, 子载波间的正交性 %}

{% note success, 上行采用SC-FDMA技术 %}

## OFDM基本原理

{% note success, 高速串行转低速并行 %}

{% note success, 傅里叶逆变换 %}

## 循环前缀

{% note success, 目的：降低ISI和ICI %}

{% note success, 分类：常规CP和扩展CP %}



## OFDM和CDMA的对比

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200425162921.png)

### OFDM缺点

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200425163141.png)



## SC-FDMA

{% note success, 单载波频分多址接入（Single  Carrier  Frequency  Division  Multiple  Access） %}

<br>

SC-FDMA类似于OFDMA，但SC-FDMA可以降低PAPR（峰均比）。



## OFDMA  VS  SC-FDMA

- OFDMA导致<kbd>高PAPR</kbd>，影响UE的成本和电池寿命
- SC-FDMA采用<kbd>单载波技术</kbd>，<kbd>峰均比（PAPR）低</kbd>，有效提高RF功率放大器的效率，降低终端成本和耗电量



## 下行多址方式-OFDMA

集中式：连续RB分给一个用户

{% folding 点击查看优点 %}

{% note success, 优点：调度开销小 %}

{% endfolding %}

分布式：分配给用户的RB不连续

{% folding 点击查看优点 %}

{% note success,  优点：选频调度增益较大 %}

{% endfolding %}

<br>

**RB(Resource Block)**：资源块。业务信道资源分配的资源单位，时域上为一个时隙，频域上为12个子载波。

**RE(Resource Element)**：最小的资源单位，时域上为一个符号，频域上为一个子载波。

<br>

## 上行多址方式-SC-FDMA

与OFDMA相同，将传输带宽划分成一系列正交的子载波资源，将不同的子载波资源分配给不同的用户实现多址。注意不同的是：任一终端使用的子载波必须连续。

<br>

{% note success,  在任一调度周期中，一个用户分得的子载波必须是连续的 %}

<br>

上行方向上给用户分配RB要满足：
$$
RB = 2^a·3^b·5^c
$$

##  总结

### OFDM的缺点

{% note success, 高峰均比，高同步要求，同频干扰 %}

### SC-FDMA定义

{% note success, 目的：抗峰均比 %}

{% note success, 傅里叶表换&傅里叶逆变换 %}

### 上下行资源的分配

上行：资源集中&连续RB数满足$$ RB = 2^a·3^b·5^c $$

下行：资源既可集中，也可分布