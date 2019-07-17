# describeSubUser


## 描述
查询子用户信息

## 请求方式
GET

## 请求地址
https://iam.jdcloud-api.com/v1/subUser/{subUser}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**subUser**|String|True| |子用户名|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**subUser**|SubUser| |
### SubUser
|名称|类型|描述|
|---|---|---|
|**name**|String|用户名|
|**phone**|String|手机号码|
|**email**|String|邮箱|
|**description**|String|描述信息|
|**account**|String|主账号|
|**createTime**|String|用户创建时间|
|**updateTime**|String|用户更新时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
