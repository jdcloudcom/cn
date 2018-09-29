# addNetworkSecurityGroupRules


## 描述
添加安全组规则

## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkSecurityGroups/{networkSecurityGroupId}:addNetworkSecurityGroupRules

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkSecurityGroupId**|String|True| |NetworkSecurityGroup ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkSecurityGroupRuleSpecs**|AddSecurityGroupRules[]|True| |安全组规则信息|

### AddSecurityGroupRules
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**addressPrefix**|String|True| |匹配地址前缀|
|**description**|String|False| |描述,​ 允许输入UTF-8编码下的全部字符，不超过256字符|
|**direction**|Number|True| |安全组规则方向。0：入规则; 1：出规则|
|**fromPort**|Number|False| |规则限定起始传输层端口, 取值范围:1-65535, 若protocol为传输层协议，默认值为1，若protocol不是传输层协议，恒为0。如果规则只限定一个端口号，fromPort和toPort填写同一个值|
|**protocol**|Number|True| |规则限定协议。300:All; 6:TCP; 17:UDP; 1:ICMP|
|**toPort**|Number|False| |规则限定终止传输层端口, 取值范围:1-65535, 若protocol为传输层协议，默认值为65535，若protocol不是传输层协议，恒为0。如果规则只限定一个端口号，fromPort和toPort填写同一个值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**400**|Request parameter x.y.z is 'xxx', expected one of [yyy,zzz]|
|**404**|Resource not found|
|**500**|Internal server error|
|**409**|SecurityGroup rules not in the same vpc|
