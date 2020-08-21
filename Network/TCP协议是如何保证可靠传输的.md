TCP通过序列号、检验和、确认应答信号、重发控制、连接管理、窗口控制、流量控制、拥塞控制实现可靠性。

## 1. 确认应答和序列号

序列号：TCP**传输时将每个字节的数据都进行了编号**，这就是序列号。 

确认应答：TCP传输的过程中，每次**接收方收到数据后，都会对传输方进行确认应答**。也就是发送ACK报文。

这个ACK报文当中带有对应的**确认序列号**，告诉发送方，接收到了哪些数据，下一次的数据从哪里发。

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyODIwMzYxMDk4NS0xOTczMDY4Nzg5LnBuZw)

 

序列号的作用不仅仅是应答的作用，有了序列号能够**将接收到的数据根据序列号排序**，并且**去掉重复序列号的数据**。

这也是TCP传输可靠性的保证之一。

 

 

## 2. 超时重传

在进行TCP传输时，由于确认应答与序列号机制，也就是说**发送方发送一部分数据后，都会等待接收方发送的ACK报文**，**并解析ACK报文，判断数据是否传输成功**。

**如果发送方发送完数据后，迟迟没有等到接收方的ACK报文，这该怎么办呢？**而没有收到ACK报文的原因可能是什么呢？

 

首先，**发送方没有接收到响应的ACK报文原因可能有两点**：

a、数据在传输过程中由于网络原因等直接全体丢包，**接收方没有接收到**。

b、接收方接收到了响应的数据，但是**发送的ACK报文响应**却由于网络原因**丢包了**。

 

TCP在解决这个问题的时候引入了一个新的机制，叫做**超时重传机制。**

简单理解就是发送方在发送完数据后等待一个时间，时间到达没有接收到ACK报文，那么对刚才发送的数据进行重新发送。

**如果是刚才第一个原因，接收方收到二次重发的数据后，便进行ACK应答。**

**如果是第二个原因，接收方发现接收的数据已存在（判断存在的根据就是序列号，所以上面说序列号还有去除重复数据的作用），那么直接丢弃，仍旧发送ACK应答。**

那么发送方发送完毕后**等待的时间是多少呢？**如果这个等待的时间过长，那么会影响TCP传输的整体效率，如果等待时间过短，又会导致频繁的发送重复的包。如何权衡？

由于TCP传输时保证能够在任何环境下都有一个高性能的通信，因此这个最大超时时间（也就是等待的时间）是动态计算的。

 

## 3. TCP的连接管理。 

（1）TCP是面向有连接的数据通信，也就说在进行实际的数据包的收发之前，会先做好通信两端主机的准备工作：TCP三次握手！

（2）在双端主机进行数据的交互完成过之后，会进行TCP连接的断开处理。见上面的博客。

## 4. 流量控制

​          接收端在接收到数据后，对其进行处理。**如果发送端的发送速度太快，导致接收端的结束缓冲区很快的填充满了。此时如果发送端仍旧发送数据，那么接下来发送的数据都会丢包**，继而导致丢包的一系列连锁反应，超时重传呀什么的。而**TCP根据接收端对数据的处理能力，决定发送端的发送速度，这个机制就是流量控制。**

简单来说就是接收方处理不过来的时候，就把窗口缩小，并把窗口值告诉发送端。

   

在这里只**考虑A向B发送数据**，假设在连接在建立时，B告诉A:我的接收窗口rwnd=400（receiver window）,不过在报文中已经省略了

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyODIwNDk0MjA3OS0xNDc1Mzc5NzEzLnBuZw)

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyODIwNTAwMDEzNy01MDUzNzc4NzkucG5n)

如果接收到窗口大小的值为0，那么发送方将停止发送数据。并**定期的向接收端发送窗口探测数据段，让接收端把窗口大小告诉发送端。** 

## 5. 拥塞控制

如果网络出现拥塞，分组将会丢失，此时发送方会继续重传，从而导致网络拥塞程度更高。因此当出现拥塞时，应当控制发送方的速率。

这一点和流量控制很像，但是出发点不同。流量控制是为了让接收方能来得及接收，而拥塞控制是为了降低整个网络的拥塞程度。

 

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyOTA4NTE0NjcxMC0xNzk3NTQ5Njk4LnBuZw)

TCP 主要通过四个算法来进行拥塞控制：**慢开始、拥塞避免、快重传、快恢复。**

**慢开始算法原理**

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyOTA4NTkxNjAwMi04MTc2Nzc5NTAucG5n)

 

 

发送方需要维护一个叫做拥塞窗口（cwnd）的状态变量，注意拥塞窗口与发送方窗口的区别：**拥塞窗口只是一个状态变量，实际决定发送方能发送多少数据的是发送方窗口**。

为了便于讨论，做如下假设：

- 接收方有足够大的接收缓存，因此不会发生流量控制；

- 虽然 TCP 的窗口基于字节，但是这里设窗口的大小单位为报文段。

- 

    

当TCP连接进行初始化是，将拥塞窗口置为1。

图中的窗口单位不再使用字节而使用报文段。

慢开始门限的初始值设置为16个报文段，即ssthresh=16；

 **慢开始和拥塞避免**

1.然后开始慢开始算法（指数增长）。当cwnd=16时开始执行拥塞避免算法，呈现线性增长。

2.当拥塞窗口cwnd=24时出现超时，发送方判定为网络拥塞，于是调整门限值ssthresh=cwnd/2=12,同时设置拥塞窗口为1，进入慢开始阶段。

3.按照慢开始算法，发送方每收到一个新报文段的确认ACK拥塞窗口值增加。当cwnd=12时（图中点3）执行拥塞避免算法

**快重传和快恢复**

4 .当cwnd=16时（图中点4）出现了一个新的情况，就是发送方连续收到3个对统一报文段的重复确认（3-ACK）。发送方执行快重传和快恢复算法。

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyOTA5MDg1ODM3My0xNzkyOTMyMDMyLnBuZw)

 

 5 在图中点4，发送方知道只是丢失了个别的报文段，于是不启动慢开始，而是先进行快重传然后执行快恢复算法。

发送方设置调整门限值ssthresh=cwnd/2=8, 同时拥塞窗口cwnd=ssthresh=8（点5），然后进行拥塞避免算法

 

 

快重传：收到3个同样的确认就立刻重传，不等到超时；

快恢复：cwnd不是从1重新开始。



## 6. 滑动窗口

实际中的传输方式，

需要说明一下，**如果你不了解TCP的滑动窗口这个事，你等于不了解TCP协议**。

我们都知道，TCP必需要解决的可靠传输以及包乱序（reordering）的问题，

所以，TCP必需要知道网络实际的数据处理带宽或是数据处理速度，这样才不会引起网络拥塞，导致丢包。

 ![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyODIxMTUzMzg4MC0xMzIwOTE5MjAxLnBuZw)

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyODIxMTcwNDQ5My04MzY0NTM2OTkucG5n)

 

 

 发送方滑动窗口示意图：

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyODIxMDcwMzIxOS0xMDk5NzE5MjIxLnBuZw)

上图中分成了四个部分，分别是：（其中那个**黑模型就是滑动窗口**）

**#1已收到ack确认的数据。**

**#2已发出但还没收到ack的。**

**#3在窗口中还没有发出的（接收方还有空间）。**

**#4窗口以外的数据（接收方没空间）**

**注意：**

**滑动窗口里是 已发出但未收到ACk、还未发出的 数据**

 

**下面是个滑动后的示意图（收到36的ack，并发出了46-51的字节）：**

**![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWcyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTM5NjgwMy8yMDE4MTEvMTM5NjgwMy0yMDE4MTEyODIxMTE1NTcxOS0xMDAwOTcyMjg2LnBuZw)**