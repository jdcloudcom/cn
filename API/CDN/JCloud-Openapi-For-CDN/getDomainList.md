# getDomainList


## 描述
查询加速域名接口

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/domain


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyWord**|String|False| |根据关键字进行模糊匹配|
|**x-jdcloud-channel**|String|False|cdn|域名来源cdn/cdn,video视频云|
|**pageNumber**|Integer|False|1|pageNumber,默认值1|
|**pageSize**|Integer|False|20|pageSize,最大值50,默认值20|
|**status**|String|False| |根据域名状态查询, 可选值[offline, online, configuring, auditing, audit_reject]|
|**type**|String|False| |域名类型，(web:静态小文件，download:大文件加速，vod:视频加速，live:直播加速),不传查所有|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer| |
|**pageSize**|Integer| |
|**pageNumber**|Integer| |
|**domains**|ListDomainItem[]|域名列表|
### ListDomainItem
|名称|类型|描述|
|---|---|---|
|**cname**|String| |
|**description**|String| |
|**domain**|String| |
|**created**|String| |
|**modified**|String| |
|**status**|String| |
|**type**|String| |
|**auditStatus**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
