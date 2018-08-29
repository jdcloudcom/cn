# setCcIpLimit


## 描述
设置实例CC防护每IP限速

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:setCcIpLimit

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||所属地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cCSpec**|[CcIpLimitSpec](##CcIpLimitSpec)|True||cc参数|

### <a name="CcIpLimitSpec">CcIpLimitSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ccSpeedLimit**|Integer|False||cc防护每个IP的限速大小|
|**ccSpeedPeriod**|Integer|False||cc防护每个IP的限速大小的统计周期|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
