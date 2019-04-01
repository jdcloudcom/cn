# describeCustomLiveStreamRecordTemplates


## 描述
查询用户自定义直播录制模板列表


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/recordCustoms:template


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNum**|Integer|False|1|页码<br>- 取值范围[1, 100000]<br>|
|**pageSize**|Integer|False|10|分页大小<br>- 取值范围[10, 100]<br>|
|**filters**|Filter[]|False| |录制模板列表查询过滤条件:<br>  - name:   template 录制模板自定义名称<br>  - value:  如果参数为空，则查询全部<br>|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**pageNumber**|Integer|当前页码|
|**pageSize**|Integer|每页数量|
|**totalCount**|Integer|查询总数|
|**recordTemplates**|RecordTemplate[]|录制模板信息|
### RecordTemplate
|名称|类型|描述|
|---|---|---|
|**recordPeriod**|Integer|自动录制周期<br>- 取值:[15,360]<br>- 单位: 分钟<br>|
|**saveBucket**|String|存储桶|
|**saveEndpoint**|String|存储地址|
|**recordFileType**|String|录制文件格式<br>- 取值: ts,flv,mp4 (多种类型之前用;隔开)<br>- 不区分大小写<br>|
|**template**|String|录制模板<br>- 取值要求：数字、大小写字母或短横线("-"),<br>          首尾不能有特殊字符("-")<br>- <b>注意: 不能与已定义命名重复</b><br>|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|

## 请求示例
GET
```
https://live.jdcloud-api.com/v1/recordCustoms:template?pageNum=1&pageSize=10&filters.1.name=template&filters.1.values.1=myrecordtemplate

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "pageNumber": 1, 
        "pageSize": 10, 
        "recordTemplates": [
            {
                "recordFileType": "mp4;flv", 
                "reordPeriod": 30, 
                "saveBucket": "testbucket", 
                "saveEndpoint": "oss.xxx.com", 
                "template": "myrecordtemplate"
            }
        ], 
        "totalCount": 1
    }
}
```
