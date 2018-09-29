# createAlarm


## 描述
创建报警规则，可以为某一个实例创建报警规则，也可以为多个实例同时创建报警规则。

## 请求方式
POST

## 请求地址
https://monitor.jdcloud-api.com/v1/regions/{regionId}/alarms

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|True| |幂等性校验参数，最长32位，值不变则返回值不会变|
|**createAlarmSpec**|CreateAlarmSpec|True| | |

### CreateAlarmSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**calculation**|String|True| |统计方法，必须与定义的metric一致，可选值列表：avg,max,sum,min|
|**contactGroups**|String[]|False| |报警规则通知的联系组，必须在控制台上已创建，例如" ['联系组1','联系组2']"|
|**contactPersons**|String[]|False| |报警规则通知的联系人，必须在控制台上已创建，例如 [“联系人1”,”联系人2”]|
|**downSample**|String|False| |取样频次，某些metric支持设置downSample，通过 <a href="http://docs.jdcloud.com/monitoring/api/describemetricsforcreatealarm">[查询可用创建监控规则的指标列表]</a> 接口可查看。|
|**metric**|String|True| |取值请查看 <a href="http://docs.jdcloud.com/monitoring/api/describemetricsforcreatealarm">[查询可用创建监控规则的指标列表]</a> 接口 的metric字段|
|**noticePeriod**|Integer|False| |通知周期 单位：小时|
|**operation**|String|True| |报警比较符，只能为以下几种<=,<,>,>=,==,!=|
|**period**|Integer|True| |统计周期，单位为分钟,目前支持的取值：2，5，15，30，60|
|**resourceIds**|String[]|True| |报警规则对应实例列表，每次最多100个，例如"['resourceId1','resourceId2']"|
|**serviceCode**|String|True| |产品名称，取值请查看 <a href="http://docs.jdcloud.com/monitoring/api/describemetricsforcreatealarm">[查询可用创建监控规则的指标列表]</a> 接口 的serviceCode字段|
|**threshold**|Number|True| |报警阈值，目前只开放数值类型功能|
|**times**|Integer|True| |持续周期，连续探测几个统计周期都满足阈值条件时报警，可选值:1,2,3,5|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求的标识id|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**alarmIdList**|String[]|创建成功的规则id列表|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**500**|internal server error|
