# createInstances


## 描述
创建一台或多台指定配置的云物理服务器<br/>
- 地域与可用区<br/>
  - 调用接口（describeRegiones）获取云物理服务器支持的地域与可用区<br/>
- 实例类型<br/>
  - 调用接口（describeDeviceTypes）获取物理实例类型列表<br/>
  - 不能使用已下线、或已售馨的实例类型<br/>
- 操作系统和预装软件<br/>
  - 可调用接口（describeOS）获取云物理服务器支持的操作系统列表<br/>
  - 可调用接口（describeSoftware）获取云物理服务器支持的软件列表，也可以不预装软件<br/>
- 存储<br/>
  - 数据盘多种RAID可选，可调用接口（describeDeviceRaids）获取服务器支持的RAID列表<br/>
- 网络<br/>
  - 网络类型目前只支持basic<br/>
  - 线路目前只支持bgp<br/>
  - 支持不启用外网，如果启用外网，带宽范围[1,200] 单位Mbps<br/>
- 其他<br/>
  - 购买时长，可按年或月购买，最少购买时长1个月，最长36个月（3年）<br/>
  - 密码设置参考公共参数规范<br/>


## 请求方式
PUT

## 请求地址
https://cps.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeRegiones）获取云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|False| |由客户端生成，用于保证请求的幂等性，长度不能超过36个字符；<br/><br>如果多个请求使用了相同的clientToken，只会执行第一个请求，之后的请求直接返回第一个请求的结果<br/><br>|
|**instanceSpec**|InstanceSpec|True| |描述云物理服务器配置|

### InstanceSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True| |可用区, 如 cn-east-1|
|**bandwidth**|Integer|False| |外网带宽, 范围[1,200] 单位Mbps|
|**charge**|ChargeSpec|True| |计费配置|
|**cidr**|String|False| |网络CIDR|
|**count**|Integer|True| |购买数量|
|**dataRaidTypeId**|String|True| |数据盘RAID类型ID|
|**description**|String|False| |云物理服务器描述|
|**deviceType**|String|True| |实例类型, 如 cps.c.normal|
|**enableInternet**|String|False|yes|是否启用外网，取值范围：yes、no|
|**imageType**|String|True| |镜像类型, 取值范围：standard、standard_app|
|**lineType**|String|False| |外网链路类型, 目前只支持bgp|
|**name**|String|True| |云物理服务器名称|
|**networkType**|String|True| |网络类型，目前只支持basic|
|**osTypeId**|String|True| |操作系统类型ID|
|**password**|String|True| |密码|
|**softwares**|Software[]|False| | |
|**subnetId**|String|False| |子网编号|
|**sysRaidTypeId**|String|True| |系统盘RAID类型ID|
### ChargeSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
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
|**instanceIds**|String[]| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
