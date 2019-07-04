# deleteForbiddenStream


## 描述
删除禁播流

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/liveDomain/{domain}/stream:unForbidden

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**deleteStreams**|DeleteStream[]|False| |要删除的禁播流|

### DeleteStream
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**stream**|String|False| |禁播流|
|**app**|String|False| |封禁推流的app|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Object| |
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
