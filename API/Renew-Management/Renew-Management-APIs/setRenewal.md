# setRenewal


## 描述
为一个或多个实例设置自动续费服务。

## 请求方式
PUT

## 请求地址
https://renewal.jdcloud-api.com/v2/regions/{regionId}/instances:autoRenewStatus

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**setRenewalParam**|SetRenewalParam|True| | |

### SetRenewalParam
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|True| |业务线|
|**serviceCode**|String|True| |产品线|
|**timeSpan**|Integer|False| |续费时长(timeUnit=MONTH时只能传1、2、3、4、5、6、7、8、9,timeUnit=YEAR时只能传1、2、3)|
|**timeUnit**|String|False| |时间单位(MONTH-月,YEAR-年)|
|**instanceIds**|String|True| |资源ID列表,英文逗号分隔|
|**autoRenewStatus**|String|True| |自动续费状态(OPEN-开通自动续费,CLOSE-关闭自动续费,MODIFY-修改自动续费)|
|**allAutoPay**|String|False| |是否绑定关联资源一并自动续费(AUTO_RENEW-是,UN_AUTO_RENEW-否)|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**stringResult**|String|设置成功条数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|Not found|
|**500**|Internal server error|
