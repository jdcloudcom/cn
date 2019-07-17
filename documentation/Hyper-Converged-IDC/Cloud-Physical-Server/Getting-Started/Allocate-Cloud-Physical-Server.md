## 配置云物理服务器

- 配置地域与可用区

![配置地域与可用区](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/cn-Create-1RegionAZ.png)

- 配置主机规格：
参考[产品规格](../Introduction/Specifications.md)。

- 选取镜像

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;例如，现阶段支持“标准镜像类型。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;其中“标准镜像”支持CentOS6.6、7.1、7.2和7.5，Ubuntu14.04、16.04和18.04。详细情况参见[镜像使用说明](../Operation-Guide/Image/Description-Image.md)。

![镜像选择](../Image/CPS-create-image.png)


- 配置存储：

选取系统盘和数据盘的RAID模式。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（说明：某些机型的系统盘或数据盘RAID模式是固定的，请根据实际情况做选择，详情参见[产品规格](../Introduction/Specifications.md)。）

![配置存储](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/cn-Create-4Storage.png)

- 配置网络

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **内部网络** ：基础网络模式下，用户只有第一次配置网络的时候可以选择内网CIDR地址段。后续创建的云物理服务器将使用第一次配置的内网CIDR地址段。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **防火墙** ：操作系统安装完成后，系统对外网网络只开放IN方向的22端口。操作系统安装成功后，用户可自行登录操作系统更改iptable设置。详情请参考[防火墙设置操作指南](../Operation-Guide/Network-And-Security/Steps-Network-And-Security.md)。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **公网带宽** ：

用户可以在创建云物理服务器时选择购买或不购买公网IP。选择购买基础网络实例时，公网IP和云物理服务器是绑定的。公网IP由系统自动分配，用户不可修改公网IP,**但是云物理服务器创建后不可添加公网IP** 。选择购买私有网络实例时，若不够买公网IP，可以待实例创建成功后绑定公网IP。

用户可选择1-200Mbps的公网带宽速率，并可在创建后做升配操作。
具体操作步骤参见[调整公网带宽](../Operation-Guide/Adjust-Public-Network-Bandwidth/Description-Adjust-Public-Network-Bandwidth.md)章节。

- 配置服务器基本信息：
配置服务器名称、描述、操作系统密码。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **实例名称** ：实例名称是指云物理服务器的别名，用户可以自定义设置，设置完成后可以通过云物理服务器列表中使用别名来筛选。一次购买多台云物理服务器的情况下，默认在设置名称后面加上数字，以递增的形式来标志多台云物理服务器。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **主机名** ：主机名是指云物理服务器操作系统内部的计算机名，用户可以自定义设置，云物理服务器成功生产后可以通过登录云物理服务器内部查看。一次购买多台云物理服务器的情况下，默认在设置名称后面加上数字，以递增的形式来标志多台云物理服务器。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 主机名为可选项，如果不输入主机名，则默认使用“host-内网IPv4地址第三段-内网IPv4地址第四段”为主机名。


![配置服务器](../Image/CPS-create-basicinfo.png)



- 配置购买时长：
购买时长1-9个月、1、2、3年。

![配置购买时长](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/cn-Create-8Quantity.png)

- 点击**立即购买**按钮，跳转到订单确认页

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;按照京东云统一的订单计费流程支付成功后，跳转回控制台列表页面。
