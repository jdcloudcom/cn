# describeIpResourceProtectInfo


## 描述
查询公网IP的防护明细

## 请求方式
GET

## 请求地址
https://baseanti.jdcloud-api.com/v1/regions/{regionId}/ipResources/{ip}/protectInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ip**|String|True| |公网IP地址|
|**regionId**|String|True| |所属地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**limit**|Integer|False| |限制查询的记录数|
|**start**|Integer|False| |限制查询的开始范围|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|IpResourceProtectInfo[]| |
### IpResourceProtectInfo
|名称|类型|描述|
|---|---|---|
|**cause**|Integer|触发原因，0->未知 1->四层 2->七层 3->四和7层|
|**endTime**|String|攻击结束时间|
|**startTime**|String|攻击开始时间|
|**status**|Integer|状态，0->完成 1->清洗 2->黑洞|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
