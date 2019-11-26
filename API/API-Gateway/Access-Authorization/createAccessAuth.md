# createAccessAuth


## 描述
创建访问授权

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/accessAuths

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accessAuthView**|[AccessAuthView](createaccessauth#accessauthview)|False| |api分组|

### <div id="accessauthview">AccessAuthView</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**authUserType**|String|False| |授权用户类型|
|**accessKey**|String|False| |Access Key|
|**deploymentIds**|String|False| |待绑定的部署ids逗号隔开|
|**description**|String|False| |描述|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createaccessauth#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**accessAuthId**|String|已创建访问授权ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
