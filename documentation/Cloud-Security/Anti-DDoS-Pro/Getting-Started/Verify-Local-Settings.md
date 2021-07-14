# 验证配置生效

此步骤 **不是必须步骤**  
<Br/>但是为了最大程度保证业务的稳定，建议在修改DNS解析前先进行本地的测试。

## 前提条件
- 已成功购买了DDoS IP高防，计费状态正常，且已配置好转发规则。

## 本地测试步骤

**非网站类转发规则验证**

用户源站业务使用IP进行访问，配置完四层IP+端口的转发规则后，使用PING命令查看高防CNAME对应的IP地址，然后使用telnet命令访问DDoS IP高防IP地址和端口，如果能连通证明DDoS IP高防转发配置成功。

**网站类转发规则验证**

方法1.登录一台Linux服务器，在命令行下输入如下内容：</br>
curl -x cname:port DomainName
<Br/>例如：<Br/>
![验证配置生效](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/Verify-Local-Settings01.png)
<Br/>若返回访问域名的页面内容，则表示配置成功。

方法2.
- 修改本地计算机hosts文件，使用记事本打开C:\Windows\System32\drivers\etc目录下的hosts文件，在文件中添加DDoS IP高防的IP地址和防护域名。</br>
- 保存hosts文件，在本地计算机使用PING命令测试防护域名，如果解析到高防CNAME和IP地址，证明本地hosts配置生效。</br>
- 使用浏览器访问域名，若返回访问域名的页面内容，则表示配置成功。<Br/>
![验证配置生效](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/Verify-Local-Settings02.png)

## 相关参考
- [入门概述](Overview.md)
- [创建实例](Create-Instance.md)
- [非网站类规则](Non-Web-Service-Forwarding-Rule.md)
- [网站类规则](Web-Service-Forwarding-Rule.md)
- [放行回源IP](Whitelist-local-IP-subnet.md)
- [计费规则](../Pricing/Billing-Rules.md)
