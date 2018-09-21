# 网络和安全性

## 功能描述

通过iptables可以为Linux服务器配置有状态的防火墙，能够指定并记住为发送或接收信息包所建立的连接的状态，是一套用来设置、维护和检查Linux内核的IP包过滤规则的命令包。

table--Linux的iptables防火墙默认有三种表，Filter、NAT与Mangle，当然还有自定义的，其中Filter即是默认使用的表格；

chain--条链，比如filter有INPUT、OUTPUT、FORWARD三条链。

**注意：请谨慎关闭SSH登录22端口，关闭22端口会造成您不可从外部访问云物理服务器！**
