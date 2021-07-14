# 更新DNS解析

此步骤完成后，所有用户的访问流量都将经过DDoS IP高防，经高防保障后再转发回用户源站。

**注意，修改DNS解析需使用CNAME解析到IP高防的CNAME记录值，DDoS IP高防节点为高可用集群部署，具备完善的监控和可用性保障措施，出现网络/硬件的维护、升级问题系统会切换DDoS IP高防CNAME对应的防护IP地址。如用户存在不支持CNAME记录或记录冲突的情况，可以使用A记录解析到DDoS IP高防的IP地址，此场景下如出现高防节点网络和系统维护情况，京东云会提前通知用户，需用户配合切换到京东云提供的备用防护IP。**

## 前提条件
- 已成功购买了DDoS IP高防，且计费状态正常。<Br/>
- 已完成了所有转发配置，并且确定配置已验证生效。

## 操作步骤
1. 登录 [DDoS IP高防 控制台](https://ip-anti-console.jdcloud.com/instancelist)。
2. 在“实例列表”页面，选择目标实例，点击 **实例名称** 或 **转发配置** ，进入实例详情页面。在网站类或非网站类转发规则中，复制待修改的CNAME值。<Br/>
以非网站转发规则为例，如下找到红框处待复制的CNAME：
![修改DNS](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/update%20dns%2005.png)
3. 在域名提供商处，需要修改域名解析配置让域名解析到高防IP上。
以京东云“云解析”为例，在 **控制台** –> **域名与备案** –> **云解析 DNS** ，进入京东云[云解析控制台](https://dns-console.jdcloud.com/list)<Br/>
![修改DNS](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/update%20dns%2006.png)<Br/>
找到待解析的域名，如下：
![修改DNS](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/update%20dns%2007.png)<Br/>
单击进入解析配置：
![修改DNS](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/update%20dns%2008.png)<Br/>
将记录值，改为DDoS IP高防的CNAME地址即可。


## 特殊说明
- 若转发规则中的 **防御/回源** 状态为回源，则访问流量直接解析到源站IP地址。


## 相关参考
- [入门概述](Overview.md)
- [创建实例](Create-Instance.md)
- [非网站类规则](Non-Web-Service-Forwarding-Rule.md)
- [网站类规则](Web-Service-Forwarding-Rule.md)
- [放行回源IP](Whitelist-local-IP-subnet.md)
- [计费规则](../Pricing/Billing-Rules.md)
