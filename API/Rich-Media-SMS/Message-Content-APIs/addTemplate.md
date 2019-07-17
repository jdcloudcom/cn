# addTemplate


## 描述
增加富媒体短信内容接口

## 请求方式
POST

## 请求地址
https://rms.jdcloud-api.com/v2/regions/{regionId}/addTemplate

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True|cn-north-1|Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appId**|String|True| |应用ID|
|**signType**|String|True| |签名类型 0:公司 1:app 2:网站 3:公众号 4:商标 5:政府机关|
|**purpose**|String|True| |用途 0:自用 1:他用|
|**signCardType**|String|True| |资质证明类型 0:三证合一 1:企业营业执照 2:组织机构代码证书 3:社会信用代码证书|
|**aptitudes**|String|True| |资质证明图片必须是jpg图片的base64编码，只支持jpg图片|
|**title**|String|True| |多媒体内容的标题|
|**description**|String|True| |多媒体内容的描述|
|**unsubscribe**|String|True| |是否支持退订 0:不支持退订 1:支持退订|
|**content**|TemplateContent[]|True| |短信内容|

### TemplateContent
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**fileType**|String|True| |类型只能为 txt/jpg/png/gif/mp3/mp4|
|**value**|String|True| |类型为txt时，为文本信息；类型为非txt时，这里需要填写文件对应的base64编码|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|RespTemplateData|短信ID|
|**status**|Boolean|请求状态|
|**code**|String|错误码|
|**message**|String|错误消息|
### RespTemplateData
|名称|类型|描述|
|---|---|---|
|**templateId**|String|短信ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|INVALID_ARGUMENT|
|**500**|INTERNAL|
