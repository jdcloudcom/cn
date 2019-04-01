# describeLiveApp


## 描述
查询域名下的APP列表

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/apps


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNum**|Integer|False|1|页码<br>- 取值范围: [1, 100000]<br>|
|**pageSize**|Integer|False|10|分页大小<br>- 取值范围: [10, 100]<br>|
|**filters**|Filter[]|False| |域名下的app列表过滤条件:<br>  - name: publishDomain 直播的推流域名<br>  - values: 如果参数为空,则查询全部<br>  - 过滤条件为空,则表示查询用户下的所有应用名<br>|

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
|**apps**|App[]|app列表|
### App
|名称|类型|描述|
|---|---|---|
|**appName**|String|应用名称|
|**appStatus**|String|应用状态<br>  online: 开启<br>  offline: 关闭<br>|
|**createTime**|String|应用创建时间<br>- UTC时间<br>  格式: yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**updateTime**|String|更新时间|

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
https://live.jdcloud-api.com/v1/apps?pageNumber=1&pageSize=10&filters.1.name=publishDomain&filters.1.values.1=push.yourdomain.com

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "apps": [
            {
                "appName": "yourapp1", 
                "appStatus": "online", 
                "createTime": "2017-11-27T06:51:25Z", 
                "publishDomain": "push.yourdomain.com", 
                "updateTime": "2017-11-27T06:51:26Z"
            }, 
            {
                "appName": "yourapp2", 
                "appStatus": "online", 
                "createTime": "2017-11-27T06:51:25Z", 
                "publishDomain": "push.yourdomain.com", 
                "updateTime": "2017-11-27T06:51:26Z"
            }
        ], 
        "pageNumber": 1, 
        "pageSize": 10, 
        "totalCount": 2
    }
}
```
