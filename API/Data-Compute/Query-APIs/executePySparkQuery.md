# executePySparkQuery


## 描述
执行用户编写的PySpark脚本

## 请求方式
POST

## 请求地址
https://xdata.jdcloud-api.com/v1/regions/{regionId}/dwQuery:executePySparkQuery

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceName**|String|True| |实例名称|
|**instanceOwnerName**|String|False| |实例拥有者名称|
|**script**|String|True| |PySpark脚本|
|**scriptType**|String|False| |脚本类型名称|
|**userName**|String|True| |用户名称|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|Integer| |
|**message**|String| |
|**status**|Boolean| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
