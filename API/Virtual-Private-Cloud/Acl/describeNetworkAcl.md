# describeNetworkAcl


## 描述
查询networkAcl资源详情

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkAcls/{networkAclId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkAclId**|String|True| |networkAclId ID|
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
|**networkAcl**|NetworkAcl|networkAcl资源信息|
### NetworkAcl
|名称|类型|描述|
|---|---|---|
|**createdTime**|String|networkAcl创建时间|
|**description**|String|描述,允许输入UTF-8编码下的全部字符，不超过256字符|
|**networkAclId**|String|networkAcl ID|
|**networkAclName**|String|networkAcl名称|
|**networkAclRules**|NetworkAclRule[]|networkAcl规则列表|
|**subnetIds**|String[]|networkAcl绑定的子网列表|
|**vpcId**|String|私有网络 ID|
### NetworkAclRule
|名称|类型|描述|
|---|---|---|
|**addressPrefix**|String|匹配地址前缀|
|**createdTime**|String|networkAclRule创建时间|
|**description**|String|描述,允许输入UTF-8编码下的全部字符，不超过256字符|
|**direction**|String|networkAcl规则方向。ingress：入规则; egress：出规则|
|**fromPort**|Integer|规则限定起始传输层端口, 取值范围:1-65535, 若protocol为传输层协议，默认值为1，若protocol不是传输层协议，设置无效，恒为0。如果规则只限定一个端口号，fromPort和toPort填写同一个值|
|**priority**|Integer|规则匹配优先级，取值范围为[1,32768]，优先级数字越小优先级越高|
|**protocol**|String|规则限定协议。取值范围：All,TCP,UDP,ICMP|
|**ruleAction**|String|访问控制策略：allow:允许，deny：拒绝|
|**ruleId**|String|networkAcl规则ID|
|**toPort**|Integer|规则限定终止传输层端口, 取值范围:1-65535, 若protocol为传输层协议，默认值为65535，若protocol不是传输层协议，设置无效，恒为0。如果规则只限定一个端口号，fromPort和toPort填写同一个值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**404**|Not found|
|**500**|Internal error|
|**401**|Authentication failed|
