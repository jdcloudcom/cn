# queryNamespaceDetail


## 描述
查询某个应用详情

## 请求方式
GET

## 请求地址
https://streamcompute.jdcloud-api.com/v1/regions/{regionId}/namespaceDetail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**namespaceId**|Integer|True| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**namespace**|Namespace|查询出的namespace对象|
### Namespace
|名称|类型|描述|
|---|---|---|
|**createTime**|String| |
|**deleted**|Integer| |
|**id**|Integer| |
|**name**|String| |
|**pods**|String| |
|**podsUpdateTime**|String| |
|**resourceId**|String| |
|**sourceId**|String| |
|**status**|String| |
|**type**|String| |
|**typeValue**|String| |
|**updateTime**|String| |
|**userName**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|INTERNAL_ERROR|
