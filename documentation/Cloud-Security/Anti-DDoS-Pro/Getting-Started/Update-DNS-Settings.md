# 更新DNS解析

此步骤完成后，所有用户的访问流量都将经过IP高防，经高防保障后再转发回用户源站。

## 前提条件
- 已成功购买了IP高防，且计费状态正常。<Br/>
- 已完成了所有转发配置，并且确定配置已验证生效。

## 操作步骤
1. 登录 [IP高防 控制台](https://ip-anti-console.jdcloud.com/instancelist)。
2. 在“实例列表”页面，选择目标实例，点击 **实例名称** 或 **转发配置** ，进入实例详情页面。在网站类或非网站类转发规则中，复制待修改的cname值。<Br/>
以非网站转发规则为例，如下找到红框处待复制的cname：
![修改DNS](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/update%20dns%2001.png)
3. 在域名提供商处，需要修改域名解析配置让域名解析到高防IP上。
以京东云“云解析”为例，在 **控制台** –》 **域名服务** –》 **云解析** ，进入京东云[云解析控制台](https://dns-console.jdcloud.com/list)<Br/>
![修改DNS](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/update%20dns%2002.png)<Br/>
找到待解析的域名，如下：
![修改DNS](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/update%20dns%2003.png)<Br/>
单击进入解析配置：
![修改DNS](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/update%20dns%2004.png)<Br/>
将记录值，改为IP高防的cname地址即可。


## 特殊说明
- 若转发规则中的 **回源/防御** 状态为回源，则访问流量不会到高防，而是直接到源站。


## 相关参考
- [入门概述](Overview.md)
- [创建实例](Create-Instance.md)
- [非网站类规则](Non-Web-Service-Forwarding-Rule.md)
- [网站类规则](Web-Service-Forwarding-Rule.md)
- [放行回源IP](Whitelist-local-IP-subnet.md)
- [计费规则](../Pricing/Billing-Rules.md)
