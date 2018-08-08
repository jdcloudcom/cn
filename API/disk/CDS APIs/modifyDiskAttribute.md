# modifyDiskAttribute


## 描述
修改云硬盘的名字或描述信息

## 请求方式
PATCH

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/disks/{diskId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskId**|String|True||云硬盘ID|
|**regionId**|String|True||地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False||云硬盘描述，name和description必须要指定一个|
|**name**|String|False||云硬盘名称|


## 返回参数
|名称|类型|描述|
|---|---|---|



## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|

## 请求示例
PATCH
```

```

## 返回示例
无
