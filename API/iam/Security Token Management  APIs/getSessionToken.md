# getSessionToken


## 描述
获取SessionToken

## 请求方式
POST

## 请求地址
https://iam.jdcloud-api.com/v1/regions/{regionId}/securityToken:getSessionToken

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**getSessionTokenInfo**|[GetSessionTokenInfo](##GetSessionTokenInfo)|True||获取sessionToken参数|

### <a name="GetSessionTokenInfo">GetSessionTokenInfo</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**businessAction**|String|True||操作action|
|**code**|String|True||验证码|
|**durationSeconds**|Integer|False||令牌有效期，单位秒，OpenAPI第三方MFA方式验证有效，默认短信、邮箱token有效期300秒，MFA有效期30秒|
|**type**|Integer|True||操作保护验证方式：1-短信,2-邮箱,3-MFA|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**sessionToken**|String|安全令牌|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
POST
```

```

## 返回示例
无
