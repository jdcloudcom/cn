# 京东云解析OpenAPI接口


## 简介
京东云解析OpenAPI接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addDomain**|POST|添加主域名|
|**addMonitor**|POST|添加子域名的监控项，默认把子域名的所有监控项都添加上监控|
|**addMonitorTarget**|POST|添加子域名的某些特定监控对象为监控项|
|**addRR**|POST|添加域名的解析记录|
|**delDomain**|DELETE|删除主域名|
|**getDomainQueryCount**|GET|查看域名的解析次数|
|**getDomainQueryTraffic**|GET|查看域名的查询流量|
|**getDomains**|GET|查询用户名下的主域名列表|
|**getMonitor**|GET|查看主域名的监控项的配置以及状态|
|**getMonitorAlarmInfo**|GET|主域名的监控项的报警信息|
|**getTargets**|GET|查询子域名的可用监控对象|
|**getViewTree**|GET|查询云解析所有的基础解析线路|
|**operateMonitor**|POST|监控项的操作集合，包括：删除，暂停，启动, 手动恢复, 手动切换|
|**operateRR**|POST|启用、停用、删除主域名下的解析记录|
|**searchRR**|GET|查询主域名的解析记录|
|**updateDomain**|POST|修改主域名|
|**updateMonitor**|POST|域名的监控项修改|
|**updateRR**|POST|修改主域名的某个解析记录|
