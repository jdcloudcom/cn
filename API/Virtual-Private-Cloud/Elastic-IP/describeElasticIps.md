# describeElasticIps


## 描述
查询弹性ip列表

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/elasticIps/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |elasticIpIds - elasticip id数组条件，支持多个<br>elasticIpAddress - eip的IP地址，支持单个<br>chargeStatus	- eip的费用支付状态,normal(正常状态) or overdue(预付费已到期) or arrear(欠费状态)，支持单个<br>|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞), 页码超过总页数时, 显示最后一页|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|返回结果|

### Result
|名称|类型|描述|
|---|---|---|
|**elasticIps**|ElasticIp[]|elasticIp资源信息列表|
|**totalCount**|Integer|总数量|
### ElasticIp
|名称|类型|描述|
|---|---|---|
|**bandwidthMbps**|Integer|弹性ip的限速（单位：Mbps)|
|**charge**|Charge|计费配置|
|**createdTime**|String|弹性ip创建时间|
|**elasticIpAddress**|String|弹性IP地址|
|**elasticIpId**|String|弹性IP的Id|
|**instanceId**|String|实例Id|
|**instanceType**|String|实例类型|
|**networkInterfaceId**|String|配置弹性网卡Id|
|**privateIpAddress**|String|私有IP的IPV4地址|
|**provider**|String|IP服务商，取值为bgp或no_bgp|
### Charge
|名称|类型|描述|
|---|---|---|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**401**|Authentication failed|
