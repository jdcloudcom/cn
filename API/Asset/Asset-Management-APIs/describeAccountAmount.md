# describeAccountAmount


## 描述
查询账户金额（总金额、可用金额、冻结金额、可提现金额、提现中金额）

## 请求方式
GET

## 请求地址
https://asset.jcloud.com/v1/regions/{regionId}/assets:describeAccountAmount

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域|

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
|**totalAmount**|String|总金额：可用金额+冻结金额|
|**availableAmount**|String|可用金额|
|**frozenAmount**|String|冻结金额：提现失败、处理中或预占中金额|
|**enableWithdrawAmount**|String|可提现金额：排除对公充值金额总额后的充值总额，如果余额大于非对公充值总额,则为非对公充值总额，否则为余额（对公充值=企业线下汇款+企业充值+活动充值金额）|
|**withdrawingAmount**|String|提现中金额：提现状态为处理中和预占中的金额|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|Not found|
|**400**|Invalid parameter|
|**500**|Internal server error|
|**502**|Internal server error|
