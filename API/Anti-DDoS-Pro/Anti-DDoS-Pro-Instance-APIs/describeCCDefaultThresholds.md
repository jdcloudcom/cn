# describeCCDefaultThresholds


## 描述
查询 CC 自定义默认阈值

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instance/describeCCDefaultThresholds

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|CCDefaultThresholds| |
### CCDefaultThresholds
|名称|类型|描述|
|---|---|---|
|**hostQps**|Integer|每个 Host 的防护阈值|
|**hostUrlQps**|Integer|每个 Host + URL 的防护阈值|
|**ipHostQps**|Integer|每个源 IP 对 Host 的防护阈值|
|**ipHostUrlQps**|Integer|每个源 IP 对 Host + URI 的防护阈值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
