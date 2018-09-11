# 创建与配置云物理服务器

## 创建云物理服务器

1、 点击京东云官网产品页面中的“立即购买”按钮，跳转到云物理服务器的控制台页面。（已实名验证的条件下）

2、 选择地域和可用区，点击“创建”按钮，跳转到创建页面。

![创建页面](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS011.png)

## 配置云物理服务器

**1、 配置地域与可用区。**

![配置地域与可用区](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS012.png)

**2、 配置主机规格。**
参考[产品规格](../Introduction/Specification.md)。

![主机规格](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS013.png)

**3、 选取镜像。**

例如，现阶段支持“标准镜像”和“标准镜像+应用”两种镜像类型。
其中“标准镜像”支持CentOS7.2和6.6，Ubuntu支持16.04和14.04；“标准镜像+应用”支持CentOS7.2和CentOS6.6下的Nginx、MySQL和RabbitMQ三个应用。

![镜像选择](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS014.png)

**4、 配置存储。**

选取系统盘和数据盘的RAID模式。
（说明：某些机型的系统盘或数据盘RAID模式是固定的，请根据实际情况做选择。）

![配置存储](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS015.png)

**5. 配置网络**

内网网卡和公网网卡均为万兆网卡。京东云数据中心底层数据网络为万兆，保证内网通信质量。京东云提供高质量的BGP网络，可享受极速带宽体验。用户可调节公网IP带宽。

**公网**：主机必须且只能绑定一个公网IP。公网IP由系统自动分配。用户不可以修改公网IP。创建时不展示公网IP地址。创建后在列表页和详情页展示公网IP地址。公网1-200Mbps，具体操作步骤参见[调整公网带宽](../Operation-Guide/Adjust-Public-Network-Bandwidth/Description.md)章节。

**内部网络**：基础网络模式下，用户只有第一次配置网络的时候可以选择内网CIDR地址段。后续创建的云物理服务器将使用第一次配置的内网CIDR地址段。

**防火墙**：操作系统安装完成后，系统对外网网络只开放IN方向的22端口。操作系统安装成功后，用户可自行登录操作系统更改iptable设置。详情请参考[防火墙设置操作指南](../Operation-Guide/Network-And-Security/Steps.md)。

![配置网络](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS016.png)

**公网带宽**：基础网络模式下，用户可选择1-200Mbps的公网带宽速率。公网IP和云物理服务器带宽绑定。

![配置网络](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS017.png)

**6、 配置服务器基本信息**：
配置服务器名称、描述、操作系统密码

![配置服务器](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS018.png)

**7、 配置购买时长**
购买时长1-9个月、1、2、3年。长期购买有优惠，详情参见购买页面。

![配置购买时长](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS019.png)

**8、 点击“立即购买”按钮。**
跳转到订单确认页。

按照京东云统一的订单计费流程支付成功后，跳转回控制台列表页面。
