# updateSubUser


## 描述
修改子用户信息

## 请求方式
PUT

## 请求地址
https://iam.jdcloud-api.com/v1/subUser/{subUser}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**subUser**|String|True| |子用户名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**updateSubUserInfo**|UpdateSubUserInfo|True| |子用户信息|

### UpdateSubUserInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |描述，0~256个字符|
|**phone**|String|False| |手机号码，区号-手机号|
|**email**|String|False| |邮箱|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**subUser**|CreateSubUserRes| |
### CreateSubUserRes
|名称|类型|描述|
|---|---|---|
|**name**|String|用户名|
|**password**|String|密码|
|**email**|String|邮箱|
|**accessKey**|String|accessKey|
|**secretAccessKey**|String|AccessKey secret|
|**createTime**|String|创建时间|
|**updateTime**|String|更新时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
