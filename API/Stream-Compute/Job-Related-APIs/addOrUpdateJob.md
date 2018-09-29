# addOrUpdateJob


## 描述
添加或者更新job

## 请求方式
POST

## 请求地址
https://streamcompute.jdcloud-api.com/v1/regions/{regionId}/job

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**jobStr**|JobStr|True| |创建作业的详情|

### JobStr
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appName**|String|False| | |
|**createTime**|String|False| | |
|**deleted**|String|False| | |
|**description**|String|False| | |
|**duration**|Integer|False| | |
|**id**|Integer|False| | |
|**jobType**|String|False| | |
|**name**|String|False| | |
|**namespaceId**|String|False| | |
|**resourceConsume**|Integer|False| | |
|**sqlStatement**|String|False| | |
|**status**|String|False| | |
|**uid**|String|False| | |
|**updateTime**|String|False| | |
|**userName**|String|False| | |

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**okInfo**|OkInfo|成功结果对象|
### OkInfo
|名称|类型|描述|
|---|---|---|
|**message**|String|状态信息|
|**status**|Boolean| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|INTERNAL_ERROR|
