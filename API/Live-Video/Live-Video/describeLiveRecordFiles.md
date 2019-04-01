# describeLiveRecordFiles


## 描述
查询录制文件列表


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/recordFiles


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNum**|Integer|True| |当面页数<br>|
|**pageSize**|Integer|True| |每页记录数<br>|
|**authExpire**|Integer|False| |下载地址有效期，单位：秒，默认：3600<br>|
|**publishDomain**|String|True| |推流域名<br>|
|**appName**|String|True| |推流AppName<br>|
|**streamName**|String|True| |流名称<br>|
|**startTime**|String|True| |查询起始时间，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**endTime**|String|True| |查询截至时间，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|


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
|**domainDetails**|RecordFile[]|文件信息集合|
### RecordFile
|名称|类型|描述|
|---|---|---|
|**fileId**|String|录制文件ID<br>|
|**format**|String|文件格式<br>|
|**width**|Integer|视频宽度<br>- 单位: 像素<br>|
|**height**|Integer|视频高度<br>- 单位: 像素<br>|
|**startTime**|String|录制开始时间<br>|
|**endTime**|String|录制结束时间<br>|
|**duration**|Integer|视频时长<br>|
|**size**|Integer|文件大小<br>|
|**bitrate**|Integer|码率<br>|
|**fps**|Integer|帧率<br>|
|**imgUrl**|String|文件地址<br>|
|**createTime**|String|创建时间<br>|

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
https://live.jdcloud-api.com/v1/recordFiles

```
```
{
    "appName": "your appname", 
    "authExpire": 3600, 
    "endTime": "2019-03-27T16:00:00Z", 
    "pageNum": "0", 
    "pageSize": "100", 
    "publishDomain": "your domain", 
    "startTime": "2019-03-26T16:00:00Z", 
    "streamName": "your streamname"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "fileList": [
            {
                "appName": "xxx", 
                "bitrate": "", 
                "createTime": "2016-05-25T05:48:11Z", 
                "duration": 18800, 
                "endTime": "2016-05-25T05:47:11Z", 
                "fileId": "", 
                "fileUrl": "", 
                "format": "jpg", 
                "fps": "", 
                "height": 234, 
                "publishDomain": "xxx", 
                "size": 200808, 
                "startTime": "2016-05-25T05:37:11Z", 
                "streamName": "xxx", 
                "width": 112
            }
        ], 
        "pageNumber": 1, 
        "pageSize": 100, 
        "totalCount": 2
    }
}
```
