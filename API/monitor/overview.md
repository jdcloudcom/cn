# 云监控


## 简介
云监控相关接口，主要包含监控规则的增删改查，以及监控项数据的查询


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**createAlarm**|POST|创建报警规则，可以为某一个实例创建报警规则，也可以为多个实例同时创建报警规则。|
|**deleteAlarms**|DELETE|批量删除已创建的报警规则|
|**describeAlarmHistory**|GET|查询报警历史|
|**describeAlarms**|GET|查询监控规则|
|**describeAlarmsByID**|GET|查询规则详情|
|**describeMetricData**|GET|查看某资源的监控数据|
|**describeMetrics**|GET|根据产品线查询可用监控项列表|
|**describeMetricsForCreateAlarm**|GET|查询可用创建监控规则的指标列表|
|**disableAlarm**|POST|禁用报警规则。报警规则禁用后，将停止探测实例的监控项数据。|
|**enableAlarm**|POST|启用报警规则，当客户的报警规则处于停止状态时，可以使用此接口启用报警规则。|
|**putMetricData**|POST|自定义监控数据上报接口|
|**updateAlarm**|PATCH|修改已创建的报警规则|
