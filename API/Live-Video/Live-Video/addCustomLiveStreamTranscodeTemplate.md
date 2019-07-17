# addCustomLiveStreamTranscodeTemplate


## 描述
添加自定义转码模板
- 系统为您预设了标准转码模板,如果不能满足您的转码需求,可以通过此接口添加自定义转码模板
- 系统标准转码模板<br>
    ld (h.264/640 * 360/15f)<br>
    sd (h.264/854 * 480/25f)<br>
    hd (h.264/1280 * 720/25f)<br>
    shd (h.264/1920 * 1080/30f)<br>
    2k (h.264/2560 * 1440/30f)<br>
    4k (h.264/3840 * 2160/30f)<br>
    ld-265 (h.265/640 * 360/15f)<br>
    sd-265 (h.265/854 * 480/25f)<br>
    hd-265 (h.265/1280 * 720/25f)<br>
    shd-265 (h.265/1920 * 1080/30f)<br>
    2k-265 (h.265/2560 * 1440/30f)<br>
    4k-265 (h.265/3840 * 2160/30f)<br>



## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/transcodeCustoms:template


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**videoCodec**|String|False| |视频编码格式，取值：h264,h265，默认h264<br>|
|**videoCodeRate**|Integer|True| |转码输出的码率值<br>- 取值范围: [128,15000]<br>- 单位: kpbs<br>|
|**videoFrameRate**|String|True| |转码输出的帧率值<br>- 取值：[1,30]<br>|
|**width**|Integer|False| |转码输出视频宽度<br>- 取值: [128,4096]<br>- 如果(width,height)只设置其中之一,则按所设置参数项等比缩放另一项输出转码<br>- 如果(width,height)都不设置，则按源流大小输出转码<br>|
|**height**|Integer|False| |转码输出视频宽度<br>- 取值: [128,4096]<br>- 如果(width,height)只设置其中之一,则按所设置参数项等比缩放另一项输出转码<br>- 如果(width,height)都不设置，则按源流大小输出转码<br>|
|**template**|String|True| |转码模板(转码流输出后缀)<br>- 取值要求：数字、大小写字母或短横线("-"),必须以数字或字母作为开头和结尾,长度不超过50字符<br>- <b>注意: 不能与系统的标准的转码模板和当前用户已自定义命名重复</b><br>- 系统标准转码模板<br>  ld (h.264/640 * 360/15f)<br> sd (h.264/854 * 480/25f)<br> hd (h.264/1280 * 720/25f)<br> shd (h.264/1920 * 1080/30f)<br> 2k (h.264/2560 * 1440/30f)<br> 4k (h.264/3840 * 2160/30f)<br> ld-265 (h.265/640 * 360/15f)<br> sd-265 (h.265/854 * 480/25f)<br> hd-265 (h.265/1280 * 720/25f)<br> shd-265 (h.265/1920 * 1080/30f)<br> 2k-265 (h.265/2560 * 1440/30f)<br> 4k-265 (h.265/3840 * 2160/30f)<br>|
|**audioCodec**|String|True| |转码输出音频编码格式<br>- 取值: aac、mp3<br>- 不区分大小写<br>|
|**audioFormat**|String|True| |转码输出音频格式<br>- 取值: aac_lc，aac_low，aac_he，aac_he_v2<br>- 不区分大小写<br>|
|**audioSampleRate**|Integer|True| |转码输出音频采样率<br>- 取值: [44100,48000]<br>|
|**audioChannel**|Integer|True| |转码输出音频通道数<br>  1: 单声道<br>  2: 双声道<br>|
|**audioCodeRate**|Integer|True| |转码输出音频码率<br>- 取值: [16,128]<br>- 单位: kbps<br>|
|**jdchd**|String|False| |京享超清开关<br>- 取值: jdchd-1.0,off<br>- 京享超清暂时只支持h.264<br>|
|**audioComfort**|String|False| |舒适音频<br>- 取值: on,off<br>|



## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|requestId|


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
POST
```
https://live.jdcloud-api.com/v1/transcodeCustoms:template
```

```
{
    "audioChannel": 2, 
    "audioCodeRate": 48, 
    "audioCodec": "aac", 
    "audioFormat": "aac_lc", 
    "audioSampleRate": 44100, 
    "height": 1080, 
    "template": "yt", 
    "videoCodeRate": 1500, 
    "videoFrameRate": "30", 
    "width": 1920
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
