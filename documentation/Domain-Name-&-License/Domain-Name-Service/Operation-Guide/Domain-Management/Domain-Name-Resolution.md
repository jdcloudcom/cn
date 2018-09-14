# 解析域名
域名注册后，客户只拥有了这个域名的使用权，但无法通过域名直接访问您的网站，或作为电子邮箱后缀进行邮件收发。“域名解析”是使用域名访问您的网站或邮箱的必备环节。

1.准备域名、网站（或邮箱）

您需要拥有一个域名以及从服务器提供商处获取主机 IP 地址（或电子邮箱 MX 记录），以便完成后续解析设置。

2.设置域名解析

京东云【控制台】，进入域名管理列表，点击解析后把域名指向网站主机 IP 地址（或电子邮箱 MX 记录），即可快速完成域名解析设置。具体操作流程如下：

A.进入域名解析设置页

- 京东云【控制台】，进入域名管理列表，后选择要操作的域名点击解析操作，直接进入解析操作页面

![image](https://github.com/jdcloudcom/cn/blob/edit/documentation/Domain-Name-&-License/Image-Domain/jiexi1.jpg)

- 点击【添加解析】，选择记录类型为 A 记录；主机记录为空，或填写 www；记录值填写您之前获取的主机 IP 地址；解析线路，TTL 默认即可。点击保存，即可完成域名解析设置。

![image](https://github.com/jdcloudcom/cn/blob/edit/documentation/Domain-Name-&-License/Image-Domain/jiexi2.jpg)


![image](https://github.com/jdcloudcom/cn/blob/edit/documentation/Domain-Name-&-License/Image-Domain/jiexi3.jpg)

B.DNS 检查

域名解析服务默认为新网DNS服务，但凡修改默认DNS服务，或者使用其他第三方商家的DNS服务后，域名解析将不再本控制台操作。

C.解析生效时间

新增解析完成设置即时生效。

修改解析则需要 10 分钟~2 小时，最终生效取决于各地运营商的缓存刷新时间，请耐心等待。
