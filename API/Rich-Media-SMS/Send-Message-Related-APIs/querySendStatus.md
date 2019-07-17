# querySendStatus


## 描述
获取发送状态

## 请求方式
POST

## 请求地址
https://rms.jdcloud-api.com/v2/regions/{regionId}/querySendStatus

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True|cn-north-1|Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appId**|String|True| |应用ID|
|**sequenceNumber**|String|True| |序列号|
|**phone**|String|False| |手机号|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|QuerySendStatus[]|发送状态响应参数|
|**status**|Boolean|请求状态|
|**code**|String|错误码|
|**message**|String|错误消息|
### QuerySendStatus
|名称|类型|描述|
|---|---|---|
|**total**|Integer|总量|
|**detailList**|SendStatus[]|发送信息明细列表|
### SendStatus
|名称|类型|描述|
|---|---|---|
|**pin**|String|用户pin|
|**appId**|String|应用ID|
|**sequenceNumber**|String|任务序列号|
|**templateId**|String|短信ID|
|**mobileNum**|String|手机号|
|**stateFlag**|Integer|发送状态 -1：初始状态；0：成功发送到网关；1：下载成功；2：发送失败；3：未发送至网关，过期失败；4：发送到网关，过期失败|
|**sendTime**|String|发送时间 yyyy-MM-dd HH:mm:ss|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|INVALID_ARGUMENT|
|**500**|INTERNAL|
