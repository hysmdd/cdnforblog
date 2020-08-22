---
title: 网络接入技术与方法
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 计算机三级
date: 2020-04-24 18:48:12
music:
  type: song  
  id: 1370047789
comments: true
tags:  
	- 网络技术
	- 计算机三级
---

数字用户线xDSL接入技术

光纤同轴电缆混合网

无源光网络（PON）标准化的业务（OC-1=51.84Mbps）

宽带接入技术IEEE 802.16标准与城域网

<!-- more -->

## 宽带接入技术的基本类型

从<red>用户接入</red>的角度，宽带接入可以分为<kbd>接入技术</kbd>与<kbd>接入方式</kbd>两种类型，其中接入方式与用户工作环境与需求相关。

从<red>技术实现</red>的角度，且前宽带接入技术主要有：<kbd>数字用户线（xDSL）技术</kbd>、<kbd>光纤同轴电缆混合网（HFC）技术</kbd>、<kbd>光纤接入技术</kbd>、<kbd>局域网接入技术</kbd>以及<kbd>无线接入技术</kbd>。其中，无线接入又可以分为<kbd>无线局域网接入</kbd>、<kbd>无线城域网接入</kbd>与<kbd>无线Ad hoc接入</kbd>。



### 真考试题

下列技术中，<red>不属于</red>无线接入技术的是（		）。

{% checkbox green,  Ad hoc %}
{% checkbox green checked,  SDH %}
{% checkbox green,  WiFi %}
{% checkbox green,  WiMAX %}



## 各种接入技术

### 数字用户线xDSL接入技术

xDSL中x的意思是表示它的不同类型，例如，可以理解x是A、H或RA等，它们对应于不同的数字用户线技术。xDSL技术根据上行和下行的速率是否相同可分为<kbd>速率对称型</kbd>和<kbd>速率非对称型</kbd>两种。

<br>

{% p subtitle, 根据信号传输的速率、距离以及上行速率与下行速率的不同，xDSL技术主要可以分为以下几种：  %}
{% folding 点击查看具体内容 %}

{% note warning, 非对称数字用户线（ADSL）  %}

{% note warning, 高比特率数字用户线（HDSL）  %}

{% note warning, 速率自适应数字用户线（RADSL）  %}

{% note warning, 超高比特率数字用户线（VDSL）  %}

{% endfolding %}

<br>

xDSL技术的上行与下行速率

| xDSL  | 上/下行速率（距离5.5km） | 上/下行速率（距离3.6km） | 是否对称 | 线对数 |
| :---: | :----------------------: | :----------------------: | :------: | :----: |
| ADSL  |   64Kbit/s / 1.5Mbit/s   |  640Kbit/s  /  6Mbit/s   |    否    |   1    |
| HDSL  |       1.554Mbit/s        |       1.554Mbit/s        |    是    |   2    |
| VDSL  |   2.3Mbit/s / 51Mbit/s   |  2.3Mbit/s  /  51Mbit/s  |    否    |   2    |
| RADSL |   64Kbit/s / 1.5Mbit/s   |  640Kbit/s  /  6Mbit/s   |    否    |   1    |

<br>

ADSL的技术特点主要表现在：

- 能够利用现有的用户电话铜双绞线，以重叠和不干扰传统模拟电话业务的方式，即普通电话业务（POTS）的方式，提供高速数字业务。ADSL允许用户在保留已有的模拟电话业务的同时，进行Internet在线访问、视频点播（VOD）等新型宽带业务。
- 该技术与本地环路的实际参数以及用户电话铜双绞线的特性关系都不大，所以用户不需要进行电缆的重新铺设。
- 上行速率在<kbd>64-640Kbit/s</kbd>，下行速率在<kbd>500Kbit/s~7Mbit/s</kbd>，用户可以根据需要自行选择。

<br>

#### 真考试题

ADSL的上行速率在（		）。

{% checkbox green,  10Mbps ~ 20Mbps %}

{% checkbox green,  7Mbps ~ 10Mbps %}

{% checkbox green,  640Kbps ~ 7Mbps %}

{% checkbox green checked,  64Kbps ~ 640Kbps %}

<br>

下列关于xDSL技术的描述中，<red>错误</red>的是（		）。

{% checkbox green,  xDSL技术按上行与下行速率分为速率对称与非对称两类 %}

{% checkbox green,  ADSL技术在现有用户电话线上同时支持电话业务和数字业务 %}

{% checkbox green checked,  ADSL上行传输速率最大可以达到8Mbps %}

{% checkbox green,  HDSL上行传输速率为1.544Mbps %}



### 光纤同轴电缆混合网

#### 光纤同轴电缆混合网的基本结构

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200424134759.png)

{% note success, HFC是由<kbd>电视头端</kbd>、<kbd>长距离干线</kbd>、<kbd>放大器</kbd>、<kbd>馈线</kbd>与<kbd>下引线</kbd>组成。 %}

{% note success, HFC是新一代的有线电视网络，是一个<kbd>双向传输系统</kbd>，光纤结点通过同轴电缆下引线可以为<kbd>500～2000</kbd>个用户服务。 %}

{% note success, HFC<kbd>改善了信号质量，提高了可靠性</kbd>，线路可以使用的带宽甚至可以达到<kbd>1GHz</kbd>。 %}

{% note success, 从用户接入的角度来看，光纤到HFC是经过双向改造的有线电视网络，是用户通过有线电视宽带接入Intermet的一种重要的方式。 %}

{% note success, HFC是使用<kbd>Cable Modem</kbd>，通过有线电视宽带接入Intermet的，数据传输速率可达<kbd>10-36Mbit/s</kbd>。 %}

<br>

#### 真考试题

下列关于光纤同轴电缆混合网HFC的描述中，<red>错误</red>的是（		）。

{% checkbox green,  HFC是一个双向传输系统 %}

{% checkbox green,  HFC由有线电视头端、长距离干线、放大器、馈线和下引线组成 %}

{% checkbox green,  HFC的数据传输速率可达10~36Mbps %}

{% checkbox green checked,  HFC通过路由器将用户计算机与同轴电缆连接起来 %}

<br>

#### 电缆调制解调器

<kbd>Cable Modem把用户过算机与有线电视同抽电缆连接起来</kbd>，不仅有调制解调功能，也带有加密解密和协议适配，以及网桥、路由器与集线器的部分功能。Cable Modem利用<kbd>频分复用</kbd>的方法，将双向信道分为：<kbd>从计算机终端到网络方向称为上行信道，从网络到计算机终端方向称为下行信道</kbd>。

<br>

从<red>数据传输</red>方向上，Cable Modem可以分为<kbd>单向</kbd>、<kbd>双向</kbd>两类。
从<red>传输方式</red>上，Cable Modem可以分为<kbd>双向对称式传输</kbd>和<kbd>非对称式传输</kbd>两类。
从<red>同步方式</red>上，Cable Modem可以分为<kbd>类似于Ethernet的同步交换</kbd>和<kbd>类似于ATM技术的异步交换</kbd>两类。
从<red>接入的角度</red>，Cable Modem可以分为<kbd>个人Cable Modem</kbd>和<kbd>宽带多用户Cable Modem</kbd>。
从<red>接口的角度</red>，Cable Modem可分为<kbd>外置式</kbd>、<kbd>内置式</kbd>和<kbd>交互式机顶盒</kbd>3种。

<br>

#### 真考试题

下列关于光纤同轴电缆混合网HFC的描述中，<red>错误</red>的是（		）。

{% checkbox green,  HFC是一个双向传输系统 %}

{% checkbox green,  Cable Modem利用频分多路复用方法将信道分为上行信道与下行信道

 %}

{% checkbox green,  Cable Modem传输方式分为对称式和非对称式两类 %}

{% checkbox green checked,  HFC通过Cable Modem将光缆与同轴电缆连接起来 %}

解析：HFC通过Cable  Modem将用户计算机与同轴电缆连接的，并不是将光缆与同轴电缆连接的。

<br>

### 光纤接入技术

APON（宽带无源光网络）是ATMPON的简称。<kbd>ATM是一种基王信元的传输协议</kbd>，能为接入网<kbd>提供动态的带宽分配</kbd>，从而更适合宽带数据业务的需要。
EPON（以太网无源光网络）是基于以太网的PON技术。EPON采用点到多点结构、无源光纤传输，在以太网之上提供多种业务，<kbd>EPON是一种实现光纤到户的重要技术</kbd>。

<br>

无源光网络（PON）是基于ITU ”基于无源光纤网的高速光纤接入系统“  下进行标准化的。

- <kbd>OC-3</kbd>：155.520Mbit/s的对称业务
- 上行<kbd>OC-3</kbd>：155.520Mbit/s；下行<kbd>OC-12</kbd>：622.080Mbit/s的不对称业务。

{% note success, OC-1 = 51.84Mbit/s %}

{% note success, 传输媒介可以是一根或两根单模光纤，双向传输通过波分复用（一根或两根光纤）实现。  %}

<br>

#### 真考试题

ITU标准OC-24和OC-12的传输速率分别为（			）。

{% checkbox green, 155.52Mbps和51.84Mbps %}

{% checkbox green,  155.52Mbps和622.08Mbps %}

{% checkbox green,  622.08Mbps和155.52Mbps %}

{% checkbox green checked,  1.244Gbps和622.08Mbps %}

解析：

{% note success, 

OC-24：OC-1 × 24 = 51.84  × 24  =  1244.16Mbps = 1.244Gbps 

<br>

OC-12:   OC-24  ÷  2  =  1244.16  ÷  2  =  622.08Mbps

%}

<br>

ITU标准OC-3和OC-12的传输速率分别为（			）。

{% checkbox green, 622.08Mbps和1.244Gbps %}

{% checkbox green checked,  155.52Mbps和622.08Mbps %}

{% checkbox green,  155.52Mbps和51.84Mbps %}

{% checkbox green,  51.84Mbps和622.08Mbps %}

解析：

{% note success, 

OC-3：OC-1 × 3 = 51.84  × 3 =   155.52Mbps

<br>

OC-12:   OC-1  ×  12  =  51.84  × 12  =  622.08Mbps

%}

<br>



### 宽带无线接入技术

无线接入技术主要有<kbd>IEEE 802.11标准的无线局域网（WL.AN）接入</kbd>、<kbd>IEEE 802.16标准的无线城域网（WMAN）接入</kbd>，以及正在发展的<kbd>Adhoc接入技术</kbd>几种。

#### 无线接入技术的分类与应用

<red>近距离使用可采用IEEE 802.11标准的无线局域网技术</red>，它可以满足一定地理范围内的用户无线接入需求；<red>远距离使用则采用IEEE 802.16标准的WiMAX技术</red>，该技术可以在<kbd>50km范围内</kbd>提供最高<kbd>70Mbit/s</kbd>的传输速率。

<br>

IEEE 802.11标准与IEEE 802.16标准<kbd>均针对无线环境</kbd>,但由于通用对象不同,采用的技术与协议解决问题的重点也不相同。<red>IEEE 802.11标准的重点在解决局域网范围的移动节点通信问题,而IEEE 802.16标准的重点是解决建筑物之间的数据通信问题</red>。

<br>

#### IEEE  802.11标准与无线局域网

- <kbd>IEEE 802.11</kbd>定义了使用<kbd>红外</kbd>、<kbd>跳频扩频</kbd>与<kbd>直接序列扩频技术</kbd>,数据传输速率为<kbd>1Mbit/s</kbd>或<kbd>2Mbit/s</kbd>

- <kbd>IEEE 802.11a</kbd>将传输速率提高到<kbd>54Mbit/s</kbd>

- <kbd>IEEE 802.11b</kbd>定义了使用<kbd>直序扩频技术</kbd>,传输速率为<kbd>1Mbit/s</kbd>、<kbd>2Mbit/s</kbd>、<kbd>5.5 Mbit/s</kbd>与<kbd>11Mbit/s</kbd>。

<br>

#### IEEE  802.16标准与无线城域网

- 按IEEE 802.16标准建立采用<kbd>全双工</kbd>、<kbd>宽带通信</kbd>方式工作的基站。
- IEEE 802.16标准规定了无线网络使用更高的、毫米波的<kbd>10~~~66GHz</kbd>波段的频率。
- 在IEEE 802.16标准上增加了两个物理层标准<kbd>IEEE 802.16d</kbd>与<kbd>IEEE 802.16e</kbd>。
- <red>与IEEE 802.16标准工作组对应的论坛组织是<kbd>WiMAX</kbd>，最高的传输速率为<kbd>134Mbit/s</kbd></red>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200424153636.png)

<br>

##### 真考试题

下列关于IEEE  802.16标准的描述中，<red>错误</red>的是（			）。

{% checkbox green,  提供宽带城域网用户访问Intenet所需要的路由服务 %}

{% checkbox green checked,  最高传输速率为234Mbps  %}

{% checkbox green,  使用无线频段为10~66GHz  %}

{% checkbox green,  与IEEE  802.16标准工作组对应的论坛组织是WiMAX  %}

<br>

下列关于IEEE  802.16标准的描述中，<red>错误</red>的是（			）。

{% checkbox green,  802.16主要用于解决城市地区范围内的宽带无线网接入问题 %}

{% checkbox green checked,  802.16a用于移动结点接入  %}

{% checkbox green,  802.11d用于固定结点接入  %}

{% checkbox green,  802.16e用于固定或移动结点接入  %}

<br>

下列关于接入技术特征的描述中，<red>正确</red>的是（			）。

{% checkbox green,  APON是一种无线接入技术 %}

{% checkbox green,  Cable  Modem利用波分复用的方法将信道分为上行信道和下行信道 %}

{% checkbox green,  IEEE  802.11b将传输速率提高到54Mbps %}

{% checkbox green checked,  ADSL技术具有非对称带宽特征 %}

{% folding 点击查看解析 %}

{% note warning, 

APON是一种光纤接入技术的一种，A选项错误；Cable  Modem利用的是频分复用的方法将信道分为上行信道和下行信道，故B选项错误；IEEE  802.11b最高的传输速率是11Mbit/s，802.11a最高的速率是54Mbit/s，故C选项错误。

 %}

{% endfolding %}

<br>

下列关于接入技术特征的描述中，<red>正确</red>的是（			）。

{% checkbox green, EPON是一种无线接入技术 %}

{% checkbox green, Cable  Modem利用波分复用的方法将信道分为上行信道和下行信道 %}

{% checkbox green, 802.11a将传输速率提高到11Mbps %}

{% checkbox green checked, ADSL技术具有非对称带宽特征 %}

{% folding 点击查看解析 %}

{% note warning, 

EPON是一种光纤接入技术，故A选项错误；Cable  Modem利用的是频分复用的方法将信道分为上行信道和下行信道，故B选项错误；IEEE  802.11b最高的传输速率是11Mbit/s，802.11a最高的速率是54Mbit/s，故C选项错误。

 %}

{% endfolding %}

<br>

{% note success, 非对称数字用户线ADSL技术特点（上行速率在64-640Kbps，下行速率在500Kbps-7Mbps %}