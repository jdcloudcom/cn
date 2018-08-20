# 第三方镜像产品制作规范

更新时间：2018-07-24



系统要求

配置自检

（官方镜像默认配置已符合以下要求，请勿修改，为保证镜像正常使用建议按照以下要求进行自检）

1. 官方镜像已配置系统更新源，请不要随意修改，可参考文档核对配置：

https://www.jdcloud.com/help/detail/349/isCateLog/1

https://www.jdcloud.com/help/detail/714/isCateLog/1

2. 关闭防火墙：

l  Linux平台：关闭默认防火墙iptables

l  Windows平台：关闭默认防火墙firewall

3. 网卡MTU值确认

l  Linux平台：

只要启动网卡，dhcp 服务自动启动，连接网络后，会自动分配合适的MTU 值，所以不需要用户自行设置使用命令。

可使用命令： ifconfig |grep 查看MTU值。（当前官方为1450）

l  Windows平台：

可使用命令： netsh interface ipv4 show interface 查看MTU值。（当前官方为1400）

       如须调整，打开命令行窗口，输入如下命令设置 MTU（最高支持1500）：

c:\> netsh interface ipv4 set subinterface "本地连接" mtu=1500 store=persistent（网络接口名称：2008为“本地连接”，2012为“以太网”）



系统组件安装

安装 cloud-init 工具

l  Linux 平台 – CentOS系统

A.    卸载官方cloud-init

如果当前系统中安装了官方cloud-init，必须完全卸载，可执行以下指令确保官方版本完全卸载

n  卸载旧的cloud-init：

rpm –e cloud-init

n  删除原有配置和保留文件：

rm –rf /etc/conf/cloud/* 

rm –rf /var/lib/cloud/*

B.    安装京东云cloud-init

n  CentOS 6.X系列请通过以下地址下载


http://iaas-cns-download.oss.cn-north-1.jcloudcs.com/cloud-init-0.7.5-20.el6.2.x86_64.rpm

执行以下指令进行安装：

rpm –ivh cloud-init-0.7.5-20.el6.2.x86_64.rpm

n  CentOS 7.X系列请通过以下地址下载


http://iaas-cns-download.oss.cn-north-1.jcloudcs.com/cloud-init-0.7.5-20.el7.centos.1.x86_64.rpm

执行以下指令进行安装：

rpm –ivh cloud-init-0.7.5-20.el7.centos.1.x86_64.rpm

l  Linux 平台 – Ubuntu系统

A.    卸载官方cloud-init

如果当前系统中安装了官方cloud-init，必须完全卸载，可执行以下指令确保官方版本完全卸载

n  卸载旧的cloud-init：

apt-get purge cloud-init

n  删除原有配置和保留文件：

rm -rf /var/lib/cloud/*

B.    安装京东云cloud-init

n  Ubuntu 16.04 系列请通过以下地址下载


http://iaas-cns-download.oss.cn-north-1.jcloudcs.com/cloud-init_17.2-35-gf576b2a2-0ubuntu1_16.04.2-jd_all.deb

执行以下指令进行安装：

①    dpkg -i cloud-init_17.2-35-gf576b2a2-0ubuntu1_16.04.2-jd_all.deb

②    dpkg-reconfigure cloud-init

如果执行①时不成功，则执行以下③、④两条指令后后再执行②

③    apt-get install -f

④    dpkg -i cloud-init_17.2-35-gf576b2a2-0ubuntu1_16.04.2-jd_all.deb

在随后出现的页面中，取消部分数据源选项，仅保留以下4个选项：

* NoCloud: Reads info from /var/lib/cloud/seed only

* ConfigDrive: Reads data from Openstack Config Drive

* OpenStack: native openstack metadata service

* None: Failsafe datasource

l  Windows 平台


不需安装



操作建议

1.     Windows系统检查更新并安装更新。

2.     清除制作镜像时的访问痕迹。

3.     建议在生成最终镜像文件之前，进行一次关机、开机操作，确保所有更新和配置已生效，避免用户使用镜像创建主机之后，登录后即刻收到系统的重启提示。
