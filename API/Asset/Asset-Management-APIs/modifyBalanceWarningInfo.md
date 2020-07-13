# modifyBalanceWarningInfo


## 描述
设置余额预警信息

## 请求方式
POST

## 请求地址
https://asset.jcloud.com/v1/regions/{regionId}/assets:modifyBalanceWarningInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**balanceWarningInfoVo**|BalanceWarningInfoVo|True| | |

### BalanceWarningInfoVo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**status**|String|False| |余额预警状态:1-启用；2-停用（状态不为空时修改状态）|
|**threshold**|String|False| |余额预警阈值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**status**|Boolean| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|Not found|
|**400**|Invalid parameter|
|**500**|Internal server error|
|**502**|Internal server error|
