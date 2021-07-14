# 网站类转发规则

网站类是针对网站域名业务进行的防护，支持流量型和应用型的攻击防护，包括CC攻击。

## 前提条件
- 已成功购买了DDoS IP高防，且计费状态正常。

## 操作步骤
1. 选中某个已购买的实例。单击“实例名称”或操作栏的“转发配置”，进入转发配置页面。
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/non-web%2004.png)

2. 在实例详情页面，切换到“网站转发配置”。
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2007.png)

3. 点击“添加规则”按钮，根据如下的弹窗提示，配置转发规则。
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2015.PNG)

规则配置字段解释如下：

- **高防IP**：购买BGP线路，支持选择高防的BGP IP地址。如购买多个BGP IP，支持将不同的源站业务流量转发给不同的BGP IP进行防护。

- 域名：支持多级域名的配置，包括泛域名支持。  

- 转发协议：支持HTTP和HTTPS两种类型，可根据网站协议情况勾选。当选择HTTPS协议时，系统会提示您上传证书。只有当上传证书成功后，防护才可生效。

- 开启websocket：如果需要websocket协议接入，请开启websocket开关。

- 转发端口/源站端口：网站类规则的源站端口默认支持80和443端口。允许自定义端口，HTTP和HTTPS协议各支持自定义5个不同的端口。**非网站类转发规则中已配置的端口，不支持在网站类转发规则中重复配置**。

- HTTP访问跳转：**勾选HTTPS协议后开关可见**，开启时，所有来自HTTP协议的访问都将重定向到HTTPS的域名。

- 开启HTTP回源：**勾选HTTPS协议后开关可见**，若您的网站不支持HTTPS回源，请务必开启此项，默认回源端口为80。

- 开启HTTP2.0：**勾选HTTPS协议后开关可见**，开启后支持HTTP2.0协议。

- 回源长连接：默认回源短连接，开启后支持回源长连接。

- 被动健康检查：默认开启被动健康检查，支持关闭。

- 请求头支持下滑线：默认忽略请求头中的下划线，开启后可支持。

- SSL协议类型：**勾选HTTPS协议后开关可见**，默认勾选TLSV1.0/1.1/1.2，需至少勾选一种协议。

- 加密套件等级：**勾选HTTPS协议后开关可见**，默认勾选中级，如遇到安全扫描显示低版本加密套件问题，建议勾选加密等级为高级。

- 转发规则：支持轮询、源IP hash和加权轮询。

- 回源方式：可选择回源IP或回源域名。其中回源IP（云内+云外）支持20个IP地址，回源域名支持1个。源站域名不能和防护域名一样。**注意，源站IP不允许填写内网地址，如源站为港澳台或海外地区，请用户自行确认网络延迟和稳定性是否满足要求，如延迟过高，接入DDoS IP高防可能出现超时现象，此场景建议使用京东云SCDN产品海外线路**。

- GEO回源：支持基于地域的访问回源。

- 备用IP：备用IP不是必填项。配置了备用IP，则非DDoS攻击时，开启回源模式，高防CNAME将指向该IP。建议备用IP为日常对外展示的IP，回源IP为不对外的IP。配置备用IP能保证源站的隐蔽性和高可用性，可参考下面 **产品设计说明** 中的流程图。

![产品设计说明](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/ip-anti-design-cn.png)

4. 网站转发规则创建成功后，在规则列表中，点击复制CNAME，可在DNS中修改解析将流量切到DDoS IP高防上，详情参考[更新DNS解析](Update-DNS-Settings.md)
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2011.png)

5. 网站转发规则配置完成后，防护开关默认开启，可点击切换到回源模式，回源模式下，流量不经过DDoS IP高防清洗，直接回源源站IP。
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2012.png)

6. 网站转发规则配置中如勾选HTTPS，在规则列表中，需要点击关联SSL数字证书。点击上传按钮，在证书管理界面可选择已上传的证书。如首次上传证书，点击 **管理证书** 按钮跳转SSL数字证书控制台界面上传证书，详情参考[上传SSL证书](https://github.com/jdcloudcom/cn/blob/edit/documentation/Cloud-Security/SSL-Certificate/Operation-Guide/Upload-SSL-Certificate.md)
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2013.png)
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2014.png)

7. 网站转发规则支持批量删除、开/关CC防护模式、开/关CC观察模式、切换防御/回源模式。
![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/batch-operate02.PNG)

## 相关参考

- [创建实例](Create-Instance.md)
- [计费规则](../Pricing/Billing-Rules.md)
- [常见问题](../FAQ/FAQ.md)

