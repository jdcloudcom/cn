# modifyNetworkInterface


## 描述
修改弹性网卡接口

## 请求方式
PATCH

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkInterfaces/{networkInterfaceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkInterfaceId**|String|True| |networkInterface ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |描述,允许输入UTF-8编码下的全部字符，不超过256字符|
|**networkInterfaceName**|String|False| |弹性网卡名称,只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符|
|**securityGroups**|String[]|False| |以覆盖原有安全组的方式更新的安全组。如果更新安全组ID列表，最多5个安全组|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Request parameter x.y.z is 'xxx', expected one of [yyy,zzz]|
|**404**|Resource not found|
