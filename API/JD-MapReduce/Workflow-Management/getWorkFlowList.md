# getWorkFlowList


## 描述
获取工作流列表

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/{workflowName}:list

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**workflowName**|String|True| |工作流名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**selectParams**|SelectParams|False| | |

### SelectParams
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**orderBy**|String|False| |排序条件，可选|
|**pageNum**|Integer|False| |搜索分页页数，可选条件|
|**pageSize**|Integer|False| |搜索分页大小，可选条件|
|**status**|String|False| | |

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|Object| |
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
