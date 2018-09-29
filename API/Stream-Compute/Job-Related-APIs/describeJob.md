# describeJob


## 描述
查询指定作业详情

## 请求方式
GET

## 请求地址
https://streamcompute.jdcloud-api.com/v1/regions/{regionId}/job

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**jobId**|Integer|True| | |
|**namespaceId**|Integer|True| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**jobStr**|JobStr| |
### JobStr
|名称|类型|描述|
|---|---|---|
|**appName**|String| |
|**createTime**|String| |
|**deleted**|String| |
|**description**|String| |
|**duration**|Integer| |
|**id**|Integer| |
|**jobType**|String| |
|**name**|String| |
|**namespaceId**|String| |
|**resourceConsume**|Integer| |
|**sqlStatement**|String| |
|**status**|String| |
|**uid**|String| |
|**updateTime**|String| |
|**userName**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|INTERNAL_ERROR|
