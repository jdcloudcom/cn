# describeQuota


## 描述
查询配额信息

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/quotas/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**parentResourceId**|String|False| |type为vpc、elastic_ip、network_interface不设置, type为subnet、security_group、vpcpeering设置为vpcId|
|**type**|String|True| |资源类型，取值范围：vpc、elastic_ip、subnet、security_group、vpcpeering、network_interface（配额只统计辅助网卡）|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|返回结果|

### Result
|名称|类型|描述|
|---|---|---|
|**quota**|Object| |

## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**400**|invalid parameter|
|**500**|Internal server error|
