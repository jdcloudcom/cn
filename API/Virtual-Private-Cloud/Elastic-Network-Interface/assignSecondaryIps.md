# assignSecondaryIps


## 描述
给网卡分配secondaryIp接口

## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkInterfaces/{networkInterfaceId}:assignSecondaryIps

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkInterfaceId**|String|True| |networkInterface ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**force**|Boolean|False|True|secondary ip被其他接口占用时，是否抢占。false：非抢占重分配，true：抢占重分配，默认抢占重分配。默认值：true|
|**secondaryIpCount**|Number|False| |指定自动分配的secondaryIp个数|
|**secondaryIps**|String[]|False| |指定分配的secondaryIp地址|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**400**|Request parameter x.y.z is 'xxx', expected one of [yyy,zzz]|
|**404**|Resource not found|
