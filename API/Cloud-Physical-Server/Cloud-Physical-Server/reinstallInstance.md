# reinstallInstance


## 描述
重装云物理服务器，只能重装stopped状态的服务器<br/>
- 可调用接口（describeOS）获取云物理服务器支持的操作系统列表
- 可调用接口（describeSoftware）获取云物理服务器支持的软件列表，也可以不预装软件


## 请求方式
PUT

## 请求地址
https://cps.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:reinstallInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |云物理服务器ID|
|**regionId**|String|True| |地域ID，可调用接口（describeRegiones）获取云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|False| |由客户端生成，用于保证请求的幂等性，长度不能超过36个字符；<br/><br>如果多个请求使用了相同的clientToken，只会执行第一个请求，之后的请求直接返回第一个请求的结果<br/><br>|
|**instanceSpec**|ReinstallInstanceSpec|True| |云物理服务器配置|

### ReinstallInstanceSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True| |可用区, 如cn-east-1a|
|**dataRaidTypeId**|String|True| |数据盘RAID类型ID|
|**imageType**|String|True| |镜像类型, 取值范围：standard、standard_app|
|**keepData**|String|True| |是否保留数据盘数据, 取值为：yes、no|
|**osTypeId**|String|True| |操作系统类型ID|
|**password**|String|True| |密码|
|**softwares**|Software[]|False| | |
|**sysRaidTypeId**|String|True| |系统盘RAID类型ID|
### Software
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |软件包描述|
|**name**|String|False| |软件包名称|
|**osTypeId**|String|False| |操作系统系统类型ID|
|**version**|String|False| |软件包版本|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**success**|Boolean|重装操作是否成功|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
