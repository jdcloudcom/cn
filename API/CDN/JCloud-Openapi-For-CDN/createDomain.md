# createDomain


## 描述
创建点播加速域名

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**x-jdcloud-channel**|String|False|cdn|域名来源cdn/cdn,video视频云|
|**sourceType**|String|False| |回源类型只能是[ips,domain,oss]中的一种|
|**cdnType**|String|False| |点播域名的类型只能是[vod,download,web]中的一种|
|**backSourceType**|String|False| |回源方式,只能是[https,http]中的一种,默认http|
|**dailyBandWidth**|Long|False| |日带宽(Mbps)|
|**quaility**|String|False| |服务质量,只能是[good,general]中的一种,默认为good|
|**maxFileSize**|Long|False| | |
|**minFileSize**|Long|False| | |
|**sumFileSize**|Long|False| | |
|**avgFileSize**|Long|False| | |
|**defaultSourceHost**|String|False| | |
|**httpType**|String|False| | |
|**ipSource**|IpSourceInfo[]|False| | |
|**domainSource**|DomainSourceInfo[]|False| | |
|**ossSource**|String|False| | |

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
