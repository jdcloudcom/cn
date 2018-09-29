# deleteCluster


## 描述
对指定集群执行逻辑删除

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/cluster/{recordId}:delete

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**recordId**|String|True| |删除集群在数据库中的主键ID|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
