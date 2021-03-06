# 1.1 计算机网络的概述

## 1 计算机网络的概念

计算机网络：将一个分散的，具有独立功能的**计算机系统**，通过**通信设备**与**线路**连接起来，由功能完善的**软件**实现资源共享和信息传递的系统。

## 2 计算机网络的功能

* **数据通信**：最基本和最重要的功能，包括连接控制，传输控制，差错控制，流量控制，路由选择，多路复用。
* 资源共享
* 分布式处理
* 提高可靠性
* 负载均衡

1. **有关负载均衡和分布式：**

* 分布式是可以根据服务器用途来区分，比如
* 应用服务器
* 图片服务器
* 数据库服务器
* ……
* 多个同一用途服务器组成集群，需要负载均衡器检查每台服务器可用性

## 3 计算机网络的组成

3.1. 组成部分

* 硬件：主机，通信处理机，通信线路，交换设备
* 软件：包括资源共享的软件和用户使用的各种工具软件
* 协议：就是一种规则

3.2. 工作方式

* 边缘部分

  用户直接使用：C/S P2P, 用于通信资源共享

* 核心部分

  为边缘部分服务（提供连通性和交换服务）：包括路由器和大量的链路

3.3. 功能组成

* 通信子网：实现**数据通信**，由传输介质，通信设备，网络协议组成。**\(包括物理层，数据链路层，网络层\)**
* 资源子网：实现资源共享，数据处理

## **4 计算机组成的分类**

4.1. 分布范围：

* 广域网WAN\(交换技术\) 
* 城域网MAN 
* 局域网WAN\(广播技术\) 
* 个人局域网PAN 

4.2. 按使用者分类：

* 公用网 
* 专用网 

4.3. 按交换技术分类：

* 电路交换 
* 报文交换 
* 分组交换 

4.4. 拓扑结构：

* 总线型
* 星型
* 环型
* 网状型 

4.5. 传输技术：

* 广播式网络：共享公共通信信道 
* 点对点网络：分组存储转发，路由选择机制

