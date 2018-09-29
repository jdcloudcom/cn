# describeIpResourceFlow


## 描述
查询公网IP的监控流量

## 请求方式
GET

## 请求地址
https://baseanti.jdcloud-api.com/v1/regions/{regionId}/ipResources/{ip}/monitorFlow

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ip**|String|True| |公网IP地址|
|**regionId**|String|True| |所属地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|False| |查询的结束时间，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ssZ|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|IpResourceFlow| |
### IpResourceFlow
|名称|类型|描述|
|---|---|---|
|**bps**|IpResourceFlowDetail| |
|**pps**|IpResourceFlowDetail| |
### IpResourceFlowDetail
|名称|类型|描述|
|---|---|---|
|**times**|String[]|时间点|
|**used**|Integer[]|对应时间点的使用值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
