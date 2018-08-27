# addMonitor


## 描述
添加子域名的监控项，采用默认配置

## 请求方式
POST

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domain/{domainId}/monitorAdd

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainId**|String|True||域名ID|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**subDomainName**|String|True||子域名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
