## Intra-AS routing in the Internet

- AS: Autonomous System 自治系统
  - Intra-autonomous system routing protocol: 在一个自治系统内运行的路由选择算法叫做**自制系统内部路由选择协议**
  - **网关路由器 **(gateway router)  ==> make connections between AS
  - Intra-AS routing: AS 内部 
  - Inter-AS routing: AS 之间
  - forwarding table 由AS间路由选择协议和AS内部路由选择协议共同决定
- AS间路由选择协议 要处理的两件事：
  1. 从相邻AS获取可达性信息
  2. 向该AS中所有路由器传播可达性信息

- AS内部路由选择协议 == 内部网关协议 IGP （Interior Gateway Protocol）

  - OSPF (Open Shortest Path First)

    i. 基于IP的网络层协议

    ii. 使用link-state algorithm

    iii. 路由器向**自治系统内**所有其他路由器广播路由选择信息

    优点：

    - Security 
    - Multiple same-cost paths allowed
    - Support both uni- and multi-cast
    - **支持在单个路由选择域内的层次结构** 

---

- AS间路由选择协议 —— BGP （Border Gateway Protocol）边界网关协议

  - 1. BGP basic

       ![image-20181231171830236](/Users/wangyutong/Library/Application Support/typora-user-images/image-20181231171830236.png)

       在边界网关协议BGP中，路由器之间通过使用半永久的TCP连接来交换路由信息。

       图中的所有连线都是BGP TCP连接，位于连接两端的路由器称为BGP对等方(BGP peers)，沿着该连接发送报文的TCP连接称为BGP会话(BGP session)。此外，跨越两个AS的BGP会话称为外部BGP会话(**eBGP**)，在同一个AS中的两台路由器之间的BGP会话称为内部BGP会话(**iBGP**)。



  - 2. 路径属性和BGP路由

       :imp: 当一台路由器通过BGP会话通告一个前缀时，它在前缀中包括一些**BGP属性(BGP Attributes)** ,

       带有*属性*的*前缀*被称为一条**路由(route)**。

       （Ex. 前缀举例—— 138.16.64/22）

       - 属性1: AS-PATH

         ​	当一个前缀传送到一个AS时，该AS将它的ASN增加到AS-PATH属性中

       - 属性2: NEXT-HOP


---

### SDN (Software defined networking)

Why?

- 更简单的network management [避免router错误配置，对于traffic flows的更大的灵活性]

- *"table-based fowarding allows **programming** routers"* ​ ​ ​ :whale:
- Open implementation of control plane

SDN组成：

SDN = data plane + control plane = [SDN-controlled switches] + [SDN controller + network-control applications]

![image-20190101113121732](/Users/wangyutong/Library/Application Support/typora-user-images/image-20190101113121732.png)



- SDN-controlled switches:
  - fast simple 实现 forwarding in hardware
  - **switch flow table** 由controller计算并安装
  - **API** for control (defines what is controllable and what is not)
  - **protocol** for communicating with controller
- SDN controller
  - maintain network state information 
  - Interacts with *network control applications* above via northbound API
  - interacts with *network switches* below via southbound API
  - implemented as distributed system for performance, scalability, fault-tolerance, robustness​ :whale:



>  SDN controller = Interface layer(to apps above) + state management layer (**a distributed database**) + communication layer(with swithes below)

![image-20190101113148900](/Users/wangyutong/Library/Application Support/typora-user-images/image-20190101113148900.png)



- Network application layer
  -  “brains” of control: implement control functions using lower-level services, API provided by SND controller 
  -  unbundled: can be provided by 3rd party: distinct from routing vendor, or SDN controller 





:eyes:: OpenFlow



---

### ICMP （Internet Control Message Protocol）

- **network-layer “above” IP**:  ICMP msgs carried in IP  datagrams 
- ICMP message: type, code plus first 8 bytes of IP datagram causing error

### SNMP (Simple Network Management Protocol)

