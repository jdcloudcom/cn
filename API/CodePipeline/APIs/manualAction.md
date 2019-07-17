# manualAction


## 描述
查询多个指定流水线执行及状态信息


## 请求方式
POST

## 请求地址
https://pipeline.jdcloud-api.com/v1/regions/{regionId}/pipeline/{uuid}/instances/{instanceUuid}/actions/{actionUuid}:manual

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**uuid**|String|True| |流水线uuid|
|**instanceUuid**|String|True| |流水线实例uuid|
|**actionUuid**|String|True| |动作UUID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**status**|String|True| |手动设置的状态，如SUCCESS,FAILED|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**instanceUuid**|String| |
|**actionUuid**|String| |
|**result**|Bool| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
