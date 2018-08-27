# listBuckets


## 描述
列出当前用户的所有bucket


## 请求方式
GET

## 请求地址
https://oss.jdcloud-api.com/v1/regions/{regionId}/buckets

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID，例如：cn-north-1|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**buckets**|[Bucket[]](##Bucket)||
|**owner**|[User](##User)||
### <a name="Bucket">Bucket</a>
|名称|类型|描述|
|---|---|---|
|**creationDate**|String||
|**name**|String||
### <a name="User">User</a>
|名称|类型|描述|
|---|---|---|
|**displayName**|String||
|**id**|String||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid Argument|
|**403**|Access Denied|
