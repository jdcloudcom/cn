# queryPushDomainORAppOrStream


## 描述
查询用户推流域名app名/流名

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/liveDomain/{domain}/stream:fuzzyQuery

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**app**|String|False| |app名，传appName查询流名列表|
|**stream**|String|False| |流名模糊查询|
|**limit**|Long|False|50|指定app/流名列表大小，默认50|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**streams**|String[]| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
