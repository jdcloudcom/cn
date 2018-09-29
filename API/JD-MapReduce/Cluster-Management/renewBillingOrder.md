# renewBillingOrder


## 描述
对指定集群按照指定的续费方式进行续费

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/BillingOrder:renew

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clusterId**|String|True| |续费集群clusterId|
|**type**|Integer|True| |"必传参数，计费类型"<br>      "* 1:按配置"<br>      "* 601-609：包年包月1一个月到9个月"<br>      "* 610:包年包月一年"<br>      "* 620:包年包月两年"<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
