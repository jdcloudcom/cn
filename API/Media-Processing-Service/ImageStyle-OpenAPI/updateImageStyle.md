# updateImageStyle


## 描述
修改图片样式

## 请求方式
PUT

## 请求地址
https://mps.jdcloud-api.com/v1/regions/{regionId}/buckets/{bucketName}/imageStyles/{id}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bucketName**|String|True| |Bucket名称|
|**id**|Integer|True| |图片样式id|
|**regionId**|String|True| |区域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bucketName**|String|False| |所属Bucket|
|**createdTime**|String|False| |创建时间|
|**id**|Integer|False| |图片样式id|
|**modifyTime**|String|False| |修改时间|
|**paramAlias**|String|False| |图片样式参数别名|
|**params**|String|False| |图片样式参数|
|**regionId**|String|False| |所属区域|
|**status**|Integer|False|1|图片样式状态|
|**styleName**|String|False| |图片样式名称|
|**ucUserId**|String|False| |用户id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |



## 返回码
|返回码|描述|
|---|---|
|**200**|successful operation|
