# renewInstance


## 描述
对相关实例进行续费。调用该接口会创建一个续费订单，并自动扣除您账户可用代金券和余额完成支付，如因为某些原因支付失败，订单会自动取消。

## 请求方式
POST

## 请求地址
https://renewal.jdcloud-api.com/v2/regions/{regionId}/instances:renew

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**renewInstanceParam**|RenewInstanceParam|True| | |

### RenewInstanceParam
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|True| |业务线|
|**serviceCode**|String|True| |产品线|
|**timeSpan**|Integer|True| |续费时长(timeUnit=MONTH时只能传1、2、3、4、5、6、7、8、9,timeUnit=YEAR时只能传1、2、3)|
|**timeUnit**|String|True| |时间单位(MONTH-月,YEAR-年)|
|**instanceIds**|String|True| |待续费资源ID列表,英文逗号分隔|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**orderNumber**|String|创建成功的订单ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|Not found|
|**500**|Internal server error|
