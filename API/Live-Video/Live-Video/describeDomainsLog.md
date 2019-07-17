# describeDomainsLog


## 描述
日志下载

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describeDomainsLog


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domains**|String|True| |播放域名，多个时以逗号（,）分隔|
|**interval**|String|False| |时间间隔，取值(hour，day),不传默认小时<br>- 按小时（hour）下载时是.log文件<br>- 按天（day）下载时是.zip文件|
|**startTime**|String|True| |起始时间<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>|
|**endTime**|String|False| |结束时间:<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>- 为空,默认为当前时间<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|DomainsLogResult[]| |
### DomainsLogResult
|名称|类型|描述|
|---|---|---|
|**domain**|String|域名<br>|
|**logList**|DomainsLogResultData[]| |
### DomainsLogResultData
|名称|类型|描述|
|---|---|---|
|**fileName**|String|文件名称<br>|
|**logUrl**|String|下载地址<br>|
|**md5**|String|文件md5<br>|
|**size**|Long|文件大小，单位：Byte<br>|
|**startTime**|String|开始时间，UTC时间格式<br>|
|**endTime**|String|结束时间，UTC时间格式<br>|

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
https://live.jdcloud-api.com/v1/describeDomainsLog?domains=push.yourdomain.com&startTime=2018-10-21T10:00:00Z
```

## 返回示例
```
{
    "requestId": "bkcu3ts60jt1f86ti756imamqaw18puj", 
    "result": {
        "dataList": [
            {
                "domain": "wcdn.servyou.com.cn", 
                "logList": [
                    {
                        "endTime": "2019-04-26T01:40:00Z", 
                        "fileName": "201904260940", 
                        "logUrl": "http://s3.cn-north-1-nat.jdcloudcs.com/cdnuserlog.test/wcdn.servyou.com.cn/20190426/2019042609/201904260935.gz?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20190524T031004Z&X-Amz-SignedHeaders=host&X-Amz-Expires=899&X-Amz-Credential=ImtHrS1VXMxeikph%2F20190524%2Fcn-ite-1%2Fs3%2Faws4_request&X-Amz-Signature=009906534b2b57f23738ef25e36a71436fc7b3f8693a07a570e521f22662c35c", 
                        "md5": "caad51b1b9cc54577183aa8e505a09da", 
                        "size": 6988, 
                        "startTime": "2019-04-26T01:35:00Z"
                    }
                ]
            }, 
            {
                "domain": "www.yqb2c.com", 
                "logList": []
            }
        ]
    }
}
```
