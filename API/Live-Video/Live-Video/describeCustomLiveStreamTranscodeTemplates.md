# describeCustomLiveStreamTranscodeTemplates


## 描述
查询用户自定义转码模板列表


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/transcodeCustoms


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNum**|Integer|False|1|页码<br>- 取值范围 [1, 100000]<br>|
|**pageSize**|Integer|False|10|分页大小<br>- 取值范围 [10, 100]<br>|
|**filters**|Filter[]|False| |转码模板查询过滤条件:<br>  - name:   template 转码模板自定义名称<br>  - value:  如果参数为空，则查询全部<br>  - 如果为空,则表示查询该用户下所有自定义的转码模板<br>|

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
|**transcodeTemplates**|TranscodeInfo[]|码率信息|
### TranscodeInfo
|名称|类型|描述|
|---|---|---|
|**videoCodec**|String|视频编码格式<br>  - 取值：h264,h265，默认h264<br>|
|**videoCodeRate**|Integer|转码输出的码率值:<br>  - 取值: [128,15000]<br>  - 单位: kpbs<br>|
|**videoFrameRate**|String|转码输出的帧率值:<br>  - 取值: [1,30]<br>|
|**width**|Integer|转码输出视频宽度:<br>  - 取值: [128,4096]<br>  - 等比: 如果只填写一个参数,则按参数比例调节输出转码视频<br>  - 随源: 如果两个参数都不填写，则按照源比例输出转码视频<br>|
|**height**|Integer|转码输出视频宽度:<br>  - 取值: [128,4096]<br>  - 等比: 如果只填写一个参数,则按参数比例调节输出转码视频<br>  - 随源: 如果两个参数都不填写，则按照源比例输出转码视频<br>|
|**template**|String|转码模板自定义名称:<br>  - 自定义模板: 枚举类型校验，忽略大小写，自动删除空格,<br>              取值要求：数字、大小写字母或短横线("-"),<br>              首尾不能有特殊字符("-")<br>  - 注意: 不能与标准的转码模板和已定义命名重复<br>|
|**audioCodec**|String|转码输出音频编码格式:<br>  - 取值: aac、mp3<br>  - 不区分大小写<br>|
|**audioFormat**|String|转码输出音频格式:<br>  - 取值: aac_lc，aac_low，aac_he，aac_he_v2<br>  - 不区分大小写<br>|
|**audioSampleRate**|Integer|转码输出音频采样率:<br>  - 取值: [44100,48000]<br>|
|**audioChannel**|Integer|转码输出音频通道数:<br>  - 1  单声道<br>  - 2  双声道<br>|
|**audioCodeRate**|Integer|转码输出音频码率:<br>  - 取值: [16,128]<br>  - 单位: kbps<br>|
|**jdchd**|String|京享超清<br>- 取值: jdchd-1.0,off<br>|
|**audioComfort**|String|舒适音频<br>- 取值: on,off<br>|


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
https://live.jdcloud-api.com/v1/transcodeCustoms?filters.1.name=template&filters.1.values.1=yt
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "pageNumber": 1, 
        "pageSize": 10, 
        "totalCount": 1, 
        "transcodeTemplates": [
            {
                "audioChannel": 2, 
                "audioCodeRate": 16, 
                "audioCodec": "aac", 
                "audioFormat": "aac_lc", 
                "audioSampleRate": 44800, 
                "height": 480, 
                "template": "yt", 
                "videoCodeRate": 300, 
                "videoFrameRate": "25/1", 
                "width": 720
            }
        ]
    }
}
```
