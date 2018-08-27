# updateDomain


## 描述
修改主域名

## 请求方式
POST

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domainUpdate

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True||域名|
|**id**|Integer|True||域名ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**updateDomain**|[Domain](##Domain)||
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
