# Chapter 2 Application Layer

## 2.1 principles of network applications （应用层协议原理）
- 需要编写将在端系统上运行的软件
- 不需要写在网络核心设备，如： 路由器(routers)或链路层(link layer)交换机上运行的软件

### 1. possible structure of applications (应用程序的体系结构): 
- client-server 客户服务器体系结构
        
    - 有一个总是打开的主机 **服务器**， 服务来自其他主机的请求，其他主机称为 **客户** 
    - 客户之间**不直接**通信
    - 服务器具有固定的、周知的地址，**IP地址**
    - 配备大量主机的**数据中心(data center)**, 常作为强大的虚拟服务器
        
- peer-to-peer(p2p) 对等体系结构 
    - 主机之间使用**直接**通信 称为**对等方**
    - 不依赖于always-on server
    - :yellow_heart:**自拓展性**(self-scalability): 
        > New peers bring new service capacity, as well as new service demands.
    
    - 缺点：peers are intermittently(间断) connected， and change IP addresses
    
### 2. 不同端系统上进程间的通信

- *同一host上的processes communication使用 inter-process communication(defined by OS)*

- *多数应用程序由通信进程对组成*

> **进程 process**: 进行通信的是进程，而非程序  (Processes  send/recv msg to/from network)

> **报文 message**: 两个进程通过交换message而通信


在p2p文件共享的某些应用中，一个process可以既是客户(download the file)又是服务器(upload the file);
此时，**发起通信的进程被标识为客户，在会话开始时等待联系的进程是服务器**。
- [ ] *tips: 区分上文提到的客户服务器体系结构与这里的“应用程序的客户端和服务器端”～*


### 3. Sockets -- 进程与计算机网络之间的接口
> :yellow_heart:Process send/recv msg to/from **socket**  -> 进程通过一个称为socket的软件接口向网络发送msg和从网络接收msg。

- Socket 也称为应用程序和网络之间的**应用程序编程接口**（Application Programming Interface, API）

### 4. IP & Port number -- 进程寻址
- process must have **identifier**: :yellow_heart: identifier = IP address + prot numbers

    - host device has unique 32-bit IP address 
    - Web服务器端口号：80， 邮件服务器进程端口号：25

### 5. Transport service -- 可供应用程序使用的运输服务

1. data integrity 可靠数据传输 *ex. 电子邮件，文件传输...*
2. throughput 吞吐量 *ex. 一些带宽敏感的应用--因特网电话应用程序...*  
    - [ ] tips: 弹性应用 *elastic*
3. timing 定时 *ex. 游戏、因特网电话...*
4. security 安全性 *ex. 加密...*

### 6. Internet transport protocols services -- 因特网提供的运输服务

##### 1. TCP Service
- 面向连接的服务 connection-oriented
    - 握手阶段：应用层数据msg开始流动之前，TCP让客户和服务器互相交换运输层控制信息
    - TCP连接：在两个sockets之间建立
    - 结束msg发送时，必须拆除该链接
- 可靠的数据传送服务 reliable transport：


##### 2. UDP Service
- unreliable data transfer
- 轻量级，无握手过程

##### 3. 因特网运输协议不提供的服务

### 7. App-layer protocol 应用层协议
- 交换的msg类型：请求msg & 相应msg
- msg语法
- msg语义
- 一个进程何时、如何发送msg

有些应用层协议是由RFC文档定义的，因此它们位于公共域中。如：Web的应用层协议HTTP

- [ ] **Tips ：应用层协议是网络应用的一部分。如：Web是Client-Server应用，Web应用有很多组成成分：**

    :yellow_heart: Web应用 = 文档格式的标准HTML + Web浏览器 + Web服务器 + 应用层协议(HTTP)

> 5种重要的网络应用： Web，文件传输，电子邮件，目录服务，P2P

## 2.2 Web and HTTP


> 从因特网(Internet) 到万维网(World Wide **Web**, 即Web), Web是一个因特网应用。

### 1. HTTP概况
- 超文本传输协议是Web的应用层协议。
- 由两个程序实现：
    - client: browser that requests, receives,(using HTTP protocol) and ''displays'' Web objects
    - server: Web server sends (using HTTP protocol) objects in response to requests
    
- HTTP使用TCP作为它的支撑运输协议：
    1. HTTP客户发起一个与服务器的TCP连接，**port 80**
    2. 服务器接受来自客户的TCP连接
    3. HTTP msg 在client(Web browser)与server(Web server)之间交换
    4. TSP连接关闭

### 2. HTTP连接
##### 1. non-persistent HTTP 非持续连接
每一个请求／响应对 经由一个单独的TCP连接发送

##### 2. persistent HTTP 持续连接
所有请求／响应 经相同的TCP连接发送





























