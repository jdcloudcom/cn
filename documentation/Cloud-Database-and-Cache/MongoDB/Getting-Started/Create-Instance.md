# 创建实例

您可以通过 MongoDB 控制台或 API 快速创建 MongoDB 实例，关于实例的计费说明请参见“[价格总览](../Pricing/Billing-Overview.md)”、“[计费规则](../Pricing/Billing-Rules.md)”。

本文介绍通过控制台如何创建 MongoDB 实例。

## 前提条件
- 已注册京东云账号，并完成实名认证。如果还没有账号请 [注册](https://accounts.jdcloud.com/p/regPage?source=jdcloud&ReturnUrl=%2f%2fuc.jdcloud.com%2fpassport%2fcomplete%3freturnUrl%3dhttp%3A%2F%2Fuc.jdcloud.com%2Fredirect%2FloginRouter%3FreturnUrl%3Dhttps%253A%252F%252Fwww.jdcloud.com%252Fhelp%252Fdetail%252F734%252FisCatalog%252F1)，或 [实名认证](https://uc.jdcloud.com/account/certify)。
- 如计费类型选择按配置计费，请确认您的账户余额（包括代金券）不小于50元。

## 操作步骤
1. 登录 [MongoDB 控制台](https://mongodb-console.jdcloud.com/mongodb)。
2. 在“实例列表”页面，点击 **创建** ，进入“创建实例”页面。

    ![创建实例](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-003.png)
    
3. 在“创建实例”页面，选择计费类型，可选择：**包年包月** 或 **按配置**。

	![创建实例](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-003.png)
	
4. 选择实例配置

	1. 地域
	
       京东云的机房分布在全球多个位置，这些位置称为地域。云数据库 MongoDB 目前支持华北-北京、华东-上海，后续将支持更多地域。

	   说明：
	   - 处在同一地域的云服务产品之间通过内网互通，但不同账户的资源内网完全隔离；
	   - 处在不同地域的云服务产品之间内网不能互通；
	   - 购买云服务时建议选择最靠近您客户的地域，可降低访问时延；
	  
	2. 规格配置
	   - 数据库版本：目前可选版本为3.2，3.4与3.6版即将发布上线。
	   - 规格：	实例占用的CPU和内存，不同规格对应不同的最大连接数和IOPS（即读和写分别可以达到的最大值，混合读写最高可以达到指标的2倍）不同。
	   - 存储空间：实例占用的磁盘空间。
	   
	3. 网络
	
	   云数据 MongoDB支持私有网络部署。如果您当前尚未完成网络规划，请先去创建私有网络与子网。

	   说明：
	   
	   MongoDB 实例选择私有网络后不可更改，请务必保证您的 MongoDB实例与云主机在同一个私有网络内，以免您的云主机不能连接 MongoDB 实例。
	   
	4. 部署方式
	
	    MongoDB 实例支持单可用区和多可用区部署。单可用区部署指 MongoDB 实例的三个物理节点分布在同一可用区的不同物理机上，可以提供跨机架的容灾；多可用区部署指 MongoDB 实例的三个物理节点分布在不同可用区的物理机上，可以提供跨机房的容灾，但网络传输会有一定延迟。您可以根据业务要求选择部署方式。

	5. 密码
	
	   您可以在创建实例时设置密码，也可以暂不设置密码，待 MongoDB 实例创建完成后重置密码。

	6. 购买时长
	
	   计费类型选择包年包月时，需指定购买时长。云数据库 MongoDB 支持选择1个月至3年。通常购买时长越长，折合单价越便宜，具体优惠信息可在创建实例页面的时长选择处查看。
	
5. 点击 **立即购买** ，进入“订单确认”页面。
6. 在“订单确认”页面，确认实例信息，并阅读《云数据库 MongoDB 服务条款》。
	- 如计费类型为按配置，请点击 **立即开通** 。
	- 如计费类型为包年包月，请点击 **立即支付** ，进入“订单支付”页面，完成支付流程。
7. 支付流程流程完成后，页面会自动跳转到 MongoDB “实例列表”页面，等待实例创建完成，您可以在“实例列表”页面查看新创建的 MongoDB 实例。

## 相关参考

- [设置白名单](Set-Whitelist.md)
- [连接实例](Connect-Instance.md)
<<<<<<< HEAD
<<<<<<< HEAD
- [修改密码](../Operation-Guide/Account/ResetPassword.md)
- [导入数据](Import-Data.md)
- [变更实例配置](../Operation-Guide/Instance-Management/ModifyInstanceSpec.md)
=======
- [修改密码](../Operation-Guide/Account-Management/Reset-Password.md)
- [导入数据](Import-Data.md)
- [变更实例配置](../../Operation-Guide/Instance-Management/ModifyInstanceSpec.md)
>>>>>>> c166c890783711e05edecdb24daafecabfb4b919
=======
- [修改密码](../Operation-Guide/Account-Management/Reset-Password.md)
- [导入数据](Import-Data.md)
<<<<<<< HEAD
- [变更实例配置](../../Operation-Guide/Instance-Management/ModifyInstanceSpec.md)
>>>>>>> edit
=======
- [变更配置](../Operation-Guide/Instance-Management/Modify-Instance-Spec.md)
>>>>>>> edit
- [计费规则](../Pricing/Billing-Rules.md)
