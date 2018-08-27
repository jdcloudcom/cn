# createCacheInstance


## 描述
创建一个指定配置的缓存Redis实例

## 请求方式
POST

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstance**|[CacheInstanceSpec](##CacheInstanceSpec)|True|||
|**charge**|[ChargeSpec](##ChargeSpec)|False|||

### <a name="CacheInstanceSpec">CacheInstanceSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**azId**|[AzIdSpec](##AzIdSpec)|True||缓存Redis实例所在区域可用区ID信息|
|**cacheInstanceClass**|String|True||实例规格代码，参见实例规格代码表。|
|**cacheInstanceDescription**|String|False||缓存Redis实例描述|
|**cacheInstanceName**|String|True||实例名称，只支持数字、字母、英文下划线、中文，且不少于2字符不超过32字符|
|**password**|String|True||密码，必须包含且只支持字母及数字，不少于8字符不超过16字符|
|**subnetId**|String|True||所属子网的ID|
|**vpcId**|String|True||所属VPC的ID|
### <a name="AzIdSpec">AzIdSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**master**|String|False||缓存Redis主实例所在区域可用区ID|
|**slave**|String|False||缓存Redis从实例所在区域可用区ID|
### <a name="ChargeSpec">ChargeSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False||预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False||预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**cacheInstanceId**|String||
|**orderNum**|String||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
