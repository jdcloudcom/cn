# describeCacheInstance


## 描述
查询单个缓存Redis实例详情

## 请求方式
GET

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceId**|String|True| |缓存Redis实例ID，是访问实例的唯一标识。|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|本次查询请求的ID|
|**result**|Result|查询缓存实例列表信息的结果|

### Result
|名称|类型|描述|
|---|---|---|
|**cacheInstance**|CacheInstance|要查询目标缓存实例的信息|
### CacheInstance
|名称|类型|描述|
|---|---|---|
|**auth**|Boolean|是否免密|
|**azId**|AzId|az信息|
|**cacheInstanceClass**|String|实例规格代码，参见<a href="https://www.jdcloud.com/help/detail/411/isCatalog/1">实例规格代码</a>|
|**cacheInstanceDescription**|String|实例描述|
|**cacheInstanceId**|String|实例ID|
|**cacheInstanceMemoryMB**|Integer|容量，单位MB|
|**cacheInstanceName**|String|实例名称|
|**cacheInstanceStatus**|String|实例状态，running：运行，error：错误，creating：创建中，changing：变配中，deleting：删除中|
|**charge**|Charge|计费信息|
|**connectionDomain**|String|访问域名|
|**createTime**|String|创建时间|
|**instanceVersion**|String|实例版本|
|**port**|Integer|端口|
|**subnetId**|String|所属子网的ID|
|**vpcId**|String|所属VPC的ID|
### AzId
|名称|类型|描述|
|---|---|---|
|**master**|String|缓存Redis主实例所在区域可用区ID|
|**slave**|String|缓存Redis从实例所在区域可用区ID|
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
|**404**|NOT_FOUND|
