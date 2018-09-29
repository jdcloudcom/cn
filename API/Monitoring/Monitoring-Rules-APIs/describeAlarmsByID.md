# describeAlarmsByID


## 描述
查询规则详情

## 请求方式
GET

## 请求地址
https://monitor.jdcloud-api.com/v1/regions/{regionId}/alarms/{alarmId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**alarmId**|String|True| |规则id|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求的标识id|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**alarm**|Alarm| |
### Alarm
|名称|类型|描述|
|---|---|---|
|**calculation**|String|统计方法：平均值=avg、最大值=max、最小值=min|
|**contactGroups**|String[]|通知的联系组，如 [“联系组1”,”联系组2”]|
|**contactPersons**|String[]|通知的联系人，如 [“联系人1”,”联系人2”]|
|**createTime**|String|创建时间|
|**enabled**|Integer|启用禁用 1启用，0禁用|
|**id**|String|规则id|
|**metric**|String|监控项|
|**metricName**|String|规则id监控项名称|
|**noticePeriod**|Integer|通知周期 单位：小时|
|**noticeTime**|String|报警的时间  , 查询正在报警规则时该字段有效|
|**operation**|String|>=、>、<、<=、==、！=|
|**period**|Integer|统计周期（单位：分钟）|
|**region**|String|地域信息|
|**resourceId**|String|此规则所应用的资源id|
|**serviceCode**|String|报警规则对应的产品|
|**status**|Integer|监控项状态:1正常，2告警，4数据不足|
|**tag**|String|监控项附属信息|
|**threshold**|Number|阈值|
|**times**|Integer|连续多少次后报警|
|**value**|Number|报警值 , 查询正在报警规则时该字段有效|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**500**|internal server error|
