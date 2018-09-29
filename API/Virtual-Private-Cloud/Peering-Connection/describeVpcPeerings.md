# describeVpcPeerings


## 描述
查询VpcPeering资源列表

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/vpcPeerings/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |vpcPeeringIds - vpcPeering ID，支持多个<br>vpcPeeringNames - vpcPeering名称列表，支持多个<br>vpcId	- vpcPeering本端Vpc Id，支持单个<br>remoteVpcId - vpcPeering对端Vpc Id，支持单个<br>|
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
|**totalCount**|Number|总数量|
|**vpcPeerings**|VpcPeering[]|VpcPeering资源信息列表|
### VpcPeering
|名称|类型|描述|
|---|---|---|
|**createdTime**|String|VpcPeering创建时间|
|**description**|String|VpcPeering 描述，可为空值，取值范围：0-256个中文、英文大小写的字母、数字和下划线分隔符|
|**remoteVpcInfo**|VpcPeeringVpcInfo|对端的Vpc信息|
|**vpcInfo**|VpcPeeringVpcInfo|发起VpcPeering的Vpc信息|
|**vpcPeeringId**|String|VpcPeering的Id|
|**vpcPeeringName**|String|VpcPeering名称，同账号下不允许重名，取值范围：1-32个中文、英文大小写的字母、数字和下划线分隔符|
|**vpcPeeringState**|String|状态，取值为Connected，Disconnected，Initiated|
### VpcPeeringVpcInfo
|名称|类型|描述|
|---|---|---|
|**addressPrefix**|String[]|如果为空，则不限制网段，如果不为空，10.0.0.0/8、172.16.0.0/12和192.168.0.0/16及它们包含的子网，且子网掩码长度为16-28之间|
|**vpcId**|String|子网所属VPC的Id|
|**vpcName**|String|私有网络名称，取值范围：1-60个中文、英文大小写的字母、数字和下划线分隔符|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
