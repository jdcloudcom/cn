# 配置网卡多队列（内测中）

单个vCPU处理网络中断存在瓶颈，您可以通过配置网卡多队列将实例中的网卡中断分散给不同的vCPU处理，提升网络处理性能。

## 支持情况

### 不同镜像支持多队列情况
目前，不同镜像对网卡多队列支持情况不同。详细情况如下：

#### 官方镜像：

* CentOS 6.6/6.8/6.9/7.1/7.2/7.2 NAT Gateway/7.3/7.4支持，6.5不支持；
* Ubuntu 14.04/16.04支持；
* Windows Server暂不支持。

#### 私有镜像：

* 若实例源镜像支持网卡多队列，则基于此事例创建的私有镜像同样支持网卡多队列；
* 若实例源镜像不支持网卡多队列，则基于此事例创建的私有镜像同样不支持网卡多队列。

#### 共享镜像：

共享镜像实际为其他用户的私有镜像共享给您使用，支持情况同私有镜像。

#### 第三方镜像：

暂不支持。

###不同实例规格支持多队列情况
各种实例规格对网卡多队列的支持现状，请参见[实例规格类型](../../Introduction/Instance-Type-Family.md)。

## 操作步骤

对于CentOS 6及Ubuntu系统，若需要使用网卡多队列，实例创建完成后需要登录实例进行配置。CentOS 7系统默认配置当前实例规格支持的最大队列数。
这里以CentOS 6.9为例，介绍配置步骤。

1. [登录实例](../../Getting-Start-Linux/Connect-To-Instance.md)。
2. 查看网卡是否支持多队列。运行命令：
	
	`ethtool -l eth0`
	
3. 设置网卡当前使用多队列。运行命令：

	`ethtool -L eth0 combined x`
	
	x为设置的队列数。
	
4. 对于有多个网卡的用户，可以对多个网卡分别进行设置，只需将上述命令中eth0替换成其他网卡设备名即可。

	```
	[root@test ~]# ethtool -l eth0
	Channel parameters for eth0:
	Pre-set maximums:
	RX:		0
	TX:		0
	Other:		0
	Combined:	4      # 此行代表最多支持4个队列
	Current hardware settings:
	RX:		0
	TX:		0
	Other:		0
	Combined:	1      # 此行代表当前生效1个队列
	[root@test ~]# ethtool -L eth0 combined 4
	```
	
3. 建议开启irqbalance服务，让系统自动调整网卡中断在多个vCPU核上的分配，CentOS 7已默认开启。运行命令：
	
	`systemctl start irqbalance `
	
	




## 相关参考

[登录实例](../../Getting-Start-Linux/Connect-To-Instance.md)


