# describePolicy


## 描述
查询策略详情

## 请求方式
GET

## 请求地址
https://iam.jdcloud-api.com/v1/policy/{policyName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**policyName**|String|True| |策略名称|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**policy**|PolicyDetail|策略信息|
### PolicyDetail
|名称|类型|描述|
|---|---|---|
|**policyId**|String|策略id|
|**name**|String|策略名称|
|**jrn**|String|京东云资源标识(jrn)|
|**description**|String|描述|
|**policyType**|String|策略类型|
|**version**|String|策略版本号|
|**defaultEdition**|Integer|默认策略文档版本|
|**content**|String|策略文档|
|**createTime**|String|策略创建时间|
|**updateTime**|String|策略更新时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
