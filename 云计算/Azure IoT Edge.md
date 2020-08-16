本文主要介绍：

\1. 为什么需要IoT Edge？

2.什么是Azure IoT Edge

3.Azure IoT Edge 组成

4.相关的产品

 

# 视频讲解：

您可以观看B站视频：https://www.bilibili.com/video/av90945940/

或在本站观看视频：

 

[azure-iot-edge-overview.mp4](https://www.yuque.com/seanyu/azure/iot-hub-direct-method#yZMVA)

 

 

 

# 图文介绍：

### 1. 为什么需要IoT Edge？

 

场景1. 网络状况不好

 

地下停车场，通常没有信号，通过Lora 网关等方式将数据汇总至一处（边缘设备），然后上报云端；

 

场景2. 终端能力不足，全部云端实现又成本高或难以实现

 

视频监控场景，突然增加了某个需求，比如时下的戴口罩监控，本地监控摄像头没有这个AI能力，视频数据全部上云分析成本太高，此时可以在一个小区或一个商场布置一台网关（边缘设备），网关本地完成AI分析计算，将结果汇总于云端或通过云端发起报警；

 

场景3. 时延要求严格

 

很多工业场景，要求时控制指令要求必须在短时间内完成，而工厂距离公有云数据中心的物理距离决定了时延太长；

 

其他场景： 

 

传感器数十万甚至更多，产生大量垃圾数据，直接上云，会导致很多垃圾数据一起上云，需要在本地先过滤；

设备通过2/3/4G网络上传数据，全部到云端，流量费用很高；

 

### 2.什么是Azure IoT Edge

 

Azure IoT Edge 是基于Azure IoT Hub构建的 IoT 服务。

IoT Edge能够将部分工作负荷移至边缘，设备将消息发送到云所花费的时间可以更少，并且设备可以对状态更改更快地做出响应。

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4ubmxhcmsuY29tL3l1cXVlLzAvMjAyMC9wbmcvNzQxNTQwLzE1ODI1NDU0NjMwNDQtMDRlMjZjNTAtZDg2MS00M2M2LThiNDItNzg4YzFhN2RjYzc4LnBuZw?x-oss-process=image/format,png)

### 3.Azure IoT Edge 组成

 

Azure IoT Edge是一组软件服务，需要运行在特定的硬件设备上，通常该硬件设备可以是Widows/Linux的设备，如果要处理的数据不多，可以使用 Raspberry Pi 3或更小的设备；如果要运行资源密集型工作负荷，请使用工业服务器。

Azure IoT Edge 包含三个组件：

- **IoT Edge modules**是容器，可以运行 Azure 服务、或者你自己的代码，IoT Edge Runtime包含Moby引擎。
- **IoT Edge runtime**在每个 IoT Edge 设备上运行，并管理部署到每个设备的模块。
- **Cloud-based interface**可以通过基于云的界面远程监视和管理 IoT Edge 设备。

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4ubmxhcmsuY29tL3l1cXVlLzAvMjAyMC9wbmcvNzQxNTQwLzE1ODI1NDU0NjM5MTQtYjIxM2EzOTUtYTk5Zi00MzdjLTgxZjMtYzczZTIyMzA2YTA2LnBuZw?x-oss-process=image/format,png)

 

IoT Edge Runtime:

Azure IoT Edge 运行时允许在 IoT Edge 设备上使用自定义逻辑和云逻辑。 运行时位于 IoT Edge 设备上，并执行管理和通信操作。 该运行时执行多个功能：

- 在设备上安装和更新工作负荷（module）。
- 维护设备上的 Azure IoT Edge 安全标准。
- 确保 IoT Edge 模块（module）始终运行。
- 将模块运行状况报告给云以进行远程监控。
- 管理下游叶设备与 IoT Edge 设备之间、IoT Edge 设备上的模块之间以及 IoT Edge 设备与云之间的通信。

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4ubmxhcmsuY29tL3l1cXVlLzAvMjAyMC9wbmcvNzQxNTQwLzE1ODI1NDU0NjMxMjAtZDUyZTU3NjAtYWE0My00ZWViLWFlZWMtYjY3NmM4NjFjNWNlLnBuZw?x-oss-process=image/format,png)

**IoT Edge agent** 管理IoT Edge设备上的模块（包括IoT Edge Hub） 

**IoT Edge hub** 处理模块（Module）之间以及设备和IoT Hub之间的通信

**IoT Edge security daemon** 安全守护程序 ，由IoT Hub Agent启动，负责监控Modules正常运行