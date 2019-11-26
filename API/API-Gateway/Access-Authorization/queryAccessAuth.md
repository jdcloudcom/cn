# queryAccessAuth


## 描述
查询单个访问授权

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/accessAuths/{accessAuthId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**accessAuthId**|String|True| |访问授权ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryaccessauth#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**accessAuth**|[AccessAuth](queryaccessauth#accessauth)| |
### <div id="accessauth">AccessAuth</div>
|名称|类型|描述|
|---|---|---|
|**accessAuthId**|String|访问授权ID|
|**authUserType**|String|授权用户类型|
|**accessKey**|String|Access Key|
|**description**|String|描述|
|**bindGroups**|String|绑定分组,用英文逗号分隔|
|**appId**|String|api调用者的appid|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
