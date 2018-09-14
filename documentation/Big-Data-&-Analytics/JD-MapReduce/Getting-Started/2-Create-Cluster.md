# 创建集群

您可以通过 JMR 控制台快速创建集群。
关于JMR的计费说明请参见：[价格总览](../Pricing/Price-Overview.md)、[计费概述](../Pricing/Billing-Overview.md)，本文介绍通过控制台创建JMR集群。

## 前提条件
- 已注册京东云账号，并完成实名认证。如果还没有账号请 [注册](https://accounts.jdcloud.com/p/regPage?source=jdcloud&ReturnUrl=%2f%2fuc.jdcloud.com%2fpassport%2fcomplete%3freturnUrl%3dhttp%3A%2F%2Fuc.jdcloud.com%2Fredirect%2FloginRouter%3FreturnUrl%3Dhttps%253A%252F%252Fwww.jdcloud.com%252Fhelp%252Fdetail%252F734%252FisCatalog%252F1)，或 [实名认证](https://uc.jdcloud.com/account/certify)。
- 如计费类型选择按配置计费，请确认您的账户余额（包括代金券）不小于50元。

## 操作步骤
1. 登录 [JMR 控制台](https://xdata.jdcloud.com/rmgr/resources/res-manage/custom-resources.html#/)，选择地域。
     京东云的机房分布在全球多个位置，这些位置称为地域。JMR 目前支持华北-北京、华南-广州，后续将支持更多地域。

	   说明：
	   - 处在同一地域的云服务产品之间通过内网互通，但不同账户的资源内网完全隔离；
	   - 处在不同地域的云服务产品之间内网不能互通；
	   - 购买云服务时建议选择最靠近您客户的地域，可降低访问时延；
2. 在集群管理页面，点击“创建”，进入创建页面。

	1. 软件设置
	
	   说明：
	   - 开启高可用，集群会有两个Master：分别为Active Namenode和Standby Namenode：两台Namenode形成互备，一台处于Active状态，为主Namenode，另一台处于Standby状态，为备Namenode，只有主Namenode才能对外提供读写服务；
	   - 不开启高可用，集群默认有一个Master；
	   - JMR_BD-OS-1.0版本在创建集群的时候，默认选择高可用；
	
3. 点击“立即购买”，页面会自动跳转到 JMR 集群管理页面，等待集群创建完成。

