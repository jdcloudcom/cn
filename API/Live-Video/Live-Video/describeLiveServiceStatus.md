# describeLiveServiceStatus


## 描述
查询服务开通状态

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/users:status


## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|ruquestId|

### Result
|名称|类型|描述|
|---|---|---|
|**openStatus**|Boolean|服务开通状态|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
