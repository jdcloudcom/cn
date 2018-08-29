# updateBucketMaxCount


## 描述
更新bucket最大数量


## 请求方式
POST

## 请求地址
https://oss.jdcloud-api.com/v1/regions/{regionId}/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID，例如：cn-north-1|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bucketmaxcount**|Integer|True||bucket最大数量，例如：50，最低20|
|**userpin**|String|True||指定user的pin|


## 返回参数
|名称|类型|描述|
|---|---|---|



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid Argument|
|**403**|Access Denied|
