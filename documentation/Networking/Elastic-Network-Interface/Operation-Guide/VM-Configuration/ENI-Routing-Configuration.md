# 辅助网卡路由配置

本教程以CentOS 6.8操作系统为例，介绍如何在云主机内配置弹性网卡（请先按照前述文档完成辅助网卡的启用与IP配置）。

**注意：中括号中的内容为用户自行填写内容。**

## 操作步骤
步骤1：在京东云控制台定位到目标云主机。

步骤2：通过SSH方式远程登录至目标云主机。

步骤3：执行以下命令查询已挂载的弹性网卡名称。

	# ifconfig -a

步骤4：执行以下命令编辑路由表文件。

	# vi /etc/iproute2/rt_tables

步骤5：在rt_tables文件中增加以下内容，如需要添加的辅助网卡名称为eth1。增加内容后保存并退出。

	100 eth1_table

步骤6：执行以下命令将源IP为eth1主IP地址的数据包引入eth1_table路由表进行路由查询。

	# ip rule add from [eth1 ip address] lookup eth1_table

假设eth1的IP地址为10.0.2.3/24，则以上命令为：

	# ip rule add from 10.0.2.3 lookup eth1_table

步骤7：执行以下命令在eth1_table路由表中添加默认路由。

	# ip route add table eth1_table 0.0.0.0/0 via [eth1 subnet gateway] dev eth1 src [eth1 ip address]

假设eth1的IP地址为10.0.2.3/24，网关地址为10.0.2.1/24，则以上命令为：

	# ip route add table eth1_table 0.0.0.0/0 via 10.0.2.1 dev eth1 src 10.0.2.3



