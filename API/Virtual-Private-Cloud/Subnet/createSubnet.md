# createSubnet


## 描述
创建子网

## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/subnets/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**addressPrefix**|String|True| |子网网段，vpc内子网网段不能重叠，cidr的取值范围：10.0.0.0/8、172.16.0.0/12和192.168.0.0/16及它们包含的子网，且子网掩码长度为16-28之间，如果vpc含有cidr，则必须为vpc所在cidr的子网|
|**description**|String|False| |子网描述信息,允许输入UTF-8编码下的全部字符，不超过256字符。|
|**routeTableId**|String|False| |子网关联的路由表Id, 默认为vpc的默认路由表|
|**subnetName**|String|True| |子网名称,只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符。|
|**vpcId**|String|True| |子网所属vpc的Id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|返回结果|

### Result
|名称|类型|描述|
|---|---|---|
|**subnetId**|String|子网ID|

## 返回码
|返回码|描述|
|---|---|
|**409**|Parameter conflict|
|**200**|Successful operation|
|**429**|Quota exceeded|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**500**|Internal server error|
|**503**|Service unavailable|
|**404**|Not found|
