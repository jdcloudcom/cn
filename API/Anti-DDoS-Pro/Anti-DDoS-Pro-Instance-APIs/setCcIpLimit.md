# setCCIpLimit


## 描述
设置实例 CC 防护每 IP 限速

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:setCCIpLimit

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cCSpec**|CcIpLimitSpec|True| |CC 参数|

### CcIpLimitSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ccSpeedLimit**|Integer|False| |cc防护每ip的限速大小|
|**ccSpeedPeriod**|Integer|False| |cc防护每ip的限速大小的统计周期|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
