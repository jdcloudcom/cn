# describeNetworkSecurityGroup


## 描述
查询安全组信息详情

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkSecurityGroups/{networkSecurityGroupId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkSecurityGroupId**|String|True| |NetworkSecurityGroup ID|
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
|**networkSecurityGroup**|NetworkSecurityGroup|安全组资源信息|
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
