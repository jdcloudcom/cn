# describeLiveRestartConfigs


## 描述
查询回看配置

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/liveRestart:configs


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNum**|Integer|False|1|页码；默认为1；取值范围[1, 100000]|
|**pageSize**|Integer|False|10|分页大小；默认为10；取值范围[10, 100]|
|**restartDomain**|String|True| |回看的推流域名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**pageNumber**|Integer|当前页码|
|**pageSize**|Integer|每页数量|
|**totalCount**|Integer|查询总数|
|**restartConfigs**|RestartConfig[]|域名集合|
### RestartConfig
|名称|类型|描述|
|---|---|---|
|**publishDomains**|RestartPublishDomain[]|推流域名集合|
|**playDomains**|RestartPlayDomain[]|播放域名集合|
### RestartPlayDomain
|名称|类型|描述|
|---|---|---|
|**playDomain**|String|播放域名|
|**restartStatus**|String|直播回看状态:<br>  on: 开启<br>  off: 关闭<br>|
|**playType**|String|播放域名类型:<br>  normal: 普通播放域名(时移播放域名)<br>  restart: 回看播放域名|
### RestartPublishDomain
|名称|类型|描述|
|---|---|---|
|**publishDomain**|String|推流域名|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
