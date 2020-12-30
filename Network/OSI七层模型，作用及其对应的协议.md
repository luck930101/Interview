![img](https://imgconvert.csdnimg.cn/aHR0cDovL3M3LjUxY3RvLmNvbS93eWZzMDIvTTAwLzQ4LzM2L3dLaW9tMVFHZFBiUUpCVXBBQUdpWkxzSnE4YzY1Ny5qcGctd2hfNjUxeC1zXzIyNDU0Mjc0OTYuanBn?x-oss-process=image/format,png)

 

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTE4NzM4NS8yMDE4MDIvMTE4NzM4NS0yMDE4MDIyMzE2NDQ0MzIzNy0xMDQ4NTk0ODA3LnBuZw?x-oss-process=image/format,png)

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTE4NzM4NS8yMDE4MDIvMTE4NzM4NS0yMDE4MDIyMzE2NDQ1MjQxNy00MDU0MDQzMzkucG5n?x-oss-process=image/format,png)

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTE4NzM4NS8yMDE4MDIvMTE4NzM4NS0yMDE4MDIyMzE2NDU1Mzc0Ni0xNTY0MTgzMTkzLnBuZw?x-oss-process=image/format,png)

 

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTE4NzM4NS8yMDE4MDIvMTE4NzM4NS0yMDE4MDIyMzE2NDUwMzE1Mi0zMzQ0NzgzMzkucG5n?x-oss-process=image/format,png)

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTE4NzM4NS8yMDE4MDIvMTE4NzM4NS0yMDE4MDIyMzE2NDQyMTQ3NS0xODI1OTE4MjU5LmpwZw?x-oss-process=image/format,png)

物理层（Physical Layer）

- 传输介质： 网线电缆、集线器、光纤、还有无线信道。
- 传输的是比特流，单位是bit比特位（本质上是0、1高低电平）。
- 在物理层，使用物理介质支持的信号类型来传输数据：电压，射频或红外或普通光脉冲。

数据链路层（Data Link Layer）：

- 设备： 网卡
- 负责建立和管理节点间的链路（mac地址）
- 传输的是frame数据帧
- 从物理层获取数据时，数据链路层会检查物理传输错误，并将位打包到数据“帧”中。数据链路层还管理物理寻址方案，例如用于以太网的[MAC](https://www.lifewire.com/media-access-control-mac-817973)地址，控制任何各种网络设备对物理介质的访问。因为数据链路层是OSI模型中最复杂的单个层，所以它通常分为两部分：媒体访问控制子层和逻辑链路控制子层

网络层（Network Layer）：

- 选择合适的路径将数据发送到目标地址（ip地址）
- 传输的是数据包
- 网络层在数据链路层之上添加了路由的概念。当数据到达网络层时，将检查每个帧内包含的源地址和目标地址，以确定数据是否已到达其最终目标。如果数据已到达最终目的地，则此第3层将数据格式化为传递到传输层的数据包。否则，网络层将更新目标地址，并将帧向下推至较低层。 为了支持路由，网络层维护逻辑地址，例如 网络上设备的IP地址。网络层还管理这些逻辑地址和物理地址之间的映射。在IP网络中，此映射是通过地址解析协议（ARP）完成的。

> 数据链路层和网络层的共同点和区别：
>
> 1、都是基于目标地址将数据发给接收端，但网络层是ip地址，数据链路层是mac地址。网络层发送的整个数据，数据链路层发送的是数据的一个分段

传输层（Transport Layer）：

- 负责连接的建立和断开和数据的传输，并保证数据的可靠性（数据不丢失）和完整性（数据不缺失）和正确性（顺序不混乱）
- 传输的数据单位是段segment
- 传输层通过网络连接传递数据。[TCP](https://www.lifewire.com/transmission-control-protocol-and-internet-protocol-816255)是传输第4层[网络协议](https://www.lifewire.com/definition-of-protocol-network-817949)的最常见示例[。](https://www.lifewire.com/definition-of-protocol-network-817949) 不同的传输协议可能支持一系列可选功能，包括错误恢复，流控制以及对重传的支持。

会话层（Session Layer）：

- 负责连接，建立和断开连接的时机，数据的发送顺序

表示层（Presentation Layer）

- 它对来自应用层的命令和数据进行解释，对各种语法赋予相应的含义，并按照一定的格式传送给会话层。其主要功能是“处理用户信息的表示问题，如：数据格式处理、数据的编码、压缩和解压缩、加密和解密。
- 表示层是所有OSI模型中最简单的功能。

应用层（Application Layer）

- 它是计算机用户，以及各种应用程序和网络之间的接口，其功能是直接向用户提供服务，完成用户希望在网络上完成的各种工作。
- 应用层为用户提供的服务和协议有：文件服务、目录服务、文件传输服务（FTP）、远程登录服务（Telnet）、电子邮件服务（E-mail）、打印服务、安全服务、网络管理服务、数据库服务等
- 应用层向最终用户应用程序提供网络服务。网络服务通常是处理用户数据的协议。例如，在Web浏览器应用程序中，应用程序层协议[HTTP](https://www.lifewire.com/hypertext-transfer-protocol-817944)打包了发送和接收网页内容所需的数据。该层7将数据提供给表示层（并从中获得数据）。