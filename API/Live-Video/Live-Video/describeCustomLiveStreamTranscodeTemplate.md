# describeCustomLiveStreamTranscodeTemplate


## 描述
查询用户自定义转码模板详情
- 查询用户自定义转码模板详情
- 系统标准转码模板
    ld (h.264/640*360/15f)
    sd (h.264/854*480/24f)
    hd (h.264/1280*720/25f)
    shd (h.264/1920*1080/30f)


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/transcodeCustoms/{template}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**template**|String|True| |转码模板|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**videoCodeRate**|Integer|转码输出的码率值<br>- 单位: kpbs<br>|
|**videoFrameRate**|String|转码输出的帧率值<br>|
|**width**|Integer|转码输出视频宽度<br>|
|**height**|Integer|转码输出视频宽度<br>|
|**template**|String|转码模板<br>|
|**audioCodec**|String|转码输出音频编码格式<br>|
|**audioFormat**|String|转码输出音频格式<br>|
|**audioSampleRate**|Integer|转码输出音频采样率<br>|
|**audioChannel**|Integer|转码输出音频通道数<br>  1: 单声道<br>  2: 双声道<br>|
|**audioCodeRate**|Integer|转码输出音频码率<br>- 单位: kbps<br>|

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
https://live.jdcloud-api.com/v1/transcodeCustoms/yt

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
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
}
```
