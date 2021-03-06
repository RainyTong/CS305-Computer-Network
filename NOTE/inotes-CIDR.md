## What is CIDR?

> Classless Interdomain Routing 无类别域间路由选择

**CIDR采用各种长度的"网络前缀"来代替分类地址中的网络号和子网号，其格式为：IP地址 = {<网络前缀>,<主机号>}**。

为了区分网络前缀，通常采用"斜线记法"（CIDR记法），即IP地址/网络前缀所占比特数。例如：192.168.24.0/22 表示32位的地址中，前22位为网络前缀，后10(32-22=10)位代表主机号。在换算中，192.168.24.0/22 对应的二进制为：

1100 0000(192)，1010 1000(168)，0001 10 ***00***(24)，***0000 0000***(0)


其中加粗倾斜为主机号，总共有10位。当这10位全为0时，取最小地址192.168.24.0，当这10位全为1时，取最大地址192.168.27.255。但请注意，在实际中，主机号全为0或者全为1的地址一般不使用，作为预留地址另有作用。所以第一个地址为1100 0000，1010 10000，0001 1000，0000 0001，即192.168.24.1 最后一个地址为：1100 0000，1010 10000，0001 1011，1111 1110，即192.168.27.254

 

因此，本例中将第三段地址数据中最小是00011000（24），最大是00011011（27），第四段地址数据中最小为0000 0001（1），最大为1111 1110（254），以上括号中数据为十进制，其前面为二进制。所以本例中192.168.24.0/22 对应地址段为192.168.24.1-192.168.27.254，共4个网段。

---

:wink: **CIDR表示方法**：IP地址/网络ID的位数，比如192.168.23.35/21，其中用21位表示网络ID。

例1：192.168.23.35/21

```子网掩码：11111111 11111111 11111000 00000000则为255.255.248.0```
