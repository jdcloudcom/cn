# setProtocolConvert


## 描述
设置转协议

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/liveDomain/{domain}/protocolConvert

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**certificate**|String|False| |https证书,转https格式时必传|
|**rsaKey**|String|False| |https私钥，转https格式时必传|
|**certFrom**|String|False| |证书来源有两种类型：default,ssl|
|**sslCertId**|String|False| |ssl证书id|
|**syncToSsl**|Boolean|False| |是否同步到ssl,boolean值，取值true或者false|
|**certName**|String|False| |syncToSsl是true时，certName是必填项|
|**protocolConverts**|ProtocolConvert[]|False| | |

### ProtocolConvert
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**sourceProtocol**|String|False| |源协议,目前只能为rtmp|
|**targetProtocol**|String|False| |目标协议|

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
