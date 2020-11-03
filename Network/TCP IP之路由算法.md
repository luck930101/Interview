网络层的重要功能就是路由和转发。而路由是根据路由器根据所维护的路由表进行路由选择。所以，如果创建和更新转发表就是一个很重要的问题。通常，在路由时，我们总是选取所需代价最小的一条路由。



![img](https://upload-images.jianshu.io/upload_images/1234352-27d2e536e2aefc4c.png)

image.png

首先，我们需要将网络进行抽象，最常见的抽象就是，将网络抽象成图结构。



![img](https://upload-images.jianshu.io/upload_images/1234352-a0d219dad5e8d197.png)

image.png

每段链路的费用可以总是1，或者是，带宽的倒数、拥塞程度等。

关键问题: 源到目的（如u到z）的最小费用路径是什么？
 所谓的路由算法: 寻找最小费用路径的算法。

# 路由算法的分类

## 静态路由 vs 动态路由

静态路由就是所有路由信息由人工静态配置好，以后需要更新的话，就要重新配置。

- 手工配置
- 路由更新慢
- 优先级高

动态路由就是在网络随时根据网络拓扑结构的结构的变化，进行动态更新

- 路由更新快
- 定期更新
- 及时响应链路费用或网络拓扑变化

## 全局信息 vs 分散信息

有的路由算法需要所有路由器掌握完整的网络拓扑和链路费用信息，也就是对网络的全局有一个了解
 最有代表性的就是链路状态(LS)路由算法。

有的路由算法只需要路由器只掌握物理相连的邻居以及链路费用。通过邻居间信息交换、运算的迭代过程来更新路由信息。
 最有代表性的就是距离向量(DV)路由算法。

# 链路状态路由算法



![img](https://upload-images.jianshu.io/upload_images/1234352-391dfc3db94ea6b0.png)

image.png

首先将网络抽象，然后利用图算法中的最短路径算法，Dijkstra 算法。

所有结点(路由器)掌握网络拓扑和链路费用

- 通过“链路状态广播”
- 所有结点拥有相同信息

利用Dijkstra 算法计算从一个结点(“源” )到达所有其他结点的最短路径。从而可以获得该节点的转发表。
 然后对不同的节点进行迭代，就可以使所有节点都得到自己的转发表。

- c(x,y): 结点x到结点y链路费用；如果x和y不直接相连，则=∞
- D(v): 从源到目的v的当前路径费用值
- p(v): 沿从源到v的当前路径， v的前序结点
- N’: 已经找到最小费用路径的结点集合



```swift
1 初始化:
2 N' = {u}
3 for 所有结点v
4 if v毗邻u
5 then D(v) = c(u,v)
6 else D(v) = ∞
7
8 Loop
9 找出不在 N’中的w ，满足D(w)最小
10 将w加入N'
11 更新w的所有不在N’中的邻居v的D(v) :
12 D(v) = min( D(v), D(w) + c(w,v) )
13 /*到达v的新费用或者是原先到达v的费用，或者是
14 已知的到达w的最短路径费用加上w到v的费用 */
15 until 所有结点在N’中
```



![img](https://upload-images.jianshu.io/upload_images/1234352-15b14c1ea8f193ef.png)

image.png



![img](https://upload-images.jianshu.io/upload_images/1234352-6a903961381b1370.png)

image.png

算法复杂性: n个结点

- 每次迭代: 需要检测所有不在集合N’中的结点w
- n(n+1)/2次比较: O(n2)
- 更高效的实现: O(nlogn)

算法可能存在震荡现象



![img](https://upload-images.jianshu.io/upload_images/1234352-a8f000104e2daebf.png)

image.png

当链路状态更新的太快并且不断变化的时候，假设我们发出一个分组，结果还没到目的地，路由表就更新了，然后这个数据报就一直在路由间切换，最后由于ttl到0，直接丢弃。这就是震荡现象。

# 距离向量(Distance Vector)路由算法



![img](https://upload-images.jianshu.io/upload_images/1234352-91fa22cc07f0ab31.png)

image.png



![img](https://upload-images.jianshu.io/upload_images/1234352-9ecfce52d6bd8763.png)

image.png

重点：结点获得最短路径的下一跳, 该信息用于转发表中！

核心思想:

- 每个结点不定时地将其自身的DV估计发送给其邻居
- 当x接收到邻居的新的DV估计时， 即依据B-F更新其自身的距离向量估计：



![img](https://upload-images.jianshu.io/upload_images/1234352-5b426d39ad5c2bff.png)

image.png

Dx(y)将最终收敛于实际的最小费用 dx(y)

异步迭代:

- 引发每次局部迭代的因素
- 局部链路费用改变
- 来自邻居的DV更新

分布式:

- 每个结点只当DV变化时才通告给邻居
- 邻居在必要时（其DV更新后发生改变）再通告它们的邻居



![img](https://upload-images.jianshu.io/upload_images/1234352-5b05d5ab9981a609.png)

image.png

## 距离向量路由算法：举例



![img](https://upload-images.jianshu.io/upload_images/1234352-b3c54ae919fe4113.png)

image.png



![img](https://upload-images.jianshu.io/upload_images/1234352-128e51633d0561c5.png)

image.png

如果链路发生变化，距离向量节点会怎么样呢？



![img](https://upload-images.jianshu.io/upload_images/1234352-3bea61354428f743.png)

image.png

链路费用变化:

- 结点检测本地链路费用变化
- 更新路由信息，重新计算距离向量
- 如果DV改变，通告所有邻居

交换过程

- t0 : y检测到链路费用改变 ，更新DV，通告其邻居.
- t1 : z收到y的DV更新，更新其距离向量表，计算到达x的最新最小费用，更新其DV，并发送给其所有邻居.
- t2 : y收到z的DV更新， 更新其距离向量表，重新计算y的DV，未发生改变，不再向z发送DV.

“好消息传播快！ ”
 “坏消息会怎么样呢？ ”
 如果是坏消息，很可能就会出现无穷计数的问题：



![img](https://upload-images.jianshu.io/upload_images/1234352-c91226605f50df2c.png)

image.png



![img](https:////upload-images.jianshu.io/upload_images/1234352-54986c8006904ad7.png?imageMogr2/auto-orient/strip|imageView2/2/w/492/format/webp)

image.png

我们发现 **坏消息传播慢！—“无穷计数(count to infinity)”问题！**

## 无穷计数问题的解决方法

### 毒性逆转(poisoned reverse):

如果一个结点(e.g. Z)到达某目的(e.g.X)的最小费用路径是通过某个邻居(e.g.Y)，则
 通告给该邻居结点到达该目的的距离为无穷大



![img](https://upload-images.jianshu.io/upload_images/1234352-44118bb7dc4551b3.png)

image.png

毒性逆转能否彻底解决无穷计数问题？
 显然是不行的，如果过于复杂的网络，我们发现毒性逆转也需要经过很多的步骤。

### 定义最大度量(maximum metric)

定义一个最大的有效费用值，如15跳步， 16跳步表示∞



![img](https://upload-images.jianshu.io/upload_images/1234352-1f316e098d7005b6.png)

image.png

# 层次路由

我们前面的算法是将网络抽象成一张图，但实际上，网络都是很大的，节点数量远超过我们想象，如果我们单纯的使用以上的算法显然是不可行的。

将任意规模网络抽象为一个图计算路由-过于理想化

- 标识所有路由器
- “扁平”网络
   ——在实际网络（尤其是大规模网络）中， 不可行！

网络规模： 考虑6亿目的结点的网络

- 路由表几乎无法存储！
- 路由计算过程的信息（ e.g. 链路状态分组、DV）交换量巨大，会淹没链路！

另一方面，就是网络管理自治的问题，不同的网络可以采取不同的方法进行路由。
 管理自治：

- 每个网络的管理可能都期望自主控制其网内的路由
- 互联网(internet) = 网络之网络(network of networks)

层次路由就是解决这样的问题，和网络领域中的问题是一样，继续抽象出一层网络。
 聚合路由器为一个区域：自治系统AS(autonomous systems)
 然后再把自治系统看成节点进行路由，对于自治系统内就采取自己的路由方法。这就是抽象成了两层。

同一AS内的路由器运行相同的路由协议(算法)

- 自治系统内部路由协议(“ intra-AS” routing protocol)
- 不同自治系统内的路由器可以运行不同的AS内部路由协议

网关路由器(gateway router):

- 位于AS“边缘”
- 通过链路连接其他AS的网关路由器



![img](https://upload-images.jianshu.io/upload_images/1234352-27732fb953907b97.png)

image.png

转发表由AS内部路由算法与AS间路由算法共同配置

- AS内部路由算法设置AS内部目的网络路由入口(entries)
- AS内部路由算法与AS间路由算法共同设置AS外部目的网络路由入口

假设AS1内某路由器收到一个目的地址在AS1之外的数据报:
 路由器应该将该数据报转发给哪个网关路由器呢？

AS1必须:
 1.学习到哪些目的网络可以通过AS2到达，哪些可以通过AS3到达
 2.将这些网络可达性信息传播给AS1内部路由器

以上这些都是





![img](https://upload-images.jianshu.io/upload_images/1234352-7634ae012e22ea5f.png)

image.png

# 例: 路由器1d的转发表设置



![img](https://upload-images.jianshu.io/upload_images/1234352-f0a3eba9be55973c.png)

image.png

假设AS1学习到(通过AS间路由协议)：子网x可以通过AS3 (网关 1c)到达，但不能通过AS2到达，AS间路由协议向所有内部路由器传播该可达性信息

为了配置转发表，路由器1d必须确定应该将去往子网x的数据报转发给哪个网关？这个任务也是由AS间路由协议完成!

- 假设AS1通过AS间路由协议学习到：子网x通过AS3和AS2均可到达
- 为了配置转发表，路由器1d必须确定应该将去往子网x的数据报转发给哪个网关？
- 这个任务也是由AS间路由协议完成!
- 热土豆路由: 将分组发送给最近的网关路由器.



![img](https://upload-images.jianshu.io/upload_images/1234352-811011a4f843e9fd.png)

image.png