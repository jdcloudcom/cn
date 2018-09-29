## 配置云物理服务器

- 配置地域与可用区

- 配置主机规格：
参考[产品规格](../Introduction/Specifications.md)。

- 选取镜像

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;例如，现阶段支持“标准镜像”和“标准镜像+应用”两种镜像类型。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;其中“标准镜像”支持CentOS7.1、7.2、7.5和6.6，Ubuntu16.04和14.04；“标准镜像+应用”支持CentOS7.2和CentOS6.6下的Nginx、MySQL和RabbitMQ三个应用。

- 配置存储：

选取系统盘和数据盘的RAID模式。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（说明：某些机型的系统盘或数据盘RAID模式是固定的，请根据实际情况做选择。）

- 配置网络

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **内部网络** ：基础网络模式下，用户只有第一次配置网络的时候可以选择内网CIDR地址段。后续创建的云物理服务器将使用第一次配置的内网CIDR地址段。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **防火墙** ：操作系统安装完成后，系统对外网网络只开放IN方向的22端口。操作系统安装成功后，用户可自行登录操作系统更改iptable设置。详情请参考防火墙设置操作指南。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **公网带宽** ：基础网络模式下，用户可选择1-200Mbps的公网带宽速率。公网IP和云物理服务器带宽绑定。

- 配置服务器基本信息：
配置服务器名称、描述、操作系统密码。

- 配置购买时长：
购买时长1-9个月、1、2、3年。

- 点击“立即购买”按钮，跳转到订单确认页

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;按照京东云统一的订单计费流程支付成功后，跳转回控制台列表页面。
