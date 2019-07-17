# queryIpBlackList


## 描述
查询ip黑名单

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}/ipBlackList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**domain**|String|域名|
|**ips**|Object[]|黑名单列表|
|**status**|String|黑名单状态,on:开启,off:关闭|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
