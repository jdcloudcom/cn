# describeAlarms


## 描述
查询监控规则，支持按照规则状态、报警状态、资源ID和产品名称进行查询。

## 请求方式
GET

## 请求地址
https://monitor.jdcloud-api.com/v1/regions/{regionId}/alarms

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**enabled**|Integer|False| |规则状态：1为启用，0为禁用|
|**isAlarming**|Integer|False| |是否为正在报警的规则，0为忽略，1为是，与 status 同时只能生效一个,isAlarming 优先生效|
|**pageNumber**|Integer|False| |页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False| |分页大小，默认为20，取值范围：[10,100]|
|**resourceId**|String|False| |资源Id|
|**serviceCode**|String|False| |产品名称|
|**status**|Integer|False| |规则报警状态, 1：正常, 2：报警，4：数据不足|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求的标识id|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**alarmList**|Alarm[]|规则列表|
|**numberPages**|Number|总页数|
|**numberRecords**|Number|总记录数|
|**pageNumber**|Number|页码|
|**pageSize**|Number|分页大小|
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
