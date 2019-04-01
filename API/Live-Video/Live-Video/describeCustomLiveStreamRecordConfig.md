# describeCustomLiveStreamRecordConfig


## 描述
查询直播直播录制配置
- 录制模板配置按照 域名,应用,流 3级配置添加,以最小的粒度配置生效
- 域名、应用、流 依次粒度递减 即: 域名>应用>流
- 该查询旨在查询域名、应用、流最终生效的录制模板配置,并非各级的模板绑定情况


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/records:config


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNum**|Integer|False|1|页码<br>- 取值范围 [1, 100000]<br>|
|**pageSize**|Integer|False|10|分页大小<br>- 取值范围 [10, 100]<br>|
|**filters**|Filter[]|False| |录制配置查询过滤条件:<br>  - name:   publishDomain，必填(推流域名)<br>  - value:  参数<br>  - name:   appName，必填(应用名称)<br>  - value:  参数<br>  - name:   streamName，非必填(流名称)<br>  - value:  参数<br>|

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
|**recordConfigs**|LiveRecordConfig[]|模板信息|
### LiveRecordConfig
|名称|类型|描述|
|---|---|---|
|**publishDomain**|String|推流域名|
|**appName**|String|应用名称|
|**streamName**|String|流名称|
|**recordConfig**|String| |

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
https://live.jdcloud-api.com/v1/records:config?filters.1.name=publishDomain&filters.1.values.1=push.yourdomain.com&filters.2.name=appName&filters.2.values.1=yourapp&filters.3.name=streamName&filters.3.values.1=yourstream

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "pageNumber": 1, 
        "pageSize": 100, 
        "recordConfigs": [
            {
                "appName": "yourapp", 
                "publishDomain": "push.yourdomain.com", 
                "recordConfig": [
                    "yourrecordtemplate"
                ], 
                "streamName": "yourstream"
            }
        ], 
        "totalCount": 2
    }
}
```
