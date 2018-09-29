# modifyRouteTableRules


## 描述
修改路由表规则

## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/routeTables/{routeTableId}:modifyRouteTableRules

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**routeTableId**|String|True| |RouteTable ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**modifyRouteTableRuleSpecs**|ModifyRouteTableRules[]|True| |路由表规则信息|

### ModifyRouteTableRules
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**addressPrefix**|String|False| |路由表规则前缀, internet类型路由跟其他类型的路由，addressPrefix不允许重复|
|**nextHopId**|String|False| |下一跳id|
|**nextHopType**|String|False| |下一跳类型, 取值范围:instance:云主机, internet:公网, vpc_peering:vpc对等连接, bgw:边界网关|
|**priority**|Number|False| |规则匹配优先级，取值范围[1,255]。当路由规则子网掩码不同时，路由最长匹配优先；当路由规则子网掩码相同时, 按照优先级匹配转发, 优先级数字越小优先级越高，路由规则子网掩码相同、优先级相同、下一跳不同时，形成等价路由，不同下一跳负载均担。|
|**ruleId**|String|True| |路由表规则的ID|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**400**|invalid parameter|
|**404**|RouteTable or RouteTableRule not found|
|**500**|Internal server error|
