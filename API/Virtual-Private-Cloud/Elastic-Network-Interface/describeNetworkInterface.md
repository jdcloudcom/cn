# describeNetworkInterface


## 描述
查询弹性网卡信息详情

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkInterfaces/{networkInterfaceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkInterfaceId**|String|True| |networkInterface ID|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|返回结果|

### Result
|名称|类型|描述|
|---|---|---|
|**networkInterface**|NetworkInterface|networkInterface资源信息|
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
