# describeInstances


## 描述
查询RDS实例列表</br>- SQL Server：支持</br>- MySQL：支持

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False||显示数据的页码，取值范围：[1,1000)，页码超过总页数时，显示最后一页，用于查询列表的接口|
|**pageSize**|Integer|False||每页显示的数据条数，取值范围：10/20/30/50/100|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**dbInstances**|[DBInstance[]](##DBInstance)||
|**totalCount**|Integer||
### <a name="DBInstance">DBInstance</a>
|名称|类型|描述|
|---|---|---|
|**azId**|String[]|可用区ID， 第一个ID必须为主实例所在的可用区|
|**charge**|[Charge](##Charge)|计费配置|
|**createTime**|String|实例创建时间|
|**engine**|String|数据库类型 MySQL|SQL Server|
|**engineVersion**|String|数据库版本 MySQL支持5.6、5.7  SQL Server支持2008 R2、2012 EE、2014 EE、2016 EE|
|**instanceId**|String|数据库实例ID|
|**instanceName**|String|数据库实例名称|
|**instanceStatus**|String|实例状态|
|**instanceType**|String|实例类别，目前仅支持主实例，对应值为master|
|**regionId**|String|地域ID|
### <a name="Charge">Charge</a>
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

## 请求示例
GET
```

```

## 返回示例
无
