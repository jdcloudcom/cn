# modifyDiskAttribute


## 描述
修改云硬盘的名字或描述信息，名字或描述信息至少要指定一个。

## 请求方式
PATCH

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/disks/{diskId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskId**|String|True| |云硬盘ID|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |云硬盘描述，允许输入UTF-8编码下的全部字符，不超过256字符。|
|**name**|String|False| |云硬盘名称，只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符。|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
