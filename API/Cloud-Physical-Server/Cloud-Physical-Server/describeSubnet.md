# describeSubnet


## 描述
查询子网

## 请求方式
GET

## 请求地址
https://cps.jdcloud-api.com/v1/regions/{regionId}/subnet

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeRegiones）获取云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True| |可用区, 如cn-east-1a；可调用接口（describeRegiones）获取云物理服务器在该地域支持的可用区|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**subnet**|Subnet|子网详细信息|
### Subnet
|名称|类型|描述|
|---|---|---|
|**az**|String|可用区, 如cn-east-1a|
|**cidr**|String|子网CIDR|
|**networkType**|String|网络类型|
|**region**|String|地域代码, 如cn-east-1|
|**subnetId**|String|子网ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
