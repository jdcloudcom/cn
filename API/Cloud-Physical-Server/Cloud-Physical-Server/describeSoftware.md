# describeSoftware


## 描述
查询物理服务器可预装的软件列表<br/>
可调用接口（describeOS）获取云物理服务器支持的操作系统列表，根据不同的操作系统类型得到支持的可预装的软件列表<br/>


## 请求方式
GET

## 请求地址
https://cps.jdcloud-api.com/v1/regions/{regionId}/os/{osTypeId}/softwares

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**osTypeId**|String|True| |操作系统系统类型ID，调用接口（describeOS）获取云物理服务器支持的操作系统|
|**regionId**|String|True| |地域ID，可调用接口（describeRegiones）获取云物理服务器支持的地域|

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
|**softwares**|Software[]| |
### Software
|名称|类型|描述|
|---|---|---|
|**description**|String|软件包描述|
|**name**|String|软件包名称|
|**osTypeId**|String|操作系统系统类型ID|
|**version**|String|软件包版本|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
