# getSoftwareAndVersionInfo


## 描述
获取指定JMR版本对应软件清单以及版本信息

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/softwareInfo/v2

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ver**|String|True| |JMR软件版本号|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|SoftwareInfoAndVersion[]| |
|**message**|String| |
|**status**|String| |
### SoftwareInfoAndVersion
|名称|类型|描述|
|---|---|---|
|**flag**|Boolean|表示获取信息是否正常|
|**name**|String|所用软件名称，如hadoop/spark|
|**version**|String|软件当前版本|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
