# listImageStyle


## 描述
图片样式列表

## 请求方式
GET

## 请求地址
https://mps.jdcloud-api.com/v1/regions/{regionId}/buckets/{bucketName}/imageStyles

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bucketName**|String|True||Bucket名称|
|**regionId**|String|True||区域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|数据页码|
|**pageSize**|Integer|False|10|每页数据的条数|
|**styleName**|String|False||按样式名称查询|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|Result||


### Result
|名称|类型|描述|
|---|---|---|
|**imageStyleQueryResult**|ImageStyleQueryResult||
### ImageStyleQueryResult
|名称|类型|描述|
|---|---|---|
|**imageStyleList**|ImageStyle[]|图片样式列表|
|**pageNumber**|Integer|数据页码|
|**pageSize**|Integer|每页数据的条数|
|**styleName**|String|按样式名称查询|
### ImageStyle
|名称|类型|描述|
|---|---|---|
|**bucketName**|String|所属Bucket|
|**createdTime**|String|创建时间|
|**id**|Integer|图片样式id|
|**modifyTime**|String|修改时间|
|**paramAlias**|String|图片样式参数别名|
|**params**|String|图片样式参数|
|**regionId**|String|所属区域|
|**status**|Integer|图片样式状态|
|**styleName**|String|图片样式名称|
|**ucUserId**|String|用户id|

## 返回码
|返回码|描述|
|---|---|
|**200**|success|
