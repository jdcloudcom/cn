# disassociateElasticIp


## 描述
容器解绑公网 IP，解绑的是主网卡、主内网 IP 对应的弹性 IP.


## 请求方式
POST

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/containers/{containerId}:disassociateElasticIp

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**containerId**|String|True| |Container ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**elasticIpId**|String|True| |弹性IP ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
