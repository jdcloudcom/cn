# CPS到VPC专线通信配置方法



## 一、背景
为了实现云物理服务器（简称CPS）的内网与云主机的VPC内网之间内网互通，更好的满足业务要求，现给出规划和配置CPS内网到云主机VPC内网的专线通信方法。
本文档提到的账户信息，网络环境信息，专线规划表、配置信息都是示例，具体配置时请以实际的信息为准。

## 二、示例网络环境说明

假设：

1、云主机所在的VPC内网网段：192.168.0.0/16，其中某个云主机的内网IP地址： 192.168.0.3/32。

2、云物理服务器CPS的内网网段：10.237.0.0/16，其中某个CPS物理机内网IP地址10.237.0.2/32。

3、云主机和云物理服务器所在的机房区域\机房可用区: 华北北京\北京有孚，云主机和CPS都在相同机房区域、相同可用区

4、云主机的VPC:Xinleitest

5、托管专线：test

6、边界网关: test_gwasa

7、托管通道: test_channel

8、网络拓扑示意图
![网络拓扑示意图](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-001.png)
 
## 三、配置方法

### 3.1 说明

1、假设CPS的网络需要和同一京东云账号下的某个VPC联通，此时按照下文3.2的过程配置即可。

2、假设CPS的网络需要和同一京东云账号下的多个VPC联通，此时首先按照下文3.2的过程完成和其中一个VPC的联通，然后在已经建立的边界网关、托管通道、托管专线的基础上，和其他VPC配置联通，只需增加双向路由，即重复配置方法6.3、6.4和7.3、7.4、7.5的过程。

3、假设CPS的网络需要和多个京东云账号下的多个VPC联通，需要针对每一个VPC所在的京东云账号重复上述1和2的过程，即先打通和其中一个VPC的连接，然后为同账号的其他VPC添加双向路由。

### 3.2 配置方法

#### 1、登陆控制台

通过访问京东云官网https://www.jdcloud.com,点击右上角“登陆”，输入京东云的用户名

![京东账号登录](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-002.png)

![登录控制台](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-003.png)

#### 2、进入专线配置控制台

开始配置云主机VPC内网到CPS内网的专线通信


#### 3、创建托管专线

* 点击左侧导航栏网络—>专线服务—>托管连接—>托管专线—>创建


![创建托管专线1](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-004.png)


* 进入创建页，名称根据可自定义填写，根据云主机或者CPS的机房地域选择托管地域。


![创建托管专线2](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-005.png)

 
* 弹出一个提示框，提示申请信息已经收到，会有专人立即处理申请


![创建托管专线3](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-006.png)


* 创建成功后，自动返回到托管专线的列表页，会看到专线在审核中状态，请等待审核完成。审核后台会有专人审核，如需支持帮助，请电话京东云400-615-55 （7*24小时）。 
 
![创建托管专线4](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-007.png)


* 正在审核时，状态会变成施工中，正在做配置操作


![创建托管专线5](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-008.png)

 
* 审核完成后，状态显示为可用

![创建托管专线6](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-009.png)

 
#### 4、创建边界网关

* 点击左侧导航栏网络—>专线服务-->边界网关—>选择相应的托管区域—>创建

![创建边界网关1](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-010.png)
 
* 选择相应的机房地域，填写网关名称，名称可以自定义

![创建边界网关2](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-011.png)


* 确认边界网关已经创建好。

![创建边界网关3](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-012.png)
 

#### 5、创建托管通道

* 按照规划表的内容创建托管通道，托管通道规划表会发到用户邮箱。

规划表：

| 客户名称        | AS    |  Ctag  |  京东云端IP  |  CPS端IP  |
| :----:         |:----: |:----:  |:----:        |:----:    |
| Jdcloud        | 65001    |  20  |  192.168.0.10/30  |  192.168.0.9/30  |
| Jdcloud        | 65001    |  20  |  192.168.0.14/30  |  192.168.0.13/30  |


* 点击左侧导航栏网络—>专线服务-->托管连接-->托管通道，选择相应的托管区域，点击创建

![创建托管通道1](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-013.png)

* 创建托管通道，利用规划表的信息、托管专线test（第3.6步骤创建的）、边界网关test_gw（第4.3步骤创建的）
 
 ![创建托管通道2](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-014.png)
  
注意：标记红色星号的参数是必须填写。

参数说明：

A、	通道名称：自定义填写，按照方框正下方的要求

B、	托管专线：会自动显示已经创建好的托管专线，如果有多个托管专线，点击下拉箭头选择相应的托管专线名称

C、	边界网关：会自动显示已经创建好的边界网关，如果有多个边界网关，点击下拉箭头选择相应的边界网关名称

D、	Vlanid:填写规划信息表里“Ctag”列的信息

E、	路由方式：默认是BGP路由

F、	BGP ASN：填写规划信息表里“AS”列的信息

G、	BGP密钥：自定义填写，按照方框正下方的要求，最好6位数字或字母以上

H、	路由互联地址：Primary IP 填写规划表第一行的“CPS端IP”、“京东云端IP”；Secondary IP 填写规划表第二行的“CPS端IP”、“京东云端IP”， 注意；规划表的第一行对应于primaryIP ,规划表的第二行对应于SecondaryIP,primary\secondaryIP不能交换填写。

I、	描述：可选，可以填写象征性意义的文字描述，如CPS到VPC专线通信

* 通道创建完成，会处于配置中状态，一下子就自动变为可用状态。
 
 ![创建托管通道3](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-015.png)
 
 ![创建托管通道4](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-016.png)

#### 6、配置边界网关的路由

* 查看VPC名称

 ![配置边界网关的路由1](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-017.png)
  
* 网络—>专线服务—>边界网关—>点击已创建的边界网关
 
 ![配置边界网关的路由2](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-018.png)

* 配置边界网关到VPC的路由策略，点击编辑

目的端：云主机VPC的内网段（192.168.0.0/16)

下一跳类型 ：VPC

下一跳：xinleitest（6.1步骤查看的vpc名称）

 ![配置边界网关的路由3](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-019.png)
 
* 配置边界网关到 cps的路由策略。点击“新增一条”

目的端：cps内网段 10.237.0.0/16

下一跳类型：托管通道

托管通道：test_channel（5.3步骤创建的通道名称）
  
  ![配置边界网关的路由4](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-020.png)

#### 7、配置云主机VPC内网去往CPS内网的路由

* 网络—>私有网络—>子网—>点击创建

 ![配置VPC到CPS内网的路由1](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-021.png)
 
* 机房区域—>私有网络（6.1步骤查看的vpc名称和内网段）—>子网名称（自定义）—>CIDR会自动填充已选择的私有网络（确保掩码位与私有网络的掩码位一致）—>默认路由表。
 
![配置VPC到CPS内网的路由2](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-022.png)
 
![配置VPC到CPS内网的路由3](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-023.png)

* 网络—>私有网络—>路由表，点击默认路由表（7.2步骤创建的路由名称）

![配置VPC到CPS内网的路由4](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-024.png)
 
* 点击路由策略—>点击编辑—>然后在左下方才会显示“新增一条”按钮

![配置VPC到CPS内网的路由5](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-025.png)
 
* 点击“新增一条”，输入信息。

目的端：10.237.0.0/16 ( CPS的内网段)

下一跳类型：边界网关

下一跳：test_gw(4.3步骤创建的边界网关)

![配置VPC到CPS内网的路由6](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-026.png)
 

#### 8、验证CPS到VPC之间的专线通信

* 从云主机 ping CPS的内网IP

![从云主机pingCPS的内网IP1](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-027.png)
 
* 从CPS ping 云主机内网IP

![从云主机pingCPS的内网IP2](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS-VPC-028.png)


