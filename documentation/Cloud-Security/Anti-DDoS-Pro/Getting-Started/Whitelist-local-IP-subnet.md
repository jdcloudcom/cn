# 放行回源IP

此步骤仅针对使用防火墙的用户，**不是必须步骤**。
<Br/>若您的源站正在使用防火墙，为了保证不对IP高防的服务产生影响，请关闭。或者将IP高防的回源IP加入白名单。

## 前提条件
- 已成功购买了IP高防，且计费状态正常。

## 操作步骤
1. 登录 [IP高防 控制台](https://ip-anti-console.jdcloud.com/instancelist)。
2. 在“实例列表”页面，选择目标实例，点击 **实例名称** 或**转发配置**，进入实例详情页面。
![网站类实例](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2001.png)
3. 请在下图红框处所示，获取需要加入白名单的IP高防回源IP段。
![高防回源](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/instance03.png)
## 相关参考

- [入门概述](Overview.md)
- [创建实例](Create-Instance.md)
- [非网站类规则](Non-Web-Service-Forwarding-Rule.md)
- [网站类规则](Web-Service-Forwarding-Rule.md)
- [计费规则](../Pricing/Billing-Rules.md)
