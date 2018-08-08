# verifySessionToken


## 描述
验证SessionToken有效性

## 请求方式
POST

## 请求地址
https://iam.jdcloud-api.com/v1/regions/{regionId}/securityToken:verifySessionToken

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**verifySessionTokenInfo**|[VerifySessionTokenInfo](##VerifySessionTokenInfo)|True||验证sessionToken参数|

### <a name="VerifySessionTokenInfo">VerifySessionTokenInfo</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**businessAction**|String|True||操作action|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||



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
