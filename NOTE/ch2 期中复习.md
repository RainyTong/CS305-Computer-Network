# ch2 期中复习

#### principles of network applications
1. Network application:

   E-mail, Web, P2P file sharing, remote login, streaming stored Video (Youtube), voice over IP (Skype)

2. Application structure

   - Client-server

     - Server: 3 features

       | 1. Always-on                    |
       | :------------------------------ |
       | **2. 不变的IP address**         |
       | **3. Data centers for scaling** |

     - Client

   - Peer-to-peer: 4 features

     | 1. no always-on server                                       |
     | ------------------------------------------------------------ |
     | **2. arbitrary end systems directly communicate**            |
     | **3. 有需求，有供给 ----<font color=#B22222>Self scalability: new peers bring service demands and service capacity.</font>** |
     | **4. (flaw) peers are intermittently connected and change IP address** |

3. About msg

   - Process: client process & server process
   - Socket
   - Process's identifier: IP address + Port number
     - *example*: to send HTTP msg to gaia.cs.umass.edu web server 
       - IP address: 128.119.245.12
       - Port number: 80

4. Transport service requirements of an app:

   - data integrity
   - timing 
   - throughput: *bit per second*
     - 一些应用需要“确保吞吐量”， 如：因特网电话
     - 一些应用属于弹性应用，如：电子邮件，文件传输，Web传送等

   <img src="/Users/wangyutong/Library/Application Support/typora-user-images/image-20181029090922304.png" style="width:1100px" />

   - security

> Internet transport protocol service:
>
> <img src="/Users/wangyutong/Library/Application Support/typora-user-images/image-20181029091759420.png" style="width:1100px" />
>
> App & corresponding (app layer protocol & trans layer protocol)
>
> <img src="/Users/wangyutong/Library/Application Support/typora-user-images/image-20181029091923371.png" style="width:1100px" />



5. App-layer protocol : *define four things*

- types of msg exchanged (e.g., request, response)
- msg syntax
- msg semantics
- rules for when & how process send & respond to msg

---

#### web & http

- http = hypertext transfer protocol:

  - http is <font color=#FF6699>"stateless" </font>

  -  HTTP connections:

    :one:non-persistent: <font color=#FF6699>at most one object can be sent over TCP connection </font>

    - ```response time = 2RTT + file transmission time```

      <img src="/Users/wangyutong/Library/Application Support/typora-user-images/image-20181030115138452.png" style="width:700px" />

    :two:persistent

- each web object is addressable by  a URL   [URL = host name + path name]

- 

