# describeDomainOnlineStream


## 描述
查询在线流列表

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describeDomainOnlineStream


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |推流域名|
|**appName**|String|False| |应用名称|
|**streamName**|String|False| |流名称|
|**pageNum**|Integer|False| |页码，起始页码1<br>|
|**pageSize**|Integer|False| |每页最大记录数，取值：[10,100]，默认：10<br>|
|**startTime**|String|True| |起始时间<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>|
|**endTime**|String|False| |结束时间:<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>- 为空,默认为当前时间，查询时间跨度不超过30天<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|PublishOnlineStreamResult[]| |
### PublishOnlineStreamResult
|名称|类型|描述|
|---|---|---|
|**total**|Integer|返回的记录数<br>|
|**streamList**|PublishOnlineStreamResultData[]| |
### PublishOnlineStreamResultData
|名称|类型|描述|
|---|---|---|
|**appName**|String|APP名称<br>|
|**streamName**|String|流名称<br>|
|**clientIp**|String|客户端ip<br>|
|**serverIp**|String|边缘节点ip<br>|
|**frameRate**|Number|帧率<br>|
|**frameLossRate**|Number|丢帧率<br>|
|**lastActive**|Long|最近活跃时间<br>|
|**realFps**|Number|实时帧率<br>|
|**uploadSpeed**|Long|上传速度  单位：KB/s<br>|
|**videoCodec**|Long|视频codec，取值：<br>- VideoAVC = 7<br>- VideoHEVC = 12<br>|
|**videoDataRate**|Long|视频码率 单位：KB/s<br>|
|**audioCodec**|Long|音频codec，取值：<br>- AudioReserved1 = 16<br>- AudioDisabled = 17<br>- AudioLinearPCMPlatformEndian = 0<br>- AudioADPCM = 1<br>- AudioMP3 = 2<br>- AudioLinearPCMLittleEndian = 3<br>- AudioNellymoser16kHzMono = 4<br>- AudioNellymoser8kHzMono = 5<br>- AudioNellymoser = 6<br>- AudioReservedG711AlawLogarithmicPCM = 7<br>- AudioReservedG711MuLawLogarithmicPCM = 8<br>- AudioReserved = 9<br>- AudioAAC = 10<br>- AudioSpeex = 11<br>- AudioReservedMP3_8kHz = 14<br>- AudioReservedDeviceSpecificSound = 15<br>|

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
https://live.jdcloud-api.com/v1/describeDomainOnlineStream?domainName=yourdomain&appName=yourapp&streamName=yourstream&startTime=2018-10-21T10:00:00Z&&endTime=2018-10-22T10:00:00Z
```

## 返回示例
```
{
    "code": 200, 
    "requestId": "bkcu3ts60jt1f86ti756imamqaw18puj", 
    "result": {
        "streamList": [
            {
                "appName": "live", 
                "audioCodec": 10, 
                "clientIp": "111.202.36.10", 
                "frameLossRate": 0.04, 
                "frameRate": 25, 
                "lastActive": 1561973235, 
                "realFps": 24, 
                "serverIp": "220.194.105.169", 
                "streamName": "dance_0", 
                "uploadSpeed": 1648, 
                "videoCodec": 7, 
                "videoDataRate": 1581
            }, 
            {
                "appName": "live", 
                "audioCodec": 10, 
                "clientIp": "", 
                "frameLossRate": 0, 
                "frameRate": 25, 
                "lastActive": 1561973234, 
                "realFps": 25, 
                "serverIp": "", 
                "streamName": "dance_0_1500", 
                "uploadSpeed": 2015, 
                "videoCodec": 7, 
                "videoDataRate": 1950
            }
        ], 
        "total": 2
    }
}
```
