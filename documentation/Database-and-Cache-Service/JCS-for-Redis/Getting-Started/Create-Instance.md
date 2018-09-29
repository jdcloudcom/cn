# 创建实例

您可以在Redis控制台或者API新建Redis实例，关于实例的计费说明请参见“[价格总览](../Pricing/Price-Overview.md)”、“[计费规则](../Pricing/Billing-Rules.md)”。

本文介绍通过Redis控制台新建Redis实例。

## 前提条件
- 已注册京东云账号，并完成实名认证。如果还没有账号请 [注册](https://accounts.jdcloud.com/p/regPage?source=jdcloud&ReturnUrl=https%3a%2f%2fuc.jdcloud.com%2fpassport%2fcomplete%3freturnUrl%3dhttps%3a%2f%2fwww.jdcloud.com)，或 [实名认证](https://uc.jdcloud.com/account/certify)。
- 如计费类型选择按配置计费，请确认您的账户余额（包括代金券）不小于50元。

## 操作步骤
1. 登录 [Redis 控制台](https://redis-console.jdcloud.com/redis)。

2. 在“实例列表”页面，点击“创建”按钮，跳转到新建实例页。
   ![创建实例](https://github.com/jdcloudcom/cn/blob/master/image/Redis/create-redis-instance.PNG)

3. 在新建实例页选择付费方式、地域、规格、网络、部署方案、基本信息、购买量等信息

4. 点击 立即购买 ，进入“订单确认”页面。

5. 在“订单确认”页面，确认实例信息，并阅读《缓存Redis服务条款》。

  - 如计费类型为按配置，请点击 立即开通 。
  - 如计费类型为包年包月，请点击 立即支付 ，进入“订单支付”页面，完成支付流程。
支付流程流程完成后，页面会自动跳转到 Redis “实例列表”页面，等待实例创建完成，您可以在“实例列表”页面查看新创建的实例。

6. 在列表查看创建实例的完成状态
  - 如果状态显示为“创建中”，则请耐心等待几分钟
  - 如果状态显示为"运行"，则创建已完成

## 相关参考

- [入门指南概述](Set-Whitelist.md)
- [连接实例](Connect-Instances.md)
- [修改密码](../../Operation-Guide/Instance-Management/Change-Password.md)
- [变更实例配置](../../Operation-Guide/Instance-Management/Change-Configuration.md)
- [计费规则](../../Pricing/Billing-Rules.md)
