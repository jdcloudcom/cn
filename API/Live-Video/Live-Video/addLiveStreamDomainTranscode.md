# addLiveStreamDomainTranscode


## 描述
添加域名级别转码配置
- 添加域名级别的转码模板配置


## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/transcodeDomains:config


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |直播的推流域名|
|**template**|String|True| |转码模板(转码流输出后缀)<br>- 取值要求：数字、大小写字母或短横线("-"),必须以数字或字母作为开头和结尾,长度不超过50字符<br>- <b>注意: 不能与系统的标准的转码模板和当前用户已自定义命名重复</b><br>- 系统标准转码模板<br>  ld (h.264/640 * 360/15f)<br> sd (h.264/854 * 480/25f)<br> hd (h.264/1280 * 720/25f)<br> shd (h.264/1920 * 1080/30f)<br> 2k (h.264/2560 * 1440/30f)<br> 4k (h.264/3840 * 2160/30f)<br> ld-265 (h.265/640 * 360/15f)<br> sd-265 (h.265/854 * 480/25f)<br> hd-265 (h.265/1280 * 720/25f)<br> shd-265 (h.265/1920 * 1080/30f)<br> 2k-265 (h.265/2560 * 1440/30f)<br> 4k-265 (h.265/3840 * 2160/30f)<br>|


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
https://live.jdcloud-api.com/v1/transcodeDomains:config
```

```
{
    "publishDomain":"push.yourdomain.com",
    "template":"shd"
}
```

## 返回示例
```
{
    "requestId":"bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
