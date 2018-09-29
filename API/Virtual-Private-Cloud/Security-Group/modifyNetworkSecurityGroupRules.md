# modifyNetworkSecurityGroupRules


## 描述
修改安全组规则

## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkSecurityGroups/{networkSecurityGroupId}:modifyNetworkSecurityGroupRules

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkSecurityGroupId**|String|True| |NetworkSecurityGroup ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**modifySecurityGroupRuleSpecs**|ModifySecurityGroupRules[]|True| |安全组规则信息|

### ModifySecurityGroupRules
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**addressPrefix**|String|False| |安全组规则前缀，取值范围：正确的CIDR|
|**description**|String|False| |安全组规则的描述，取值范围：0-256个UTF-8编码下的全部字符|
|**fromPort**|Integer|False| |安全组规则的起始端口。取值范围：1-65535|
|**protocol**|Number|False| |规则限定协议。300:All; 6:TCP; 17:UDP; 1:ICMP|
|**ruleId**|String|True| |安全组规则的ID。|
|**toPort**|Integer|False| |安全组规则的终端口。取值范围：1-65535|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**400**|invalid parameter|
|**404**|SecurityGroup or SecurityGroupRule not found|
|**500**|Internal server error|
