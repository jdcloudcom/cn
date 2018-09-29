# 验证配置生效

此步骤 **不是必须步骤**  
<Br/>但是为了最大程度保证业务的稳定，我们建议在修改DNS解析前先进行本地的测试。

## 前提条件
- 已成功购买了IP高防，计费状态正常，且已配置好转发规则。

## 本地测试步骤
1.登录任意一台Linux服务器;</br>
2.在命令行下输入如下内容：</br>
curl -x cname:port DomainName
<Br/>例如：<Br/>
![验证配置生效](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/Verify-Local-Settings.png)
<Br/>若返回访问域名的页面内容，则表示配置成功。

## 相关参考
- [入门概述](Overview.md)
- [创建实例](Create-Instance.md)
- [非网站类规则](Non-Web-Service-Forwarding-Rule.md)
- [网站类规则](Web-Service-Forwarding-Rule.md)
- [放行回源IP](Whitelist-local-IP-subnet.md)
- [计费规则](../Pricing/Billing-Rules.md)
