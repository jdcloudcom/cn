# createSecret


## 描述
创建 secret

## 请求方式
POST

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/secrets

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**data**|[DockerRegistryData](##DockerRegistryData)|False||机密的数据|
|**name**|String|True||机密数据名称，不能重复|
|**secretType**|String|True||私密数据的类型，目前仅支持如下类型：docker-registry：用来和docker registry认证的类型|

### <a name="DockerRegistryData">DockerRegistryData</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**email**|String|False||邮件地址|
|**password**|String|True||密码|
|**server**|String|True||registry服务器地址|
|**username**|String|True||用户名|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**secretName**|String||

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**500**|Internal server error|
|**503**|Service unavailable|
|**200**|OK|
|**404**|Not found|
|**429**|Quota exceeded|

## 请求示例
POST
```

```

## 返回示例
无
