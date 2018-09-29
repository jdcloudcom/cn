# describeNetworkInterfaces


## 描述
查询弹性网卡列表

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkInterfaces/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |networkInterfaceIds - 弹性网卡ID列表，支持多个<br>networkInterfaceNames - 弹性网卡名称列表，支持多个<br>vpcId - 弹性网卡所属vpc Id，支持单个<br>subnetId	- 弹性网卡所属子网Id，支持单个<br>role - 网卡角色，取值范围：Primary（主网卡）、Secondary（辅助网卡），支持单个<br>|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞), 页码超过总页数时, 显示最后一页|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|返回结果|

### Result
|名称|类型|描述|
|---|---|---|
|**networkInterfaces**|NetworkInterface[]|networkInterface资源信息列表|
|**totalCount**|Number|总数量|
### NetworkInterface
|名称|类型|描述|
|---|---|---|
|**az**|String|可用区名称|
|**createdTime**|String|弹性网卡创建时间|
|**description**|String|网卡描述信息|
|**deviceIndex**|Integer|网卡在实例上的设备索引号，取值范围：[0,8]，0：辅助网卡未绑定设备，1：主网卡，2-8：辅助网卡已绑定设备|
|**instanceId**|String|关联实例ID|
|**instanceOwnerId**|String|实例所属的账号|
|**instanceType**|String|关联实例类型，取值范围：vm|
|**macAddress**|String|以太网地址|
|**networkInterfaceId**|String|弹性网卡ID|
|**networkInterfaceName**|String|弹性网卡名称|
|**networkSecurityGroupIds**|String[]|安全组ID列表|
|**primaryIp**|NetworkInterfacePrivateIp|网卡主IP|
|**role**|String|网卡角色，取值范围：Primary（主网卡）、Secondary（辅助网卡）|
|**sanityCheck**|Integer|源和目标IP地址校验，取值为0或者1|
|**secondaryIps**|NetworkInterfacePrivateIp[]|网卡附属IP列表|
|**subnetId**|String|子网ID|
|**vpcId**|String|虚拟网络ID|
### NetworkInterfacePrivateIp
|名称|类型|描述|
|---|---|---|
|**elasticIpAddress**|String|弹性IP实例地址|
|**elasticIpId**|String|弹性IP实例ID|
|**privateIpAddress**|String|私有IP的IPV4地址|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**401**|Authentication failed|
