# modifyInstanceCC


## 描述
设置实例CC防护

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:setCC

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||所属地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cCSpec**|[CCSpec](##CCSpec)|True||cc参数|

### <a name="CCSpec">CCSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ccProtectMode**|Integer|False||cc防护模式，0->正常 1->宽松 2->紧急 3->自定义|
|**ccThreshold**|Integer|False||cc防护阈值大小|
|**hostQps**|Integer|False||ccProtectMode为自定义模式时，指定每个Host的防护阈值|
|**hostUrlQps**|Integer|False||ccProtectMode为自定义模式时，指定每个Host+URI的防护阈值|
|**ipHostQps**|Integer|False||ccProtectMode为自定义模式时，指定每个源IP对Host的防护阈值|
|**ipHostUrlQps**|Integer|False||ccProtectMode为自定义模式时，指定每个源IP对Host+URI的防护阈值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
