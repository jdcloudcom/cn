# createSubUser


## 描述
创建子用户

## 请求方式
POST

## 请求地址
https://iam.jdcloud-api.com/v1/subUser


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createSubUserInfo**|CreateSubUserInfo|True| |子用户信息|

### CreateSubUserInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |子用户名，支持4~20位的字母，数字以及-和_，以字母开头|
|**description**|String|False| |描述，0~256个字符|
|**password**|String|True| |按照密码策略设置，默认8~20位，至少包含一个小写字母、大写字母和数字|
|**phone**|String|True| |手机号码，区号-手机号|
|**email**|String|True| |邮箱|
|**createAk**|Boolean|False| |是否创建accessKey，默认false|
|**needResetPassword**|Boolean|False| |子用户首次登录是否需要重置密码，默认false|
|**consoleLogin**|Boolean|False| |子用户是否支持控制台登录，默认true|
|**autoGeneratePassword**|Boolean|False| |是否自动生成密码，默认false|

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
