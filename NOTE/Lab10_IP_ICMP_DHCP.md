# CS305 Lab Tutorial

## Lecture 10 IP ICMP DHCP

---

**CONTENTS**

- IP
  - best effort
  - IP address 
  - IP fragment & assemble
- ICMP
  - Detect & report
- DHCP
  - Configuration parameters to dynamically configured hosts
- :yellow_heart:*tools: ping, traceroute, pingplotter, Wireshark*

---

### IP

1. 2 function: addressing and fragmentation

### IP datagram

- Type of Service
- Time to Live
- Options
- Header Checksum

![image-20181118150042555](/Users/wangyutong/Library/Application Support/typora-user-images/image-20181118150042555.png)

### Protocol field of IP datagram:

- IHL(4 bits) : Internet header length = 20 bytes (5)   ​ :yellow_heart:NOTE: 5 means <u>5 * 32 bit words</u>           **==>based on 32 bit words**
- Total Length(16 bits): the length of the datagram, including **internet header and data(TCP/UDP header + data). **         **==> based on bytes**

### IP Fragment

- Flags: 3 bits

  ![image-20181118153007187](/Users/wangyutong/Library/Application Support/typora-user-images/image-20181118153007187.png)

- Flagment offset: 13 bits

- **offset** is measured in units of 8 octets (64 bits) ==> * 8 to get the **bytes** number

- Identification

### ICMP

> Internet Control Message Protocol



> ICMP is used from gateways to hosts and between hosts to report errors and make routing suggestions.
>
> 是TCP/IP协议族的一个子协议，属于网络层协议。

Header length  = 8 bytes

### ICMP (Echo and echo reply)

![image-20181118161551095](/Users/wangyutong/Library/Application Support/typora-user-images/image-20181118161551095.png)

Type: 8 ==> echo msg, 0 ==> echo reply msg



### ICMP: time exceeded

![image-20181118161603507](/Users/wangyutong/Library/Application Support/typora-user-images/image-20181118161603507.png)

:exclamation:*Internet Header + 64 bits of Original Data Datagram* ==> IP header + 8-bytes ICMP header

![image-20181118161819786](/Users/wangyutong/Library/Application Support/typora-user-images/image-20181118161819786.png)



### DHCP

> **Dynamic Host Configuration Protocol** ==> 用于局域网的网络协议
>
> 主要作用是集中的管理、分配IP地址，使网络环境中的主机动态的获得IP地址、Gateway地址、DNS服务器地址等信息，并能够提升地址的使用率。



















