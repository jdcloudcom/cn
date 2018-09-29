# 后端服务签名


目前 API 网关为您配置安全防护设置，提供了两种安全措施：后端签名密钥和流控策略。本章将介绍后端签名。

后端签名密钥采用京东云用户AK/SK(Access Key/Access Key Secret) 在网关请求您的真实后端时，通过后端签名校验保障您后端的安全。

您将京东云用户AK绑定到 API分组 上后，当网关请求这个分组下的 API 时，会添加并出示该AK/SK，您的后端通过验证签名字符串来验证网关的身份。


## 操作步骤

* [配置后端签名步骤说明](../Operation-Guide/Create-BackSign/Create-BackSign.md)

  
