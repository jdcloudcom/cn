# associateElasticIp


## 描述
容器绑定弹性公网 IP，绑定的是主网卡、主内网IP对应的弹性IP. <br>
一台云主机只能绑定一个弹性公网 IP(主网卡)，若主网卡已存在弹性公网IP，会返回错误。<br>
如果是黑名单中的用户，会返回错误。


## 请求方式
POST

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/containers/{containerId}:associateElasticIp

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
