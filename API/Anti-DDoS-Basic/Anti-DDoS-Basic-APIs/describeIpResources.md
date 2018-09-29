# describeIpResources


## 描述
查询区域下的公网IP资源列表

## 请求方式
GET

## 请求地址
https://baseanti.jdcloud-api.com/v1/regions/{regionId}/ipResources

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ip**|String|True| |公网IP地址|
|**regionId**|String|True| |所属地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ip**|String|False| |IP模糊匹配|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|IpResource[]| |
|**totalCount**|Integer| |
### IpResource
|名称|类型|描述|
|---|---|---|
|**bandwidth**|Integer|带宽上限，单位Mbps|
|**ip**|String|公网IP地址|
|**safeStatus**|Integer|安全状态，0->安全 1->清洗 2->黑洞|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
