# describeAlarmHistory


## 描述
查询报警历史，支持按照报警规则ID、资源ID、产品名称进行查询。

## 请求方式
GET

## 请求地址
https://monitor.jdcloud-api.com/v1/regions/{regionId}/alarmHistory

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|True| |查询数据结束时间，默认当前时间，可以输入long型时间，也可以输入yyyy-MM-dd'T'HH:mm:ssZ类型时间|
|**id**|String|False| |报警规则的Id|
|**pageNumber**|Integer|False| |页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False| |分页大小，默认为20，取值范围：[10,100]|
|**resourceId**|String|False| |资源Id|
|**serviceCode**|String|False| |产品名称|
|**startTime**|String|True| |查询数据开始时间，默认24小时前，可以输入long型时间，也可以输入yyyy-MM-dd'T'HH:mm:ssZ类型时间|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求的标识id|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**alarmHistoryList**|AlarmHistory[]|报警历史列表|
|**numberPages**|Number|总页数|
|**numberRecords**|Number|总记录数|
|**pageNumber**|Number|页码|
|**pageSize**|Number|分页大小|
### AlarmHistory
|名称|类型|描述|
|---|---|---|
|**calculation**|String|统计方法：平均值=avg、最大值=max、最小值=min|
|**contactGroups**|String[]|通知的联系组，如 [“联系组1”,”联系组2”]|
|**contactPersons**|String[]|通知的联系人，如 [“联系人1”,”联系人2”]|
|**deleted**|Integer|该规则是否已经被删除，1表示已经被删除，0表示未删除，被删除的规则，在使用查询规则的接口时，将不会被检索到|
|**enabled**|Integer|启用禁用 1启用，0禁用|
|**id**|String|规则id|
|**metric**|String|监控项|
|**metricName**|String|规则id监控项名称|
|**noticePeriod**|Integer|通知周期 单位：小时|
|**noticeTime**|String|报警的时间|
|**operation**|String|>=、>、<、<=、==、！=|
|**period**|Integer|统计周期（单位：分钟）|
|**region**|String|地域信息|
|**resourceId**|String|此规则所应用的资源id|
|**serviceCode**|String|报警规则对应的产品|
|**tag**|String|监控项附属信息|
|**threshold**|Number|阈值|
|**times**|Integer|连续多少次后报警|
|**value**|Number|报警值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**500**|internal server error|
