# describeRouteTable


## 描述
查询路由表信息详情

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/routeTables/{routeTableId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**routeTableId**|String|True| |RouteTable ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|返回结果|

### Result
|名称|类型|描述|
|---|---|---|
|**routeTable**|RouteTable|路由表资源信息|
### RouteTable
|名称|类型|描述|
|---|---|---|
|**createdTime**|String|路由表创建时间|
|**description**|String|路由表描述信息，允许输入UTF-8编码下的全部字符，不超过256字符。|
|**routeTableId**|String|路由表ID|
|**routeTableName**|String|路由表名称，只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符。|
|**routeTableRules**|RouteTableRule[]|路由表规则信息|
|**routeTableType**|String|路由表类型，default：默认路由表，custom：自定义路由表|
|**subnetIds**|String[]|路由表绑定的子网列表|
|**vpcId**|String|私有网络ID|
### RouteTableRule
|名称|类型|描述|
|---|---|---|
|**addressPrefix**|String|匹配地址前缀, internet类型路由跟其他类型的路由，addressPrefix不允许重复|
|**nextHopId**|String|下一跳id|
|**nextHopType**|String|下一跳类型, 取值范围:local:本地, instance:云主机, internet:公网, vpc_peering:vpc对等连接, bgw:边界网关|
|**priority**|Number|规则匹配优先级，取值范围[1,255]，默认为100。当路由规则子网掩码不同时，路由最长匹配优先；当路由规则子网掩码相同时, 按照优先级匹配转发, 优先级数字越小优先级越高，路由规则子网掩码相同、优先级相同、下一跳不同时，形成等价路由，不同下一跳负载均担。|
|**ruleId**|String|路由表规则ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**401**|Authentication failed|
