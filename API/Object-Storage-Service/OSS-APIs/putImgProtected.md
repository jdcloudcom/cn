# putImgProtected


## 描述
创建原图保护


## 请求方式
PUT

## 请求地址
https://oss.jdcloud-api.com/v1/regions/{regionId}/buckets/{bucketname}:imgProtected

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bucketname**|String|True||Bucket Name，例如：test|
|**regionId**|String|True||Region ID，例如：cn-north-1|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**condition**|String|True||原图保护配置|


## 返回参数
|名称|类型|描述|
|---|---|---|



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid Argument|
|**403**|Access Denied|
|**409**|The requested bucket name is not available. The bucket namespace is shared by all users of the system. Please select a different name and try again.|
