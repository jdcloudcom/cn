# describeSubnet


## 描述
查询子网信息详情

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/subnets/{subnetId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**subnetId**|String|True| |Subnet ID|

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
|**subnet**|Subnet|子网资源信息|
### Subnet
|名称|类型|描述|
|---|---|---|
|**aclId**|String|子网关联的acl Id|
|**addressPrefix**|String|子网网段，vpc内子网网段不能重叠，cidr的取值范围：10.0.0.0/8、172.16.0.0/12和192.168.0.0/16及它们包含的子网，且子网掩码长度为16-28之间，如果VPC含有Cidr，则必须为VPC所在Cidr的子网|
|**availableIpCount**|Number|子网可用ip数量|
|**createdTime**|String|子网创建时间|
|**description**|String|子网描述信息|
|**endIp**|String|子网的结束地址，子网第1个地位为路由器网关保留，第2个地址为dhcp服务保留|
|**routeTableId**|String|子网关联的路由表Id|
|**startIp**|String|子网的起始地址，子网第1个地位为路由器网关保留，第2个地址为dhcp服务保留|
|**subnetId**|String|Subnet的Id|
|**subnetName**|String|子网名称|
|**vpcId**|String|子网所属VPC的Id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
