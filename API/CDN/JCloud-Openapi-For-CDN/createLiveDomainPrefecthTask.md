# createLiveDomainPrefecthTask


## 描述
创建直播预热任务

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/task:createLivePrefetchTask


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**urlList**|String[]|False| |预热的URL|
|**prefetchTime**|Integer|False| |预热时长|
|**action**|String|False| |操作类型只能是[start,stop]中的一种|


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
