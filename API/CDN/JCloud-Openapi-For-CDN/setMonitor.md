# setMonitor


## 描述
设置源站监控信息

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}/monitor

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cycle**|Integer|False| |探测周期，取值1和5，单位为分钟|
|**monitorPath**|String|False| |探测路径|
|**httpRequestHeader**|Object|False| |http请求头|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**monitorId**|Long| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
