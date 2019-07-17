# queryMonitor


## 描述
查询源站监控信息

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}/monitor

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
|**domain**|String|域名|
|**cycle**|Integer|探测周期，单位分钟|
|**monitorPath**|String|探测路径|
|**httpRequestHeader**|Object|查询结果,类型为HashMap<String, Object>|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
