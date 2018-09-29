# createNetworkInterface


## 描述
创建网卡接口，只能创建辅助网卡

## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkInterfaces/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|False| |可用区，用户的默认可用区|
|**description**|String|False| |描述,​ 允许输入UTF-8编码下的全部字符，不超过256字符|
|**networkInterfaceName**|String|False| |网卡名称，只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符。|
|**primaryIpAddress**|String|False| |网卡主IP，如果不指定，会自动从子网中分配|
|**sanityCheck**|Integer|False| |源和目标IP地址校验，取值为0或者1,默认为1|
|**secondaryIpAddresses**|String[]|False| |SecondaryIp列表|
|**secondaryIpCount**|Integer|False| |自动分配的SecondaryIp数量|
|**securityGroups**|String[]|False| |要绑定的安全组ID列表，最多指定5个安全组|
|**subnetId**|String|True| |子网ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|返回结果|

### Result
|名称|类型|描述|
|---|---|---|
|**networkInterfaceId**|String|弹性网卡Id|

## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**409**|Resource 'primaryIp' already be used|
|**404**|Resource 'subnetId' not found|
|**429**|NetworkInterface quota limit exceeded|
