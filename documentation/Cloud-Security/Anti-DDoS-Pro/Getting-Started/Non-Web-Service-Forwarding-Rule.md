# 非网站类转发规则

非网站类是针对用户IP地址进行的防御，只支持四层转发，不支持七层防护，如不支持CC防护。

## 前提条件
- 已成功购买了DDoS IP高防，且计费状态正常。

## 操作步骤
1. 选中某个已购买的实例。单击“实例名称”或操作栏的“转发配置”，进入转发配置页面。
![非网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/non-web%2004.png)

2. 在转发配置页面，可根据业务情况，配置转发规则。在这里可配置最多60条转发规则。
![非网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/non-web%2005.png)

3. 点击“添加”按钮，根据如下的弹窗提示，即可配置转发规则。我们支持TCP和UDP协议的配置。
![非网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/non-web%2006.png)

规则配置字段解释如下：

- **高防IP**：购买BGP线路，支持选择高防的BGP IP地址。如购买多个BGP IP，支持将不同的源站业务流量转发给不同的BGP IP进行防护。 

- 转发协议：支持选择TCP/UDP协议。

- 转发端口：支持配置IP高防转发端口，建议和源站端口保持一致， **网站类转发规则中已配置的端口，不支持在非网站类转发规则中重复配置**。

- 转发规则：支持轮询、加权轮询、源IP hash。

- 回源方式：支持选择回源IP或回源域名。其中回源IP（云内+云外）支持20个IP地址，回源域名支持1个。**注意，源站IP不允许填写内网地址，如源站为港澳台或海外地区，请用户自行确认网络延迟和稳定性是否满足要求，如延迟过高，接入DDoS IP高防可能出现超时现象，此场景建议使用京东云SCDN产品海外线路**。

- 源站端口：用户源站业务端口。

- 备用IP：备用IP不是必填项。配置了备用IP，则非DDoS攻击时，开启回源模式，高防CNAME将指向该IP。建议备用IP为日常对外展示的IP，回源IP为不对外的IP。配置备用IP能保证源站的隐蔽性和高可用性，可参考下面 **产品设计说明** 中的流程图。

![产品设计说明](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/ip-anti-design-cn.png)

4. 非网站转发规则创建成功后，在规则列表中，点击复制CNAME，可在DNS中修改解析将流量切到IP高防上，详情参考[更新DNS解析](Update-DNS-Settings.md)
![非网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/non-web%2007.png)

5. 多条非网站转发规则支持按照转发端口进行排序，默认按照创建时间排序，可点击图中按钮进行升序或降序排序，点击按钮旁空白处可恢复默认创建时间排序。BGP线路的非网站转发规则排序会优先按照同一高防IP的不同端口聚合后，再根据端口进行升序或降序排序。
![非网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/Port-Sorting.PNG)

6. 非网站转发规则支持批量进行删除和切换防御/回源模式。
![非网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/batch-operate01.PNG)

## 相关参考

- [创建实例](Create-Instance.md)
- [计费规则](../Pricing/Billing-Rules.md)
- [常见问题](../FAQ/FAQ.md)
