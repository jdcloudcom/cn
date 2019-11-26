# batchOffline


## 描述
批量下线

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/deployments:offline

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**deploymentIds**|String|False| |要删除的部署ID集合，以,分隔|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](batchoffline#result)| |
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**successCount**|Integer|操作成功的资源个数|
|**failed**|[ErrorItem[]](batchoffline#erroritem)|操作失败的资源及原因|
### <div id="erroritem">ErrorItem</div>
|名称|类型|描述|
|---|---|---|
|**id**|String|出错资源ID|
|**code**|Long|错误码，同标准code|
|**details**|Object| |
|**message**|String| |
|**status**|String|具体错误，同标准status|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
