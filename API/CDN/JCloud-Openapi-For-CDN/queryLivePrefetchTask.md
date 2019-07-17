# queryLivePrefetchTask


## 描述
查询直播预热任务

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/task:queryLivePrefetchTask


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**urlList**|String[]|False| |预热的URL|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result|预热详情|
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**result**|QueryLivePrefetchItem[]| |
### QueryLivePrefetchItem
|名称|类型|描述|
|---|---|---|
|**stream**|String| |
|**code**|Integer| |
|**message**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
