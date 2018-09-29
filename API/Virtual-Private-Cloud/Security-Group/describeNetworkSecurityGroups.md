# describeNetworkSecurityGroups


## 描述
查询安全组列表

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkSecurityGroups/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |networkSecurityGroupIds - 安全组ID列表，支持多个<br>networkSecurityGroupNames - 安全组名称列表，支持多个<br>vpcId	- 安全组所属vpc Id，支持单个<br>|
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
|**networkSecurityGroups**|NetworkSecurityGroup[]|安全组资源信息列表|
|**totalCount**|Number|总数量|
### NetworkSecurityGroup
|名称|类型|描述|
|---|---|---|
|**createdTime**|String|安全组创建时间|
|**description**|String|安全组描述信息|
|**networkSecurityGroupId**|String|安全组ID|
|**networkSecurityGroupName**|String|安全组名称|
|**securityGroupRules**|SecurityGroupRule[]|安全组规则信息|
|**vpcId**|String|安全组所在vpc的Id|
### SecurityGroupRule
|名称|类型|描述|
|---|---|---|
|**addressPrefix**|String|匹配地址前缀|
|**createdTime**|String|安全组规则创建时间|
|**description**|String|描述,​ 允许输入UTF-8编码下的全部字符，不超过256字符|
|**direction**|Number|安全组规则方向。0：入规则; 1：出规则|
|**fromPort**|Number|规则限定起始传输层端口, 默认1 ，若protocal不是传输层协议，恒为0|
|**ipVersion**|Number|匹配地址协议版本。4：IPv4|
|**protocol**|Number|规则限定协议。300:All; 6:TCP; 17:UDP; 1:ICMP|
|**ruleId**|String|安全组规则ID|
|**toPort**|Number|规则限定终止传输层端口, 默认1 ，若protocal不是传输层协议，恒为0|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**401**|Authentication failed|
