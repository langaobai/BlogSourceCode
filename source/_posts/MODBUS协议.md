title: MODBUS协议
author: LanGaoBai
author_id: defaultAuthorId
language: zh-CN
tags:
  - MODBUS
  - 通信协议
categories:
  - MODBUS
date: 2018-03-09 14:34:00
---
#### 情况介绍

最近公司项目有部分涉及到一个库位灯的通讯，因此我需要对该协议有个具体的了解；

在之前我并没有接触过这个协议甚至不明白这是啥，能用来做啥的。

我们首先对**协议**这个特定的词汇进行深入解读一下，避免一些语文差点的同学搞不清楚；

如果需要对这个汉语有更深入的了解，可以百度一下；

我们这里用自己的话说一下，其实就是方言，例如你说温州话，或者英语，而你也只能听懂这类话，我们因此把这种说温州话或者英语的标准称为协议。

上面我们说了一堆废话，那么从下面开始，我们进入正题；

我们需要与库位灯进行沟通，那么就需要一种方言——*协议*。

就让我们了解下什么是MODBUS协议；

#### 协议简介

**Modbus 是一个请求/应答协议。**

**它已经成为一通用工业标准。有了它，不同厂商生产的控制设备可以连成工业网络，进行集中监控。**

MODBUS协议支持传统的RS-232、RS-422、RS-485和以太网设备。许多工业设备，包括PLC，DCS，智能仪表等都在使用Modbus协议作为他们之间的通讯标准。

MODBUS通讯协议，是1979年由美国Modicon 公司提出的，就是被称为PLC 之父的迪克·莫利先生创造的品牌。

**MODBUS是世界上第一个用于工业现场的总线协议**，可以说，它的出现标志着工业现场从模拟量时代向通讯时代迈进。。

#### 如何定义

既然是协议，那么它究竟如何定义，它的规范又是什么呢？

从程序的角度出发，快速定义：

#### 快速上手

##### 仿真

安装modbus仿真工具[Modbus Slave](http://www.modbustools.com/download.html), 用来模仿一台Modbus协议设备

1.安装完毕之后的界面是这样的：

![安装好之后的样子](\img\articlePicture\ModbusSlaveIcon.png)

2.启动后的界面：

![启动之后的样子](\img\articlePicture\ModbusSlaveLunch.png)

3.选中仿真的设备，然后进行设定，或者鼠标点击按**F8**

![启动之后的样子](\img\articlePicture\ModbusSlaveOperat.png)

4.这里我参考了别人对于Function的理解

4.1 个人理解版本

- 可以读写的布尔类型(0x)
- 只能读的布尔类型(1x)
- 只能读的数字类型(3x)
- 可以读写的数字类型(4x)

4.2 jamod也提供了操作每种不同类型使用不同的类，这里我列个表

|  类型  | 请求类 | 响应类 |
|----------|--------|-------|
| 可以读写的布尔类型(0x) |ReadCoilsRequest | ReadCoilsResponse|
| 只能读的布尔类型(1x)   | ReadInputDiscretesRequest|ReadInputDiscretesResponse|
|只能读的数字类型(3x)|ReadInputRegistersRequest|ReadInputRegistersResponse|
|可以读写的数字类型(4x)|ReadMultipleRegistersRequest |ReadMultipleRegistersResponse|

5.设定成功以后选择上部的菜单<kbd>Connection</kbd>，选择**Modebus TCP/IP**，在**TCP/IP Server**栏进行进行配置，如图

![Modbus Connect](\img\articlePicture\ModbusSlaveConnect.png)

启动之后，红色的No Connection就会消失了；


##### jar包

如果你使用的也是java，好吧，这里仅仅介绍java的，其他另外想办法吧。

可以到maven仓库去下载这个[jamod.jar](http://mvnrepository.com/artifact/net.wimpi/jamod/1.2)

##### java编程部分[^源码]

```java
public class ModbusUtil {
	/**
	* @Title: readDigitalInput 
	* @Description: TODO(只能读的布尔类型(1x)) 
	* @autor hongpeng.zhang
	* @param ip IP地址
	* @param port 端口
	* @param slaveId modbus设备地址
	* @param address 内部寄存器地址，PLC地址
	* @return
	* @throws
	 */
	public static int readDigitalInput(String ip, int port, int slaveId, int address) {}
	
    /**
	* @Title: readInputRegister 
	* @Description: TODO(只能读的数字类型(3x)) 
	* @autor hongpeng.zhang
	* @param ip IP地址
	* @param port 端口
	* @param address 内部寄存器地址，PLC地址
	* @param slaveId modbus设备地址
	* @return
	* @throws
	 */
	public static int readInputRegister(String ip, int port, int slaveId, int address) {}
	
	/**
	* @Title: readDigitalOutput 
	* @Description: TODO(可以读写的布尔类型(0x)) 
	* @param ip IP地址
	* @param port 端口
	* @param slaveId modbus设备地址
	* @param address 内部寄存器地址，PLC地址
	* @return
	* @throws
	 */
	public static int readDigitalOutput(String ip, int port, int slaveId, int address) {}

	/**
	* @Title: readRegister 
	* @Description: TODO(读取可以读写的数字类型(4x)) 
	* @autor hongpeng.zhang
	* @param ip IP地址
	* @param port 端口
	* @param slaveId modbus设备地址
	* @param address 内部寄存器地址，PLC地址
	* @return
	* @throws
	 */
	public static int readRegister(String ip, int port,int slaveId, int address) {}

	/**
	* @Title: writeRegister 
	* @Description: TODO(写入数据到真机，数据类型是RE,用于写到寄存器地址，相应数据，这里需要注意的是，针对的设备必须是可以读写的数字类型，而非另外三种) 
	* @param ip IP地址
	* @param port 端口
	* @param slaveId modbus设备地址
	* @param address 内部寄存器地址，PLC地址
	* @param value 需要设置的值
	* @throws
	 */
	public static void writeRegister(String ip, int port, int slaveId, int address, int value) {}

	/**
	* @Title: writeDigitalOutput 
	* @Description: TODO(写入数据到真机的DO类型的寄存器上面) 
	* @param ip IP地址
	* @param port 端口
	* @param slaveId modbus设备地址
	* @param address 内部寄存器地址，PLC地址
	* @param value 需要设置的值
	* @throws
	 */
	public static void writeDigitalOutput(String ip, int port, int slaveId, int address, int value) {}

```

上面的部分引自**核心代码**部分，需要直接操作的，可以直接找到这个类，我已经对照进行注释了；

内部使用的变量字符都可以对照着模拟仿真对应的设置参数；


[^源码]: 详细的可以从GitHub上下载源代码,具体见文章最后

> 本文中的代码部分，以及代码操作部分引 [Dn9x](https://www.cnblogs.com/Dn9x/p/4298146.html) [GitHub地址](https://github.com/Dn9x/dn-modbus)