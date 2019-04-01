# describeCustomLiveStreamWatermarkTemplates


## 描述
查询用户定义水印模板列表


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/watermarkCustoms


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNum**|Integer|False|1|页码<br>- 取值范围 [1, 100000]<br>|
|**pageSize**|Integer|False|10|分页大小<br>- 取值范围 [10, 100]<br>|
|**filters**|Filter[]|False| |水印模板列表查询过滤条件:<br>  - name:   template 录制模板自定义名称<br>  - value:  如果参数为空，则查询全部<br>|

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
|**watermarkTemplates**|WatermarkTemplate[]|水印模板|
### WatermarkTemplate
|名称|类型|描述|
|---|---|---|
|**offSetX**|Integer|x轴偏移量<br>- 单位: 像素<br>|
|**offSetY**|Integer|y轴偏移量<br>- 单位: 像素<br>|
|**width**|Integer|水印宽度<br>- 单位: 像素<br>|
|**height**|Integer|水印高度<br>- 单位: 像素<br>|
|**url**|String|水印地址<br>|
|**template**|String|水印模板自定义名称<br>|

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
https://live.jdcloud-api.com/v1/watermarkCustoms?filters.1.name=template&filters.1.values.1=yourwatermarktemplate

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "pageNumber": 1, 
        "pageSize": 100, 
        "totalCount": 2, 
        "watermarkTemplates": [
            {
                "height": 200, 
                "offSetX": 10, 
                "offSetY": 50, 
                "template": "yourwatermarktemplate", 
                "url": "http://xxx.com/xxx.jpg", 
                "width": 155
            }
        ]
    }
}
```
