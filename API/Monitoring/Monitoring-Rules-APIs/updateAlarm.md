# updateAlarm


## 描述
修改已创建的报警规则，支持修改报警规则及通知的联系人信息。当报警规则处于“已启用”状态时，允许修改报警规则。

## 请求方式
PATCH

## 请求地址
https://monitor.jdcloud-api.com/v1/regions/{regionId}/alarms/{alarmId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**alarmId**|String|True| |规则id|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**calculation**|String|True| |统计方法：平均值=avg、最大值=max、最小值=min、总和=sum|
|**contactGroups**|String[]|False| |通知的联系组，如 [“联系组1”,”联系组2”]|
|**contactPersons**|String[]|False| |通知的联系人，如 [“联系人1”,”联系人2”]|
|**downSample**|String|False| |取样频次|
|**metric**|String|True| |根据产品线查询可用监控项列表 接口 返回的Metric字段|
|**noticePeriod**|Integer|False| |通知周期 单位：小时|
|**operation**|String|True| |>=、>、<、<=、==、!=|
|**period**|Integer|True| |统计周期（单位：分钟），可选值：2,5,15,30,60|
|**serviceCode**|String|True| |产品名称|
|**threshold**|Number|True| |阈值|
|**times**|Integer|True| |连续多少次后报警，可选值:1,2,3,5|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求的标识id|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**alarmId**|String|规则id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**500**|internal server error|
