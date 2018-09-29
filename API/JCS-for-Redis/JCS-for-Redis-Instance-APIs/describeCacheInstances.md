# describeCacheInstances


## 描述
查询缓存Redis实例列表及其实例信息，可分页查询，查询指定页码，指定分页大小和指定过滤条件

## 请求方式
GET

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |cacheInstanceId -缓存实例Id，精确匹配，支持多个<br>cacheInstanceName - 缓存实例名称，模糊匹配，支持单个<br>cacheInstanceStatus - 缓存你实例状态，精确匹配，支持多个(running：运行，error：错误，creating：创建中，changing：变配中，deleting：删除中)<br>|
|**pageNumber**|Integer|False| |请求查询缓存实例的页码；默认为1|
|**pageSize**|Integer|False| |请求查询缓存实例的分页大小；默认为20；取值范围[10, 100]|
|**sorts**|Sort[]|False| |createTime - 创建时间(asc：正序，desc：倒序)<br>|

### Sort
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**direction**|String|False| |排序条件的方向|
|**name**|String|False| |排序条件的名称|
### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|本次查询请求的ID|
|**result**|Result|查询缓存实例列表信息的结果|

### Result
|名称|类型|描述|
|---|---|---|
|**cacheInstances**|CacheInstance[]|要查询目标缓存实例的信息。|
|**totalCount**|Integer|查询到的缓存实例总个数。|
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
