# getAccessKeys


## 描述
根据userpin获取accessKey和accessKeySecret

## 请求方式
GET

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/accessKeys

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

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
|**data**|UserAccessKey|用户的AK/SK|
|**message**|String| |
|**status**|String| |
### UserAccessKey
|名称|类型|描述|
|---|---|---|
|**accessKey**|String|访问密钥，AccessKey用于程序方式调用云服务API|
|**accessKeySecret**|String|AccessKeySecret是用来验证用户的密钥|
|**account**|String|用户账号|
|**created**|String|创建时间|
|**expire**|String|到期时间|
|**id**|Integer|用户通行id|
|**modified**|String|更新时间|
|**modifier**|String|更新操作人|
|**pin**|String|用户名|
|**state**|Integer|状态|
|**yn**|Integer| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
