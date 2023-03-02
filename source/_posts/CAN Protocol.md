---
title: CAN 通信协议（Vector）
date: 2023-02-22 04:35:16
tags: 
	- "CAN Protocol"
	- "教程"
top_img: https://cdn.chrelyonly.cf/gh/Shenyan-Wu/BlogImages/img/subghost.jpeg
cover: https://cdn.chrelyonly.cf/gh/Shenyan-Wu/BlogImages/img/CAN%20Controller%20title.png
---
# 概述

## CAN学习模块

### 目标群体

该在线学习模块适用于所有希望更好地了解CAN通信技术的人员。

### Vector培训课程

该在线学习模块还适用于所有计划参加Vector培训课程的人员。在对数据通信有一定程度的了解之后，您将更容易接受绝大多数Vector培训课程。

### 相关信息

##### 学习目标

- 了解[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)中的数据通信

##### 要求

- 电子学的基础知识
- [动因](https://elearning.vector.com/mod/page/view.php?id=4810)和时间

##### 范围

- 37个学习单元

##### 学习用时

- 每个学习单元10分钟

### 技术文章

[Reliable data exchange in the automobile with CAN](https://vector-academy.com/portal/medien/cmc/press/PTR/SerialBusSystems_Part2_ElektronikAutomotive_200612_PressArticle_EN.pdf)

[Ways to transition from classic CAN to the improved CAN FD](https://vector.com/portal/medien/cmc/press/Vector/CAN_FD_ElektronikAutomotive_201304_PressArticle_EN.pdf)

### **版权声明**

详情查看Vector培训官网 -《[版权声明](https://vector-academy.com/vi_training_copyright_cn.html)》

# 介绍

## CAN的推动因素

### 电子化

汽车近年来的发展呈现出以电子化为主的特点。电子化的主要原因是由于当前用户对汽车的需求一直在不断增长，以及日益严格的汽车排放法规。另一个因素是全球化，全球化加剧了竞争和成本压力，直接导致创新压力不断增加。

### 数据传输

起初，独立运行的ECU足以实现电子功能。但工程师们很快就意识到，ECU彼此协调工作可以极大地增强车辆功能。最初，ECU之间数据交换是以传统方式实现的，即为每一个传输信号分配一个物理通信通道。

### 串行通信

然而，大量的布线也只能实现有限的数据交换。唯一可以解决这一难题的方法是通过单个通信通道（总线）进行串行位数据交换。因此，需要设计适合汽车需求的串行通信系统。

### 基于CAN的安全数据传输

上世纪八十年代初，Bosch开发一种新的串行通信系统，即CAN。即使在今天，CAN汽车动力系统、底盘和舒适系统的ECU网络中发挥着重要作用。最重要的是，CAN具有数据传输非常可靠的特点，可以满足应用领域的实时要求。

### 化繁为简

自引入CAN后，汽车中的复杂线束（通常存在多种变体）已成为过去。CAN不仅可以简化项目规划和实施，还可以降低布线重量和空间要求。

<div style="text-align: center">
<iframe height=424px width=670px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12184/mod_page/content/5/CAN_1.1_GRA_Networking_EN.html'></iframe></div>


## 标准化

### CAN协议（CAN protocol）

从1994年开始，ISO启动CAN技术标准化工作，并最终形成4份标准规范。其中，ISO 11898-1描述了CAN协议。除了数据通信的参考模型，CAN协议仅包括数据链路层（介质访问控制子层MAC -Medium Access Control和逻辑链路控制子层LLC - Logical Link Control）和物理层（物理信号PLS - Physical Signaling）。

### [CAN控制器](https://elearning.vector.com/mod/page/view.php?id=4814)（CAN Controller）

CAN协议是基于硬件实现的。目前有多种不同的CAN控制器，其唯一区别在于对CAN报文的处理方式，具体体现在对象层中：具有对象存储的CAN控制器（即完整CAN控制器-Full CAN Controller）与不具有对象存储的CAN控制器（即基础CAN控制器-Basic CAN Controller）。

### 高速CAN（CAN High Speed）和低速CAN（CAN Low Speed）

ISO 11898-2和ISO 11898-3介绍了数据通信参考模型的两个子层：PMA（Physical Medium Attachment，物理介质适配层）和PMS（Physical Medium Specification，物理介质规范）。它们描述了两种不同的CAN物理层：高速CAN物理层和低速CAN物理层，主要区别在于对总线电平和数据传输速率（波特率）的定义。

### 波特率

ISO 11898-3规定最大的波特率为125 kbit/s，主要用于汽车的舒适系统领域。ISO 11898-2规定最大波特率为1 Mbit/s，主要用于汽车的动力系统和底盘系统领域。
ISO 11898-3规定最大的波特率为125 kbit/s，主要用于汽车的舒适系统领域。ISO 11898-2规定最大波特率为1 Mbit/s，主要用于汽车的动力系统和底盘系统领域。

### 事件驱动通信

ISO 11898-1定义了事件驱动通信。总线负载较高可能会导致延迟，对于优先级较低的CAN报文来说尤其如此。若要确保在CAN网络中实现确定性通信，可以使用ISO 11898-4。ISO 11898-4是数据链路层的扩展，为CAN网络增加了时间触发的通信选项。

### ISO/OSI参考模型

图“Standard and Implementation”显示了数据通信的ISO/OSI参考模型、CAN技术规范（CAN standard）及其实现之间的关系。

<div style="text-align: center">
<iframe height=607px width=705px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12185/mod_page/content/5/CAN_1.2_GRA_StandardImplementation_EN.html'></iframe></div>

# CAN通信

## CAN网络

### 结构

CAN网络由若干个经物理传输介质（[CAN总线](https://elearning.vector.com/mod/page/view.php?id=4816)-CAN Bus）连接的CAN节点组成。实际上，CAN网络通常采用线性拓扑结构，每个ECU经CAN接口连接到总线。也有少数CAN网络采用被动星形拓扑。

### 物理层

非屏蔽[双绞线](https://elearning.vector.com/mod/page/view.php?id=4831)（UTP，Unshielded Twisted Pair）是传输对称信号时最常用的物理传输介质。通常，UTP的线横截面介于0.34 mm2 和0.6 mm2 之间。线路电阻应小于60 mΩ。

### 边界条件

在最高传输速率1Mbit/s的情况下，允许的最大长度是40米。在CAN网络的末端，总线[终端](https://elearning.vector.com/mod/page/view.php?id=4832)电阻（termination resistor）有助于抑制信号反射现象。ISO 11898规定CAN节点的最大数量为32。

<div style="text-align: center">
<iframe height=401px width=615px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12186/mod_page/content/8/CAN_2.1_GRA_CANNetwork1_EN.html'></iframe></div>

## CAN节点

### 电子化

随着汽车电子化程度的提高，软件的数量和复杂度也在迅速增长。一些豪华汽车已经拥有1000多种软件功能，多条总线系统，以及70多个ECU。在[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)中执行任务的ECU称为CAN节点。

### 复杂度不断升高

在ECU联网的初期，一个简单的CAN驱动程序（该驱动程序为应用程序提供与硬件无关的简单接口）、一个[CAN控制器](https://elearning.vector.com/mod/page/view.php?id=4814)和一个[CAN收发器](https://elearning.vector.com/mod/page/view.php?id=4815)（CAN transceiver）足以实现CAN接口。如今，ECU网络离不开操作系统、网络管理和诊断功能。同时，软件已变得极其复杂，因此有必要对ECU基础软件进行[标准化](https://elearning.vector.com/mod/page/view.php?id=4811)。

### 软件协调

标准统一的软件可减少开发工作并简化维护工作，还有助于提高重复使用率，并且有助于增强不同车辆平台之间以及OEM和供应商之间的软件组件的互换性。

### **AUTOSAR**

AUTOSAR（AUTomotive Open System ARchiteture，汽车开放系统架构）为ECU软件提供了参考架构，其核心是AUTOSAR实时运行环境（RTE），负责将网络与应用程序的软件组件完全分离。AUTOSAR以基础软件的形式为软件组件提供统一的服务，从低到高分别为：微控制器抽象层、ECU抽象层、服务层。

### CAN节点结构

“CAN Node”图描述了新式CAN节点的结构。最值得关注的是“通信服务”领域。AUTOSAR COM（通信）提供标准通信服务、诊断服务（诊断COM管理器）和网络管理服务（通用NM/CAN NM）。PDU路由器（PDU：协议数据单元）处理各个通信层之间的内部节点通信，并协调AUTOSAR COM、诊断COM管理器和CAN TP（传输协议）之间的通信。

<div style="text-align: center; transform-origin: top left; transform: scale(0.96);">
<iframe height=756px width=815px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12187/mod_page/content/5/CAN_2.2_GRA_CANNode_EN.html'></iframe></div>


## CAN控制器

### CAN接口

ECU需要CAN接口才能参与CAN通信。CAN接口由CAN控制器和CAN收发器组成。CAN控制器执行CAN协议规定的通信功能，从而大大减轻了主机的负担。

### [CAN收发器](https://elearning.vector.com/mod/page/view.php?id=4815)

[CAN收发器](https://elearning.vector.com/mod/page/view.php?id=4815)将CAN控制器连接到物理传输介质。通常，控制器和收发器之间采用光耦隔离或磁耦隔离，因此尽管CAN总线上的过电压可能会损坏CAN收发器，但CAN控制器和底层主机仍可受到保护。

### 发送/接收

在CAN网络中，[CAN节点](https://elearning.vector.com/mod/page/view.php?id=4813)的不同之处在于每个节点发送或接收的CAN报文的数量。发送和接收的频率也存在很大差异。例如，一个CAN节点可能要接收五条不同的CAN报文，且每隔10毫秒接收一条，而另一个CAN节点只需每隔100毫秒接收一条CAN报文。这些明显的差异导致产生了两种基本的CAN控制器架构：完整CAN控制器和基础CAN控制器。

### 集成

不论CAN控制器类型如何，CAN控制器都可集成在微控制器中，也可以作为独立的芯片存在（如图所示）。在这种情况下，微控制器会将CAN控制器视为存储芯片。虽然独立CAN控制器更加灵活，但集成CAN控制器具有所需空间更少的优势，并且微控制器和CAN控制器之间的通信更快、更可靠。

<div style="text-align: center">
<iframe height=435px width=606px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12188/mod_page/content/7/CAN_2.3_GRA_CANNetwork2_EN.html'></iframe></div>

## CAN收发器

### 总线连接

以前，[CAN控制器](https://elearning.vector.com/mod/page/view.php?id=4814)经常通过离散电路连接到通信介质（[CAN总线](https://elearning.vector.com/mod/page/view.php?id=4816)）。但现在，CAN收发器可以处理总线连接。CAN收发器有两个总线引脚：一个用于连接CAN高信号线（CANH），另一个用于连接CAN低信号线（CANL）。这是因为CAN采用对称的物理信号传输以满足电磁兼容性，而且CAN网络中的物理传输介质是由两根线（非屏蔽[双绞线](https://elearning.vector.com/mod/page/view.php?id=4831)）构成。

<div style="text-align: center">
<iframe height=435px width=606px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12189/mod_page/content/7/CAN_2.3_GRA_CANNetwork2_EN.html'></iframe></div>

### 高/低速率

通常，高速CAN收发器和低速CAN收发器的物理电平不同，支持的数据传输速率也不同。高速CAN收发器支持的波特率高达1 Mbit/s。低速CAN收发器支持的波特率最高仅为125 kbit/s。但低速CAN收发器可确保总线接口的容错布局（例如，两条通信线路之中的某一条故障不会导致总体通信故障）。

### 收发器布局

“CAN Transceiver Layout”图显示了高速CAN收发器的基本布局。两个输出晶体管都处于截止状态时，CANH和CANL均具有相同的电位（0.5*Vcc），且差分电压为零。两个晶体管导通时会在CANH和CANL之间产生一个随负载电阻变化的差分电压。根据ISO 11898-2，该差分应为2V。因此，会产生约35 mA的电流。

<div style="text-align: center">
<iframe height=391px width=426px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12189/mod_page/content/7/CAN_2.4_GRA_Transceiver_EN.html'></iframe></div>

### 抗噪能力

通常，CAN收发器的电磁辐射极低且共模工作范围广，具有较高的抗噪能力。此外，目前的CAN收发器可提供高达8 kV的ESD（Electro-Static discharge，防静电）保护。尽管CAN收发器在某些应用领域中具有很高的共模抑制，但在输出附近插入共模扼流圈（CMC）仍有助于进一步减少辐射。

<div style="text-align: center">
<iframe height=365px width=465px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12189/mod_page/content/7/CAN_2.4_GRA_BusInterfaceWithCMC_EN.html'></iframe></div>

### 限制

ISO 11898中规定CAN节点的最大数量为32。实际上，[CAN节点](https://elearning.vector.com/mod/page/view.php?id=4813)的最大数量在很大程度上取决于所使用的CAN收发器的性能以及CAN网络是高速还是低速。例如，如果在高速CAN网络中使用TJA1050高速CAN收发器，则在一个CAN网络中最多可以连接110个CAN节点。

## CAN总线

### 差分信号（Differential signals）

[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)中的物理信号基于差分信号进行传输，有效地消除发动机、点火系统和开关触点引起的干扰电压所造成的负面影响。因此，传输介质（CAN总线）由两条线路构成：CAN高信号线（CANH）和CAN低信号线（CANL）。

### [双绞线](https://elearning.vector.com/mod/page/view.php?id=4831)

将两条导线绞成一股可显著减小磁场。因此，在实践中[双绞线](https://elearning.vector.com/mod/page/view.php?id=4831)通常用作物理传输介质。

### 总线[终端](https://elearning.vector.com/mod/page/view.php?id=4832)

由于信号传播速度有限，反射现象的影响会随着波特率提高和总线延长而增加。使用[终端](https://elearning.vector.com/mod/page/view.php?id=4832)电阻连接通信通道的两端（模拟传输介质的电特性）可防止在高速CAN网络中发生反射。

<div style="text-align: center">
<iframe height=435px width=605px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12190/mod_page/content/6/CAN_2.5_GRA_CANNetwork3_EN.html'></iframe></div>

总线[终端](https://elearning.vector.com/mod/page/view.php?id=4832)电阻的关键参数是导线的特性阻抗。ISO11898-2（高速CAN）规定[终端](https://elearning.vector.com/mod/page/view.php?id=4832)电阻是120欧姆，但ISO11898-3（低速CAN）未规定任何总线[终端](https://elearning.vector.com/mod/page/view.php?id=4832)电阻，因为它的最大速率仅为125kbit/s。

## CAN总线电平

### 总线连接

[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)中的物理信号基于差分信号进行传输，具体的差分电压取决于所使用的总线接口。高速CAN总线接口（ISO 11898-2）和低速CAN总线接口（ISO 11898-3）有所不同。

### 电压等级

在ISO 11898-2中，逻辑“1”对应差分电压0V，逻辑“0”对应差分电压2V。高速CAN收发器将超过0.9V的差分电压当做共模工作范围（通常为-12V到12V之间）内的显性（dominant）电平。

低于0.5V的差分电压被当做隐性（recessive）电平。磁滞电路提高了抵抗干扰电压的能力。在ISO 11898-3中，逻辑“1”对应差分电压-5V，逻辑“0”对应差分电压2V。

“High-Speed CAN Bus Levels”图和“Low-Speed CAN Bus Levels”图说明了不同CAN总线上的电压关系。

<div style="text-align: center">
<iframe height=370px width=420px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12191/mod_page/content/6/CAN_2.6_GRA_HighSpeedBusLevels_EN.html'></iframe>
<iframe height=370px width=420px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12191/mod_page/content/6/CAN_2.6_GRA_LowSpeedBusLevels_EN.html'></iframe>
</div>

## CAN总线逻辑

### 显性/隐性

在CAN网络中实现通信顺畅（尤其是总线访问、故障指示和应答）的基本前提是总线显性电平和总线隐性电平之间存在明显差别。总线显性电平对应于逻辑“0”，总线隐性电平对应于逻辑“1”。

显性电平优先级高于隐性电平。当不同CAN节点同时发送显性和隐性总线电平时，[CAN总线](https://elearning.vector.com/mod/page/view.php?id=4816)将呈现显性总线电平。只有当所有CAN节点都发送隐性电平时，[CAN总线](https://elearning.vector.com/mod/page/view.php?id=4816)才呈现隐性总线电平。

### 与逻辑

从逻辑上说，上述行为是与逻辑。从物理上讲，与逻辑由集电极开路电路实现。通过“Bus Logic”图可以了解CAN网络的线与（wired-AND）逻辑。

<div style="text-align: center">
<iframe height=550px width=700px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12192/mod_page/content/7/CAN_2.7_IGR_BusLogic_EN.html'></iframe></div>

## 通信原理

### 分散化

安全性关键应用（例如动力系统领域的应用）对通信系统的可用性提出了严格的要求。因此，让单个总线节点承担总线分配责任会造成不利影响。该总线节点易受攻击，且如果出现故障，将导致所有通信失败。最佳解决方案是分散总线访问权限，以便每个总线节点都能够访问总线。

### 事件驱动

[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)基于多主架构与总线型拓扑的原因是：每个CAN节点都可以发送报文至CAN总线上。CAN报文的传输不遵循任何预定的时间顺序，而是由事件驱动。

当传输信息时，通信通道才会处于繁忙状态，因此CAN节点可以非常快速地访问总线。理论上，由于可以快速响应异步事件且波特率高达1 Mbit/s，因此在CAN网络中完全可以实现毫秒级的实时数据传输。

### 接收方（receiver）选择[寻址](https://elearning.vector.com/mod/page/view.php?id=4823)（addressing）

在CAN网络中，接收方选择[寻址](https://elearning.vector.com/mod/page/view.php?id=4823)防止总线节点之间产生依赖，从而提高配置的灵活性：CAN报文是广播发送的，网络中所有CAN节点都可以接收到所有CAN报文。每个节点中都有过滤器，可以通过报文的标识符（ID）来筛选实际所需的CAN报文。虽然这会增加开销，但却可以在不修改CAN网络的情况下集成其他CAN节点。

### CAN通信

通过“CAN Communication Principle”动画可以了解如何在CAN网络中进行报文传输，以及如何使用CAN通信矩阵和接收过滤器。请阅读说明，以便充分利用动画中的全部功能。 “Typical CAN Communication”图显示了典型的通信顺序，包括构成CAN网络基础的通信矩阵，以及最终的接收和发送情况。

<div style="width: 785px; height: 499px; text-align: center; overflow: hidden;">
<iframe style="width: 1007px; height: 640px; transform-origin: left top; transform: scale(0.775);" scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12193/mod_page/content/11/CAN_2.8_ANI_CommunicationPrinciple_EN.html'></iframe>
</div>
<br>

<div style="width: 785px; height: 614px; text-align: center; overflow: hidden;">
<iframe height=632px width=804px style="transform-origin: left top; transform: scale(0.97); " scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12193/mod_page/content/11/CAN_2.8_GRA_TypicalCANCommunication_EN.html'></iframe>
</div>

# CAN帧

## 帧类型

### [数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)（Data frame）

为传输用户数据，ISO 11898-1定义了[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)。[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)可以传输的最大有效负载为八个字节，即数据场。除了数据场，[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)还包括执行CAN通信协议所需的许多其他场，包括报文ID、数据长度代码（DLC）、校验场（循环冗余校验序列 - CRC序列）以及应答场（ACK）等。

<div style="text-align: center">
<iframe height=284px width=760px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12194/mod_page/content/6/CAN_3.1_GRA_StandardDataFrame_EN.html'></iframe></div>

### [远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)（Remote frame）

通常ECU会通过[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)主动发送相关数据，但某些情况也可能用到[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)。使用[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)可以从其他任何CAN节点请求用户数据（即[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)）。除了缺少数据场以外，[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)与[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)结构相同。

<div style="text-align: center">
<iframe height=294px width=660px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12194/mod_page/content/6/CAN_3.1_GRA_StandardRemoteFrame_EN.html'></iframe></div>

### 错误帧（Error frame）

错误帧可用于指示通信期间检测到的错误。错误帧将强行中止正在进行的错误数据传输。错误帧的结构与[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)或[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)明显不同，仅由两部分构成：错误标志（error flag）和错误界定符。

<div style="text-align: center">
<iframe height=259px width=508px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12194/mod_page/content/6/CAN_3.1_GRA_ErrorFrame_EN.html'></iframe></div>

## 数据帧

### 段

数据帧是传输用户数据的载体，CAN通信中的主要角色。数据帧由多种不同部分构成，每个部分都会在传输过程中执行一项重要任务。例如：启动并维护ECU节点之间的同步，建立通信矩阵中定义的通信关系，以及传输和保护用户数据。

### SOF（Start of Frame，帧起始）

SOF是数据帧传输的起始位。发送方（sender）会发送一个显性电平作为SOF，由于总线空闲时总线会保持隐性电平，因此SOF发出后会产生一个跳变沿用于整个CAN网络的时间同步。为了在帧传输期间保持与发送方的同步，接收方会在所有隐性电平到显性电平的跳变沿进行是否与发送方保持同步的判断。如果出现偏差，接收方将按照相关相位误差量重新进行同步（重同步）。

### ID和RTR（Remote Transmission Request，远程传输请求位）

SOF之后是标识符（ID），用于区分数据帧的优先级，并根据通信矩阵中定义的收发关系为节点中的接收过滤器提供过滤依据。ID之后是RTR位。发送方将其用于通知接收方帧的类型（数据帧或[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)）。RTR位为显性表示数据帧，隐性则表示[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)。

### IDE（Identifier Extension bit，标识符扩展位）

IDE位用于区分标准格式和扩展格式。标准ID有11位，扩展ID有29位，“Physical Transfer of a Data Frame in Standard Format”图展示了这两种格式。

<div style="text-align: center">
<iframe height=534px width=760px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12195/mod_page/content/15/CAN_3.2_GRA_StandardExtendedDataFrame_EN.html'></iframe></div>

### DLC（Data Length Code，数据长度代码）

DLC表示数据场中的有效负载的字节数。一个数据帧最多可以传输八个字节。

<div style="text-align: center">
<iframe height=530px width=760px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12195/mod_page/content/15/CAN_3.2_GRA_DLCDataField_EN.html'></iframe></div>

### CRC（cyclic redundancy check，循环冗余校验码）和ACK（acknowledge，应答）

校验场使用以界定符（delimiter）为结尾的CRC来保护有效负载。接收方在ACK位做出肯定或否定的应答，ACK位后同样有一位界定符。

### EOF

EOF由7个连续隐性位组成，在此之后，报文传输结束。

### 知识强化

为加深对CAN数据帧的理解，可以查看“Physical Transfer of a Data Frame in Standard Format”图并通过习题进行练习。该图显示了高速CAN网络中标准格式数据帧的物理传输。您可以尝试在布局练习中以正确顺序排列标准格式数据帧的所有部分。

<div style="width: 785px; height: 416px; text-align: center; overflow: hidden;">
<iframe style="width: 840px; height: 445px; transform-origin: left top; transform: scale(0.934);" scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12195/mod_page/content/15/CAN_3.2_GRA_PhysicalTransfer_EN.html'></iframe>
</div>
<br>
<div style="width: 785px; height: 368px; text-align: center; overflow: hidden;">
<iframe style="width: 802px; height: 375px; transform-origin: left top; transform: scale(0.979);" scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12195/mod_page/content/15/CAN_3.2_EXE_DragDropArrangementOfComponents_EN.html'></iframe>
</div>

## 远程帧

### 请求数据

远程帧用于从任何CAN节点请求数据（即[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)）。但是数据传输并不基于请求，而是主要基于信息生产者的自我主动性，因此汽车应用程序中几乎不使用远程帧。远程帧支持标准格式和扩展格式。

### 通过RTR决定

除缺少数据场以外，远程帧与[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)布局相同。[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)和远程帧是以RTR位来区分的。[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)的RTR位为显性，远程帧的RTR位则为隐性。

### 两种帧， 同一ID

原则上，可以为CAN网络中的所有[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)定义远程帧，仅需确保远程帧的标识符与所关联[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)的ID匹配。发送节点通过发送[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)来响应远程帧。

### 远程帧和响应

如果CAN控制器具有对象存储，则该CAN控制器会自动响应远程帧。不具有对象存储的CAN控制器必须先让主机知道远程帧，然后才能发起响应。 在理想情况下，远程帧的请求会立即触发对应[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)的响应。但在请求和响应之间可能会插入具有更高优先级的CAN报文。

<div style="text-align: center">
<iframe height=294px width=660px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12196/mod_page/content/7/CAN_3.1_GRA_StandardRemoteFrame_EN.html'></iframe></div>

## 寻址

### 报文寻址

[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)中的通信基于与内容相关的寻址。[CAN节点](https://elearning.vector.com/mod/page/view.php?id=4813)本身没有ID，但是可以通过ID区分CAN报文。所有CAN节点都会收到总线上广播发送的所有CAN报文。每个接收方都根据需求自行选择CAN报文。这种接收方选择寻址非常灵活，但需要每个接收方对接收到的CAN报文进行过滤（接收过滤）。

### 标准格式和扩展格式

用户可以选择以下两种报文格式：标准格式和扩展格式。两种格式的标识符长度不同。在标准格式中，ID有11位。在扩展格式中，ID有29位。

与标准格式ID相比，扩展格式ID由两个部分构成：基本ID和扩展ID。连接这两个部分的是IDE（Identifier Extension，标识符扩展）位和SRR（Substitute Remote Request，替代远程请求）位。

显性IDE位表示CAN报文为标准格式。隐性IDE位表示CAN报文为扩展格式。在扩展格式中，始终以隐性方式传输的SRR位取代了标准格式的RTR位，并且控制场的前两位（r0和r1）没有实际作用，两者都作为显性位传输。

<div style="text-align: center">
<iframe height=534px width=760px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12197/mod_page/content/6/CAN_3.2_GRA_StandardExtendedDataFrame_EN.html'></iframe></div>

## CRC和应答

### 传输可靠性

串行通信在汽车环境中遇到的最大难题之一就是如何保证极高的传输可靠性。[CAN总线](https://elearning.vector.com/mod/page/view.php?id=4816)中使用的CRC校验是功能最强大的错误检测方法之一。

### CRC序列

CRC方法根据要传输的位（从SOF到数据场结束）和ISO 11898-1定义的生成多项式G（x）计算CRC序列。CRC序列位于数据场之后。接收方会采用同样的方法针对接收到的位（SOF开始到数据场结束）计算CRC并与接收到的报文中的CRC序列进行对比，这样可以非常可靠地检测是否发生了传输错误。（例外情况：当CRC序列本身遭到干扰破坏时）。

### 应答

根据计算后的结果，每个接收节点都会给出应答，与节点是否会过滤该报文无关。接收方的应答不是肯定就是否定。ACK 位中的显性电平表示肯定应答，隐性电平表示否定应答。

### ACK界定符

为了进行[错误跟踪](https://elearning.vector.com/mod/page/view.php?id=4835)，ACK界定符始终以隐性方式传输。由于发送方以隐性方式传输ACK 位和ACK界定符，因此一个肯定应答足以告知发送方报文已正确传输。这就是CAN网络中的应答方法被称为节点肯定应答的原因。

<div style="text-align: center">
<iframe height=453px width=760px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12198/mod_page/content/7/CAN_3.5_GRA_Acknowledgement_EN.html'></iframe></div>

您可通过交互式动画了解CAN网络中的应答。该图假设CAN网络中存在一个发送方和两个肯定应答的接收方。

<div style="text-align: center">
<iframe height=600px width=710px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12198/mod_page/content/7/CAN_3.5_ANI_PositiveAcknowledgement_EN.html'></iframe></div>

### ACK错误和错误标志

在有节点给出肯定应答的情况下，如果还有其他节点给出否定应答，那么这些否定应答不会被其他节点收到。为确保网络范围内的数据一致性，这些节点会在ACK界定符之后发送错误标志。

如果没有一个肯定应答，则ACK位会保持隐性，发送方将检测到ACK错误，并通过发送错误标志来终止正在进行的报文传输。ACK错误表示由发送方引起的错误或总线上没有接收方引起的错误。

## 位填充

### 同步

数据传输正确的基本前提是网络中通信节点之间同步。起始位（帧起始 - SOF）的隐性至显性的跳变沿用于同步CAN报文。之后，重同步（resynchronization）机制用于保持同步，直到报文传输结束为止。

### 重同步

重同步机制基于对隐性至显性跳变沿的评估。位填充机制保证了传输过程中有足够的跳变沿。ISO 11898-1规定，发送方在传输连续5个相同位后必须传输一个相反的位；即使连续5个相同位后本就是一个相反位，也需要添加填充位。

### 位填充区

由于位填充从以SOF的传输为开始，以CRC序列的最后一位的传输为结束，因此在传输包含8个数据字节的标准格式的[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)时，在极限情况下，应有24个填充位。所以，理论上标准格式[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)最多包含132位。

“Bit Stuffing”图可以帮助您迅速理解位填充机制。

<div style="width: 785px; height: 475px; text-align: center; overflow: hidden;">
<iframe style="width: 875px; height: 529px; transform-origin: left top; transform: scale(0.897);" scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12199/mod_page/content/7/CAN_3.6_IGR_BitStuffing_EN.html'></iframe>
</div>

# CAN总线访问

## 总线访问原则

### 所有节点均可访问总线

ISO 11898-1定义了多主架构，以确保高可用性和事件驱动的数据传输。[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)中的每个节点都有权访问CAN总线，无需请求许可，也无需事先与其他CAN节点进行协调。虽然基于事件驱动的总线访问对事件的响应非常快，但也存在风险，即多个CAN节点可能同时访问CAN总线，从而导致CAN总线上出现数据重叠。

### 冲突避免

为保持通信系统的实时能力，ISO 11898-1规定了用于确保无损数据传输的总线访问， CSMA/CA（Carrier Sense Multiple Access with Collision Avoidance，载波监听多路访问/冲突避免）方法。CSMA/CA方法确保希望发送报文的CAN节点在CAN总线可用时才对其进行访问。

### [逐位总线仲裁](https://elearning.vector.com/mod/page/view.php?id=4827)

如果多个节点同时访问总线，基于[逐位总线仲裁](https://elearning.vector.com/mod/page/view.php?id=4827)的CSMA/CA方法可确保发送最高优先级CAN报文的节点获得总线访问权。原则上，CAN报文的优先级越高，在CAN总线上的传输次序越靠前。如果系统设计不佳，可能导致低优先级的CAN报文永远无法发出。

“ Principle of Bus Access”图可以帮助您更好地理解上述内容。图中假设两个CAN节点希望访问正在传输报文的总线。请阅读说明，以便充分利用图片中的全部功能。

<div style="width: 785px; height: 593px; text-align: center; overflow: hidden;">
<iframe style="width: 860px; height: 649px; transform-origin: left top; transform: scale(0.913);" scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12200/mod_page/content/6/CAN_4.1_IGR_PrincipleOfBusAccess_EN.html'></iframe>
</div>

## 逐位总线仲裁

### CSMA/CA

ISO 11898-1定义的总线访问方法的关键是逐位总线仲裁。即使多个节点同时访问总线，也可以防止发生冲突。逐位总线仲裁的原理相对简单。

### 唯一的总线电平

在网络范围内实现同步后，所有希望发送报文的CAN节点会将其CAN报文的ID从最高有效位到最低有效位逐位发送到CAN总线。在此过程中，[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)所基于的线与逻辑可确保在总线上产生清晰明确的总线电平。

### 仲裁逻辑

仲裁逻辑决定CAN节点是否可以继续发送，或者停止发送。“<a id="AccessLogic"> Bus Access Logic</a>”图有助于加深了解逐位总线仲裁的机制。

<div style="width: 785px; height: 587px; text-align: center; overflow: hidden;">
<iframe style="width: 827px; height: 618px; transform-origin: left top; transform: scale(0.949);" scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12201/mod_page/content/5/CAN_4.2_IGR_BusAccessLogic_EN.html'></iframe>
</div>

### 每次一个发送方

仲裁阶段结束时，ID最小的CAN报文的发送节点获得总线访问权。试图发送较低优先级报文的CAN节点切换为接收状态，等待CAN总线再次可用时对其进行访问，以再次尝试发送。“ Bus Access Procedure”图说明了CAN节点在总线访问期间的所有操作。

<div style="text-align: center">
<iframe height=596px width=530px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12201/mod_page/content/5/CAN_4.2_GRA_BusAccessProcedure_EN.html'></iframe></div>

### 知识强化

<a href="#AccessLogic">“逐位总线仲裁”</a>模拟可以帮助您加深对CAN网络中的总线访问的理解。该模拟基于三个希望进行发送的节点所构成的CAN网络。您可以自行设置这三个CAN节点发送的报文ID。

## 优先次序

### 优先级和标识符

CAN报文的优先级对于获得CAN网络的总线访问权具有决定性作用。优先级通过标识符进行编码，标识符从最高有效位到最低有效位逐位传输。

### **标识符值越小=优先级越高**

线与总线逻辑和仲裁逻辑可确保CAN报文的优先级随着标识符值的减小而增加：标识符值越小，CAN报文的优先级越高。“Prioritization”图说明了这种关系。

<div style="text-align: center">
<iframe height=437px width=662px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12202/mod_page/content/9/CAN_4.3_GRA_Prioritization_EN.html'></iframe></div>

### 总线负载率和实时行为

如果总线负载率不太高，这种非破坏性仲裁和优先级控制的随机访问机制将提供公平且非常快速的总线访问。
但必须考虑到总线负载率增加会导致优先级较低的CAN报文的延迟时间变长。这可能会损害CAN通信系统的实时能力。因此，设计系统时应根据CAN报文所传输信号的紧急程度来确定其优先级。

### 典型CAN通信

“ Typical CAN Communication”图可以帮助您理解CAN网络中的通信流程，包括通信矩阵中列出的通信关系以及各时间点发生的事件。

<div style="width: 785px; height: 555px; text-align: center; overflow: hidden;">
<iframe style="width: 870px; height: 623px; transform-origin: left top; transform: scale(0.902);" scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12202/mod_page/content/9/CAN_4.3_IGR_TypicalCANCommunication_EN.html'></iframe>
</div>

### 知识强化

通过“[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)中的总线访问”练习可测试您的知识掌握程度。该练习要求您编排CAN总线上任意[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)和事件组的报文序列。


# CAN数据保护

## 数据保护原则

### 车辆中的数据完整性

可靠的数据传输是实现车辆电子系统的安全性和可靠性的前提。因此，CAN不仅必须满足严格的实时要求，还必须始终提供可靠的数据传输。由于CAN也用于车辆中时间和安全性至关重要的应用，因此对数据完整性的要求极高。

### EMC（Electromagnetic compatibility，电磁兼容）

由于环境对数据传输有干扰作用，所以环境对评估数据完整性至关重要，同样重要的还有串行总线系统抵御干扰的能力。因此，保证可靠的数据传输从物理系统布局开始，其中EMC往往扮演重要角色。

### 潜在错误来源

尽管具有电磁兼容设计和物理数据保护，但仍可能发生传导、电感和电容耦合，从而导致信号衰减和失真。如果再考虑到采样点不同、阈值差异以及节点之间的时钟频率偏差，实现无故障的数据传输是不可能的。

### 最大程度降低错误概率

数据完整性可以看作是数据在传输过程中遭到干扰和破坏的概率与遭到干扰的数据未被检测到的概率的乘积。两种基本策略可以尽量减少出错概率并提高数据完整性：一种策略是通过电磁兼容方式对网络进行布局或采取物理措施来避免损坏数据；另一种策略是通过有效的[逻辑错误检测](https://elearning.vector.com/mod/page/view.php?id=4833)和[逻辑错误处理](https://elearning.vector.com/mod/page/view.php?id=4834)来检测和纠正损坏的数据。“ Principle of Data Protection in the CAN Network”图对此进行了概述。

<div style="text-align: center">
<iframe height=410px width=430px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12203/mod_page/content/4/CAN_5.1_GRA_PrincipleOfDataProtection_EN.html'></iframe></div>

## NRZ编码

### 位编码

避免故障需要处理噪声辐射和敏感性或抗干扰性。位编码对辐射发射具有重大意义。智能设计的位编码有助于显著减少辐射，但必须经常与所需的输送能力进行协调。

### NRZ位编码

NRZ（Non Return to Zero，不归零）位编码被用于CAN。这意味着二进制信号与物理电平的映射关系：逻辑“1”对应高电平，逻辑“0”对应低电平。NRZ编码的特征在于，相同极性的连续位没有电平变化。

<div style="text-align: center">
<iframe height=400px width=556px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12204/mod_page/content/5/CAN_5.2_GRA_NRZCoding_EN.html'></iframe></div>

### 缺少同步

NRZ编码能够实现极高的波特率，同时又可将辐射保持在限制范围内。但NRZ编码不是自同步的，即不具有任何同步属性。如果较长时间内没有发生电平变化，则接收方将不能保持同步。因此使用NRZ编码需要显式同步机制，但这会降低传输效率。

### 用于同步的[位填充](https://elearning.vector.com/mod/page/view.php?id=4825)

在CAN总线中，使用[位填充](https://elearning.vector.com/mod/page/view.php?id=4825)方法作为同步机制：发送方在传输五个相同位后，在位流中插入一个相反的位。曼彻斯特（Manchester）编码没有这种机制，因为它是自同步的。

## 双绞线

### **对称信号传输**

对称信号传输可以有效地避免发动机、点火单元和开关触点等引起的干扰电压的危害。在对称信号传输中，外部噪声对两条线的作用相同。

### **差分结构**

差分结构可用于消除噪声-有用的信号不受影响。对称信号传输需要由两条线构成的物理传输介质（[CAN总线](https://elearning.vector.com/mod/page/view.php?id=4816)），即CAN高信号线（CANH）和CAN低信号线（CANL）。

### 磁场

对于对称信号传输，可以利用导线周围磁场叠加的原理。导线内的电场以及导线周围产生的磁场正好彼此相反。如果导线彼此紧密相邻，则磁场几乎叠加为零，从而消除电磁辐射。绞合两根CAN信号线（双绞线）可确保其紧密相邻。

### 缠绕越密=感应效应越弱

通过绞合导线，不仅可以确保导线紧密相邻，就局部而言，感应效应的极性相反，每根导线上的感应电流是可以相互抵消的，从而可以进一步减弱感应效应。绞合导线将导线回路转变为单独的导体。理论上，每一段导线的磁场方向相反，从而导致感应电压或感应效应相互抵消。

<img src="https://elearning.vector.com/pluginfile.php/12205/mod_page/content/6/CAN_5.3_GRA_TwistedPair_EN.png" id="yui_3_17_2_1_1675675406062_50">

## 终端

### **特性阻抗**

随着波特率的提高，由于信号传播距离有限，[CAN总线](https://elearning.vector.com/mod/page/view.php?id=4816)上会出现反射现象。因此，高速CAN网络中的总线最远两端必须连接120欧姆的电阻。

<div style="text-align: center">
<iframe height=435px width=605px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12206/mod_page/content/5/CAN_2.5_GRA_CANNetwork3_EN.html'></iframe></div>

### 终端电阻（Termination resistor）

[CAN总线](https://elearning.vector.com/mod/page/view.php?id=4816)的末端可以连接分离式总线终端，代替在通信通道的每个末端连接一个总线终端电阻方案。

由两个相同电阻（60欧姆）和一个电容（通常为4.7 nF）构成的分离式总线终端类似于低通滤波器。高频信号转移至地，不会影响直流电压。测量结果表明，这可以提高抗噪能力并减少对外界的电磁干扰。

<div style="text-align: center">
<iframe height=350px width=680px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12206/mod_page/content/5/CAN_5.4_GRA_SplitBusTermination_EN.html'></iframe></div>

## 逻辑错误检测

### 五种错误检测机制

为检测被破坏的报文，CAN协议定义了五种机制：位监控、报文格式监控（格式检查）、位编码监控（填充检查）、应答评估（ACK检查）以及校验场验证（循环冗余校验）。

### 发送方和接收方的任务

位监控和ACK检查由发送方执行。接收方执行格式检查、填充检查和循环冗余校验，这些检测针对总线上的所有报文，不受接收过滤器影响。“Error Detection”图显示了各种错误检测机制所影响的[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)场或[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)场。

<div style="width: 785px; height: 330px; text-align: center; overflow: hidden;">
<iframe style="width: 835px; height: 350px; transform-origin: left top; transform: scale(0.94);" scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12207/mod_page/content/12/CAN_5.5_IGR_ErrorDetection_EN.html'></iframe>
</div>
<br>
<div style="text-align: center">
<iframe height=373px width=680px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12207/mod_page/content/12/CAN_5.5_GRA_ErrorDetection_EN.html'></iframe></div>

### 填充检查（接收方）

填充检查用于检查位流。CAN协议规定发送方传输五个相同位后必须传输相反的位，以便实现同步。如果连续接收到五个以上的相同位，则会出现填充错误。

### 位监控（发送方）

在位监控的框架内，发送方会将发送的位电平与实际的总线电平进行比较。如果发送方检测到两个电平之间存在差异，则会发生位错误。位监控可确保检测到发送方的所有全局错误和所有局部错误。

### 格式检查（接收方）

格式检查用于检查CAN报文的格式。所有CAN报文在某些位置始终呈现相同的位序列，即CRC界定符、ACK界定符和EOF。发送方始终以隐性电平传输这些报文部分。如果接收方在进行格式检查时在其中一个位检测到显性总线电平，则会发生格式错误。

### 循环冗余校验（接收方）

在循环冗余码中，与接收到的[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)或[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)关联的多项式R(x)应是ISO 11898-1指定的生成多项式G(x)的倍数。如果不是，就会产生CRC错误，说明[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)或[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)在传输期间遭到了破坏。

### ACK检查（发送方）

CAN协议中定义的应答机制规定，所有接收方在完成循环冗余校验之后必须立即应答每一个接收的CAN报文。一个肯定应答足以告知发送方，至少一个接收方已正确接收了其发送的CAN报文。如果发送方没有接收到任何肯定应答，则发生了应答错误（ACK错误）。

## 逻辑错误处理

### 数据一致性

为在网络范围内实现数据一致，CAN协议规定，如果有CAN节点检测到了总线错误，则必须通知CAN网络的所有CAN节点。为此，检测到错误的CAN节点会传输由六个显性位构成的错误信号主要（主要错误标志）。该操作故意违反[位填充](https://elearning.vector.com/mod/page/view.php?id=4825)规则，从而产生[位填充](https://elearning.vector.com/mod/page/view.php?id=4825)错误。

### 错误标志

传输错误标志可确保其他所有CAN节点会因为检测到总线错误而发送错误标志（次要错误标志），从而像主要错误标志的发送方一样终止常规数据传输。根据情况，主要和次要错误标志可能会有所重叠。

### 错误界定符

错误标志的传输由错误界定符来终止。错误界定符由八个隐性位构成，取代了常规报文传输的ACK界定符和EOF，连同CAN总线上的强制传输暂停（ITM - 帧间间隔），合计形成11个隐性位（总线空闲标识符）。

<div style="text-align: center">
<iframe height=261px width=508px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12208/mod_page/content/7/CAN_5.6_GRA_ErrorSignaling_EN.html'></iframe></div>

### 处理错误

错误处理由被中断CAN报文传输的发送方完成。在ITM后，发送方会尝试再次传输被中断的CAN报文。“Error Handling”图总结了检测到错误后CAN网络中采取的所有操作。“Bit Monitoring Error”动画以位监控错误为例展示错误处理。由于总线访问是基于优先级的，因此不能保证立即再次进行总线访问。最佳情况下，从错误检测到重新发送（主要错误标志、错误界定符、ITM）需要17个位时间。如果主要和辅助错误标志不存在重叠，则需要23个位时间。如果CAN节点处于被动错误状态，则需要31个位时间。在这种状态下，[CAN节点](https://elearning.vector.com/mod/page/view.php?id=4813)必须等待8个位暂停传输时间，然后才能再次访问CAN总线。

<div style="text-align: center">
<iframe height=322px width=680px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12208/mod_page/content/7/CAN_5.6_GRA_ErrorHandling_EN.html'></iframe></div>
<br>
<div style="width: 785px; height: 507px; text-align: center; overflow: hidden;">
<iframe style="width: 1000px; height: 645px; transform-origin: left top; transform: scale(0.785);" scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12208/mod_page/content/7/CAN_5.6_ANI_BitMonitoringError_EN.html'></iframe>
</div>

## 错误跟踪

### 避免总线拥堵

为在网络范围内确保数据一致，[CAN网络](https://elearning.vector.com/mod/page/view.php?id=4812)中的每个节点都有权终止任何被认为是故障的CAN报文。将正确CAN报文错认为故障的CAN节点同样具有此权利。为防止传输介质发生拥堵，CAN协议规定了错误跟踪，用于确保CAN节点能够区分偶发干扰和持久性干扰。

### TEC和REC

每个CAN控制器都有一个TEC（Transmit Error Counter，发送错误计数器）和一个REC（Receive Error Counter，接收错误计数器）。如果[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)或[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)传输成功，相关的错误计数器将递减（TEC=TEC-1；REC=REC-1）。错误标志的检测和后续传输会导致相关错误计数器根据特定规则递增。对于发送方，适用以下规则：TEC=TEC+8。检测到错误的接收方将其REC递增一个单位（REC=REC+1）。对于引起错误的接收方，适用以下规则：REC=REC+8。

### 主动错误（Error Active）

根据特定的错误计数，[CAN控制器](https://elearning.vector.com/mod/page/view.php?id=4814)可以切换错误状态。[CAN控制器](https://elearning.vector.com/mod/page/view.php?id=4814)启动后将进入“主动错误”正常状态。在该状态下，[CAN控制器](https://elearning.vector.com/mod/page/view.php?id=4814)在检测到错误后发送六个显性位（主动错误标志）。超出限制（TEC>127；REC>127）时，[CAN控制器](https://elearning.vector.com/mod/page/view.php?id=4814)将切换为“被动错误（Error Passive）”状态。

### 被动错误（Error Passive）

处于“被动错误”状态的CAN控制器只能通过发送六个相同的隐性位来指示检测到的错误。这可以防止检测错误的接收方将检测到的错误全局化。此外，发送两个连续的[数据帧](https://elearning.vector.com/mod/page/view.php?id=4821)或[远程帧](https://elearning.vector.com/mod/page/view.php?id=4822)时，处于“被动错误”状态的CAN控制器必须等待“暂停传输时间”（8个位）。

### Bus Off

如果CAN控制器发生故障或错误累积过多，则会进入“Bus Off”状态，[CAN控制器](https://elearning.vector.com/mod/page/view.php?id=4814)与CAN总线断开连接。只能通过软件恢复（强制等待时间为128 x 11位）或通过硬件复位来退出“Bus-Off”状态。

<div style="text-align: center">
<iframe height=520px width=500px  scrolling="no" frameborder="0" src='https://elearning.vector.com/pluginfile.php/12209/mod_page/content/5/CAN_5.7_GRA_ErrorTracking_EN.html'></iframe></div>
