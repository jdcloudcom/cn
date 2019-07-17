# createPolicy


## 描述
创建策略

## 请求方式
POST

## 请求地址
https://iam.jdcloud-api.com/v1/policy


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createPolicyInfo**|CreatePolicyInfo|True| |策略信息|

### CreatePolicyInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |策略名，支持4~64位的字母，数字以及-和_, 以字母开头|
|**description**|String|False| |描述，0~256个字符|
|**content**|String|True| |策略文档，最多6144个字符|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**policy**|Policy|策略信息|
### Policy
|名称|类型|描述|
|---|---|---|
|**policyId**|String|策略id|
|**name**|String|策略名称|
|**jrn**|String|京东云资源标识(jrn)|
|**description**|String|描述|
|**policyType**|String|策略类型：0-系统策略，1-用户策略|
|**version**|String|策略版本号|
|**defaultEdition**|Integer|默认策略文档版本|
|**createTime**|String|策略创建时间|
|**updateTime**|String|策略更新时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
