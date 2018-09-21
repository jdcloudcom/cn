# createSubuser


## 描述
创建子账号

## 请求方式
POST

## 请求地址
https://iam.jdcloud-api.com/v1/regions/{regionId}/subUser

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createSubUserInfo**|CreateSubUserInfo|True||子账号信息|

### CreateSubUserInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createAk**|Boolean|True||是否创建accessKey|
|**description**|String|False||描述，0~256个字符|
|**email**|String|True||邮箱|
|**name**|String|True||子账号用户名，4~20位数字、字母、中文、下划线、中划线|
|**password**|String|True||密码，6~20位，至少包含一个字母，至少包含一个数字或半角符号|
|**passwordConfirm**|String|True||确认密码|
|**phone**|String|True||手机号码，区号-手机号，目前只支持0086-中国手机号码|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
