# createCacheInstance


## 描述
创建一个指定配置的缓存Redis实例
规格性能：创建缓存Redis实例的规格，分为主从版和集群版两种规格。每种规格都有最大连接数，内网带宽上限，CPU处理能力，规格代码等信息，具体可查看：<a href="https://www.jdcloud.com/help/detail/411/isCatalog/1">实例规格代码</a>
可用区：可用区是指在同一地域下，电力、网络等基础设施互相独立的物理区域。一个地域包含一个或多个可用区，同一地域下的多个可用区可以彼此连通。地域可用区详细信息可查询：<a href="https://www.jdcloud.com/help/detail/2222/isCatalog/1">地域可用区详情</a>
私有网络：简称VPC，自定义的逻辑隔离网络空间，支持自定义网段划分、路由策略等。具体信息可查询：<a href="https://www.jdcloud.com/help/detail/1509/isCatalog/1">私有网络VPC详情</a>
子网：子网是所属VPC IP地址范围内的IP地址块，简称subnet，在VPC下创建子网，同一VPC下子网的网段不可以重叠，不同VPC下子网的网段可以重叠。具体信息可查询：<a href="https://www.jdcloud.com/help/detail/1510/isCatalog/1">子网subnet详情</a>


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
|**cacheInstance**|[CacheInstanceSpec](##CacheInstanceSpec)|True||创建缓存实例的具体属性，包括所属私有网络ID(vpcId)、子网ID(subnetId)、缓存实例名称、缓存实例规格、缓存实例密码、缓存实例所在区域可用区ID信息和缓存实例描述。|
|**charge**|[ChargeSpec](##ChargeSpec)|False||计费信息的相关配置。|

### <a name="CacheInstanceSpec">CacheInstanceSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**azId**|[AzIdSpec](##AzIdSpec)|True||缓存Redis实例所在区域可用区ID信息|
|**cacheInstanceClass**|String|True||缓存redis实例规格代码，参见实例规格代码表<a href="https://www.jdcloud.com/help/detail/411/isCatalog/1">实例规格代码</a>。|
|**cacheInstanceDescription**|String|False||缓存Redis实例描述，不能超过256个字符|
|**cacheInstanceName**|String|True||缓存redis实例名称，只支持数字、字母、英文下划线、中文，且不少于2字符不超过32字符|
|**password**|String|False||密码，为空即为免密，包含且只支持字母及数字，不少于8字符不超过16字符|
|**subnetId**|String|True||缓存redis实例在私有网络下所属的子网ID|
|**vpcId**|String|True||缓存redis实例所属的私有网络ID|
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
|**requestId**|String|本次查询请求的ID。|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**cacheInstanceId**|String|创建的缓存实例的ID。|
|**orderNum**|String|创建缓存实例所生成的订单编号。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
