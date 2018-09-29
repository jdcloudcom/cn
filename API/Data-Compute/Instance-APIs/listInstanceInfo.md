# listInstanceInfo


## 描述
查询用户所属的实例信息

## 请求方式
GET

## 请求地址
https://xdata.jdcloud-api.com/v1/regions/{regionId}/dwInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|DwInstance[]| |
|**message**|String| |
|**status**|Boolean| |
### DwInstance
|名称|类型|描述|
|---|---|---|
|**area**|String|实例所属区域|
|**comments**|String|实例描述|
|**createTime**|String|实例创建时间|
|**instanceName**|String|实例名|
|**instanceOwnerName**|String|实例属主|
|**uname**|String|实例别名（在页面显示）|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
