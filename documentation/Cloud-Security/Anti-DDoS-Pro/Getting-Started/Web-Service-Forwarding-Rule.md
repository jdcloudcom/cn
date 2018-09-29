# 网站类转发规则

网站类是针对网站域名业务进行的防护，支持流量型和应用型的攻击防护，包括CC攻击。

## 前提条件
- 已成功购买了IP高防，且计费状态正常。

## 操作步骤
1. 选中某个已购买的实例。单击“实例名称”或操作栏的“转发配置”，进入转发配置页面。
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/non-web%2001.png)

2. 在实例详情页面，切换到“网站转发配置”。
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2002.png)

3. 点击“添加规则”按钮，根据如下的弹窗提示，配置转发规则。
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2003.png)

规则配置部分字段解释如下：
- 域名：支持多级域名的配置，包括泛域名支持。
- 协议类型：支持HTTP和HTTPS两种类型，可根据网站协议情况勾选。当选择HTTPS协议时，系统会提示您上传证书。只有当上传证书成功后，防护才可生效。如果需要websocket协议接入，请开启websocket开关。
- 回源方式：可选择回源IP或回源域名。其中回源IP（云内+云外）支持20个IP地址，回源域名支持1个。源站域名不能和防护域名一样；源站IP不允许为内网地址。
若开启HTTP回源，则返回源站的协议将全部转换为HTTP协议。
- 网站类规则的源站端口默认支持80和443端口。允许自定义端口，HTTP和HTTPS协议各支持自定义5个不同的端口。
- 备用IP不是必填项。配置了备用IP，则常态时，cname将指向该IP。建议备用IP为日常对外展示的IP，回源IP为不对外的IP。配置备用IP能保证源站的更高可用性，可参考页面**产品图形说明**中的流程图。

## 相关参考

- [创建实例](Create-Instance.md)
- [计费规则](../Pricing/Billing-Rules.md)
- [常见问题](../FAQ/FAQ.md)

