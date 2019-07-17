# addCustomLiveStreamWatermarkTemplate


## 描述
添加用户自定义水印模板


## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/watermarkCustoms:template


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**position**|Integer|False| |水印位置<br>- 取值范围：左上：1，右上：3， 左下：7，右下：9，默认：1<br>|
|**offsetUnit**|String|False| |偏移量单位<br>- 取值: percent,pixel<br>- percent:按百分比; pixel:像素 默认:pixel<br>|
|**offsetX**|Integer|True| |x轴偏移量<br>- 取值范围<br>  percent: (0,100]<br>  pixel: (0,1920]<br>|
|**offsetY**|Integer|True| |y轴偏移量:<br>- 取值范围<br>  percent: (0,100]<br>  pixel: (0,1920]<br>|
|**sizeUnit**|String|False| |水印大小单位<br>- 取值: percent,pixel<br>- percent:按百分比; pixel:像素 默认:pixel<br>|
|**width**|Integer|True| |水印宽度:<br>- 取值范围<br>  percent: (0,100]<br>  pixel: (0,1920]<br>|
|**height**|Integer|True| |水印高度:<br>- 取值范围<br>  percent: (0,100]<br>  pixel: (0,1920]<br>|
|**template**|String|True| |自定义水印模板名称<br>-&ensp;取值要求: 数字、大小写字母、短横线("-")、下划线("_"),<br>&ensp;&ensp;首尾不能有特殊字符("-"),<br>&ensp;&ensp;不超过50字符,utf-8格式<br>-&ensp;<b>注意: 不能与已定义命名重复</b><br>|
|**uploadId**|String|False| |创建上传任务时返回的uploadId参数，当通过接口上传水印图片时，uploadId必填<br>|
|**url**|String|True| |水印地址<br>-&ensp;以&ensp;http:// 开头,可公开访问地址<br>|


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
https://live.jdcloud-api.com/v1/watermarkCustoms:template
```

```
{
    "height": 30, 
    "offsetUnit": "pixel", 
    "offsetX": 10, 
    "offsetY": 20, 
    "sizeUnit": "pixel", 
    "template": "yourwatermark", 
    "uploadId": "response uploadId from createImageUploadTask api", 
    "url": "http://xxx.com/xxx.jpg", 
    "width": 50
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
