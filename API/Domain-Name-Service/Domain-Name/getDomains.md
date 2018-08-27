# getDomains


## 描述
查询用户名下的主域名列表

## 请求方式
GET

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domain

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|False||关键字，按照”%domainName%”模式搜索主域名|
|**pageNumber**|Integer|True||当前页数，起始值为1，默认为1|
|**pageSize**|Integer|True||分页查询时设置的每页行数|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**currentCount**|Integer||
|**dataList**|[Domain[]](##Domain)||
|**totalCount**|Integer||
### <a name="Domain">Domain</a>
|名称|类型|描述|
|---|---|---|
|**createTime**|Integer|创建时间，格式Unix timestamp|
|**domainName**|String|域名字符串|
|**expirationDate**|Integer|过期时间，格式Unix timestamp|
|**id**|Integer|域名的唯一ID|
|**packId**|Integer|套餐类型，0-免费 1-企业版 2-高级版|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
