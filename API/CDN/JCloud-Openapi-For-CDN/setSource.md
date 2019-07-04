# setSource


## 描述
设置源站信息

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}/source

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**sourceType**|String|False| |回源类型只能是[ips,domain,oss]中的一种|
|**backSourceType**|String|False| |回源方式,只能是[https,http]中的一种,默认http|
|**ipSource**|IpSourceInfo[]|False| | |
|**domainSource**|DomainSourceInfo[]|False| | |
|**ossSource**|String|False| |oss回源域名|
|**defaultSourceHost**|String|False| |默认回源host|

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
