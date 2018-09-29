# modifyInstanceIpWhiteList


## 描述
设置实例 IP 白名单

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:setIpWhiteList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ipBwListSpec**|IpBwListSpec|True| |设置 IP 黑名单请求|

### IpBwListSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ipList**|String[]|False| |IP 或 IP 段列表|
|**tryFlag**|Boolean|False| |false 时强制写入, true 时有重复则不写入|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**msgList**|BwRepeatMsg[]| |
|**status**|Status| |
### BwRepeatMsg
|名称|类型|描述|
|---|---|---|
|**black**|String|黑名单重复 IP/IP段|
|**white**|String|白名单重复 IP/IP段|
### Status
|名称|类型|描述|
|---|---|---|
|**code**|Integer|请求错误码|
|**msg**|String|请求错误消息|
|**retcode**|Integer|请求结果, 0 表示成功, 非 0 表示失败|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
