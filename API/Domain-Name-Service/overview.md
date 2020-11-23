# 域名


## 简介
域名系统相关的接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**certificateTemplate**|POST|域名信息模板实名认证|
|**certificateTemplateState**|GET|查询域名信息模板实名认证状态|
|**checkDomain**|GET|检查域名是否可以注册|
|**createDomain**|POST|域名注册<br>域名注册前，请确保用户的京东云账户有足够的资金支付，Openapi接口回返回订单号，可以用此订单号向计费系统查阅详情<br>|
|**createTemplate**|POST|创建域名信息模板|
|**deleteTemplate**|DELETE|删除域名信息模板|
|**domainInfo**|GET|查询用户的域名信息|
|**domainLock**|POST|域名锁定，设置域名状态为禁止转移|
|**domainTemplateAssigned**|POST|通过已实名的信息模板，完成域名的快速过户|
|**domainUnLock**|POST|域名解锁，，取消域名禁止转移的状态|
|**getDomainTransferOutPassWord**|GET|获取转移密码，用于域名转移注册商转出获取域名转移密码|
|**modifyDns**|PUT|根据域名修改域名对应的 DNS 信息|
|**modifyTemplateInfo**|PUT|修改域名信息模板|
|**queryTemplateInfo**|GET|查询域名信息模板|
|**queryWhoisInfo**|GET|查询域名的whois信息|
|**renewDomain**|POST|针对用户的域名进行续费<br>域名续费前，请确保用户的京东云账户有足够的资金支付，Openapi接口回返回订单号，可以用此订单号向计费系统查阅详情<br>|
|**transferinDomain**|POST|用于提交域名转入操作<br>要转入域名前，请确保用户的京东云账户有足够的资金支付，Openapi接口回返回订单号，可以用此订单号向计费系统查阅详情<br>|
|**transferinDomainState**|GET|域名转入状态查询|
