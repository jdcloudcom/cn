# createNamespace


## 描述
创建namespace

## 请求方式
POST

## 请求地址
https://streamcompute.jdcloud-api.com/v1/regions/{regionId}/namespace

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**namespaceStr**|Namespace|True| | |

### Namespace
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createTime**|String|False| | |
|**deleted**|Integer|False| | |
|**id**|Integer|False| | |
|**name**|String|False| | |
|**pods**|String|False| | |
|**podsUpdateTime**|String|False| | |
|**resourceId**|String|False| | |
|**sourceId**|String|False| | |
|**status**|String|False| | |
|**type**|String|False| | |
|**typeValue**|String|False| | |
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
|**status**|Boolean|创建成功标志|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|INTERNAL_ERROR|
