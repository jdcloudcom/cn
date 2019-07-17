# getDomainDetail


## 描述
查询加速域名详情

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}

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
|**allStatus**|String| |
|**allowNoReferHeader**|String| |
|**allowNullReferHeader**|String| |
|**dailyBandWidth**|Integer| |
|**forbiddenType**|String| |
|**maxFileSize**|Long| |
|**minFileSize**|Long| |
|**sumFileSize**|Long| |
|**avgFileSize**|Long| |
|**referList**|String[]| |
|**referType**|String| |
|**domain**|String| |
|**cname**|String| |
|**archiveNo**|String| |
|**type**|String| |
|**created**|String| |
|**modified**|String| |
|**status**|String| |
|**auditStatus**|String| |
|**source**|BackSourceInfo| |
|**sourceType**|String| |
|**defaultSourceHost**|String|默认的回源host|
|**backSourceType**|String| |
|**httpType**|String| |
|**certificate**|String| |
|**rsaKey**|String| |
|**jumpType**|String| |
|**certFrom**|String| |
|**sslCertId**|String| |
|**certName**|String| |
|**certType**|String| |
|**sslCertStartTime**|String| |
|**sslCertEndTime**|String| |
### BackSourceInfo
|名称|类型|描述|
|---|---|---|
|**ips**|IpSourceInfo[]| |
|**domain**|DomainSourceInfo[]| |
|**ossSource**|String| |
### DomainSourceInfo
|名称|类型|描述|
|---|---|---|
|**priority**|Integer| |
|**sourceHost**|String| |
|**domain**|String| |
### IpSourceInfo
|名称|类型|描述|
|---|---|---|
|**master**|Integer| |
|**ip**|String| |
|**ratio**|Double| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
