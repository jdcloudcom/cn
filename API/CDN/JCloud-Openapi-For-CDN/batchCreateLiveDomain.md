# batchCreateLiveDomain


## 描述
创建直播域名

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/liveDomain:batchCreate


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**x-jdcloud-channel**|String|False|cdn|域名来源cdn/cdn,video视频云|
|**playDomain**|String|False| |播放域名|
|**publishDomain**|String|False| |创建推流域名时，必传推流域名|
|**sourceType**|String|False| |回源类型只能是[ips,domain]中的一种|
|**backHttpType**|String|False| | |
|**defaultSourceHost**|String|False| |默认回源host|
|**siteType**|String|False| |站点类型pull(拉流)push(推流)|
|**backSourceType**|String|False| |回源类型，目前只能为rtmp|
|**ipSource**|IpSourceInfo[]|False| | |
|**domainSource**|DomainSourceInfo[]|False| | |

### DomainSourceInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**priority**|Integer|False| | |
|**sourceHost**|String|False| | |
|**domain**|String|False| | |
### IpSourceInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**master**|Integer|False| | |
|**ip**|String|False| | |
|**ratio**|Double|False| | |

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Object| |
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
