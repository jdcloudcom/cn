# setHttpType


## 描述
设置http协议

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}/httpType

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**httpType**|String|False| |http类型,只能为http或者https,默认为http.当设为https时,需要调用“设置通讯协议”接口上传证书和私钥|
|**certificate**|String|False| |用户证书,当Type为https时必须设置|
|**rsaKey**|String|False| |证书私钥|
|**jumpType**|String|False| |有三种类型：default、http、https|
|**certFrom**|String|False| |证书来源有两种类型：default,ssl|
|**sslCertId**|String|False| |ssl证书id|
|**syncToSsl**|Boolean|False| |是否同步到ssl,boolean值，取值true或者false|
|**certName**|String|False| |syncToSsl是true时，certName是必填项|


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
