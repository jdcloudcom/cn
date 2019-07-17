# getSslCertList


## 描述
查看证书列表

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/sslCert


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |第几页，从1开始计数|
|**pageSize**|Integer|False| |每页显示的数目|
|**domain**|String|False| |域名，支持按照域名检索证书|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|请求Id|

### Result
|名称|类型|描述|
|---|---|---|
|**certList**|SslCertModel[]|证书列表详情|
|**totalCount**|Integer|总数量|
### SslCertModel
|名称|类型|描述|
|---|---|---|
|**certId**|String|证书Id|
|**certName**|String|证书名称|
|**commonName**|String|绑定域名|
|**certType**|String|证书类型|
|**startTime**|String|开始时间|
|**endTime**|String|结束时间|
|**deletable**|Integer|是否允许被删除,1允许,0不允许|
|**digest**|String|对私钥文件使用sha256算法计算的摘要信息|
|**aliasName**|String|证书别名|
|**dnsNames**|String[]|域名|
|**downloadable**|Integer|是否允许被下载,0->不允许,1->允许|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
