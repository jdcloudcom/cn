# queryTemplateList


## 描述
查询富媒体短信内容列表接口

## 请求方式
POST

## 请求地址
https://rms.jdcloud-api.com/v2/regions/{regionId}/queryTemplateList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True|cn-north-1|Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appId**|String|True| |应用ID|
|**title**|String|False| |查询标题关键词|
|**pageNum**|Integer|True| |第几页|
|**pageLimit**|Integer|True| |每页多少条记录|
|**status**|String|False| |审核状态：0: 审核中 1: 通过 2: 未通过 4:待提交|
|**startTime**|String|False| |开始时间,格式YYYY-MM-DD|
|**endTime**|String|False| |结束时间,格式YYYY-MM-DD|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|RespTemplatePageResult| |
|**status**|Boolean|请求状态|
|**code**|String|错误码|
|**message**|String|错误消息|
### RespTemplatePageResult
|名称|类型|描述|
|---|---|---|
|**count**|Long|总条数|
|**pageNum**|Integer|当前页|
|**pageSize**|Integer|每页条数|
|**pageCount**|Integer|总页数|
|**list**|RespQueryTemplateListData[]|数据|
### RespQueryTemplateListData
|名称|类型|描述|
|---|---|---|
|**templateId**|String|短信ID|
|**title**|String|短信标题|
|**status**|String|审核状态 0: 审核中 1: 通过 2: 未通过 4:待提交|
|**reason**|String|审核未通过原因|
|**createTime**|String|短信创建时间 yyyy-MM-dd HH:mm:ss|
|**contentSize**|String|短信内容大小|
|**aptitudesId**|String|资质Id|
|**description**|String|短信描述|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|INVALID_ARGUMENT|
|**500**|INTERNAL|
