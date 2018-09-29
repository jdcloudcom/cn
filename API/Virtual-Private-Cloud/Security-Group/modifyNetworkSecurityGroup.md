# modifyNetworkSecurityGroup


## 描述
修改安全组属性

## 请求方式
PATCH

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkSecurityGroups/{networkSecurityGroupId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkSecurityGroupId**|String|True| |NetworkSecurityGroup ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |安全组的描述，取值范围：0-256个UTF-8编码下的全部字符|
|**networkSecurityGroupName**|String|False| |安全组的名字。名称取值范围：1-32个中文、英文大小写的字母、数字和下划线分隔符|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Request parameter x.y.z is 'xxx', expected one of [yyy,zzz]|
|**404**|Resource not found|
