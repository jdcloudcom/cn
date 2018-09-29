# describeContainers


## 描述
批量查询原生容器的详细信息<br>
此接口支持分页查询，默认每页20条。


## 请求方式
GET

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/containers

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |containerId - 实例ID，精确匹配，支持多个<br>privateIpAddress - 主网卡IP地址，模糊匹配，支持单个<br>az - 可用区，精确匹配，支持多个<br>vpcId - 私有网络ID，精确匹配，支持多个<br>status - 容器状态，精确匹配，支持多个<br>name - 实例名称，模糊匹配，支持单个<br>subnetId - 镜像ID，模糊匹配，支持单个<br>|
|**pageNumber**|Integer|False| |页码；默认为1|
|**pageSize**|Integer|False| |分页大小；默认为20；取值范围[10, 100]|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**containers**|Container[]| |
|**totalCount**|Number| |
### Container
|名称|类型|描述|
|---|---|---|
|**args**|String[]|容器执行命令的参数|
|**az**|String|可用区|
|**charge**|Charge|计费配置信息|
|**command**|String[]|容器执行命令|
|**containerId**|String|容器ID|
|**dataVolumes**|VolumeMount[]|挂载的数据Volume信息|
|**description**|String|容器描述|
|**elasticIpAddress**|String|主网卡主IP绑定弹性IP的地址|
|**elasticIpId**|String|主网卡主IP绑定弹性IP的ID|
|**envs**|EnvVar[]|动态指定的容器执行的环境变量|
|**hostAliases**|HostAlias[]|域名和IP映射的信息|
|**hostname**|String|主机名|
|**image**|String|镜像名称|
|**instanceType**|String|实例类型|
|**launchTime**|String|创建时间|
|**logConfiguration**|LogConfiguration|容器日志配置信息|
|**name**|String|容器名称|
|**primaryNetworkInterface**|InstanceNetworkInterfaceAttachment|主网卡信息|
|**privateIpAddress**|String|主网卡主IP地址|
|**reason**|String|容器终止原因|
|**rootVolume**|VolumeMount|根Volume信息|
|**secondaryNetworkInterfaces**|InstanceNetworkInterfaceAttachment[]|弹性网卡信息|
|**secret**|String|secret引用的名称|
|**status**|String|容器状态|
|**subnetId**|String|主网卡所属子网的ID|
|**tty**|Boolean|容器是否分配tty|
|**vpcId**|String|主网卡所属VPC的ID|
|**workingDir**|String|容器的工作目录|
### Charge
|名称|类型|描述|
|---|---|---|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
### VolumeMount
|名称|类型|描述|
|---|---|---|
|**autoDelete**|Boolean|自动删除，删除容器时自动删除此volume|
|**category**|String|环境变量名称|
|**cloudDisk**|InstanceCloudDisk|云硬盘规格|
|**fsType**|String|指定volume文件系统类型，目前支持[xfs, ext4]|
|**mountPath**|String|容器内的挂载目录|
|**readOnly**|Boolean|只读，默认false；只针对data volume有效，root volume为false|
### InstanceCloudDisk
|名称|类型|描述|
|---|---|---|
|**az**|String|所属AZ|
|**createTime**|String|创建时间|
|**description**|String|硬盘描述|
|**diskId**|String|云硬盘ID|
|**diskSize**|Integer|磁盘大小（GiB）|
|**diskType**|String|磁盘类型，取值为 ssd, premium-hdd 之一|
|**name**|String|硬盘名称|
|**status**|String|云硬盘状态，取值为 creating、available、in-use、extending、restoring、deleting、deleted、error_creating、error_deleting、error_restoring、error_extending 之一|
### EnvVar
|名称|类型|描述|
|---|---|---|
|**name**|String|环境变量名称|
|**value**|String|环境变量的值|
### HostAlias
|名称|类型|描述|
|---|---|---|
|**hostnames**|String[]|域名列表|
|**ip**|String|IP地址|
### LogConfiguration
|名称|类型|描述|
|---|---|---|
|**logDriver**|String|日志Driver名称  default：默认在本地分配10MB的存储空间，自动rotate|
|**options**|LogOption|日志Driver的配置选项|
### LogOption
|名称|类型|描述|
|---|---|---|
|**key**|String| |
|**value**|String| |
### InstanceNetworkInterfaceAttachment
|名称|类型|描述|
|---|---|---|
|**attachStatus**|String|绑定状态|
|**attachTime**|String|绑定时间|
|**autoDelete**|Boolean|指明删除实例时是否删除网卡|
|**deviceIndex**|Integer|设备Index|
|**networkInterface**|InstanceNetworkInterface|弹性网卡信息|
### InstanceNetworkInterface
|名称|类型|描述|
|---|---|---|
|**description**|String|描述|
|**macAddress**|String|以太网地址|
|**networkInterfaceId**|String|弹性网卡ID|
|**primaryIp**|NetworkInterfacePrivateIp|网卡主IP|
|**sanityCheck**|Boolean|源和目标IP地址校验，取值为0或者1|
|**secondaryIps**|NetworkInterfacePrivateIp[]| |
|**securityGroups**|SecurityGroupSimple[]|安全组列表|
|**vpcId**|String|虚拟网络ID|
### NetworkInterfacePrivateIp
|名称|类型|描述|
|---|---|---|
|**elasticIpAddress**|String|弹性IP实例地址|
|**elasticIpId**|String|私有IP的IPV4地址|
|**privateIpAddress**|String|私有IP的IPV4地址|
### SecurityGroupSimple
|名称|类型|描述|
|---|---|---|
|**groupId**|String|安全组ID|
|**groupName**|String|安全组名称|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
