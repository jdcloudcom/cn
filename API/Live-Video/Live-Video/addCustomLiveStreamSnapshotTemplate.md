# addCustomLiveStreamSnapshotTemplate


## 描述
添加直播截图模板

## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/snapshotCustoms:template


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**format**|String|True| |截图格式<br>- 取值: jpg, png<br>- 不区分大小写<br>|
|**width**|Integer|False| |截图宽度<br>- 取值: [8,8192]<br>- 如果(width,height)只设置其中之一,则按所设置参数项等比缩放另一项输出截图<br>- 如果(width,height)都不设置，则按源流大小输出截图<br>|
|**height**|Integer|False| |截图高度<br>- 取值: [8,8192]<br>- 如果(width,height)只设置其中之一,则按所设置参数项等比缩放另一项输出截图<br>- 如果(width,height)都不设置，则按源流大小输出截图<br>|
|**fillType**|Integer|True| |截图与设定的宽高不匹配时的处理规则<br>  1: 拉伸<br>  2: 留黑<br>  3: 留白<br>  4: 高斯模糊<br>- 1是按照设定宽高拉伸<br>- 2,3,4是等比例的缩放多余或不足处按调置处理<br>|
|**snapshotInterval**|Integer|True| |截图周期<br>- 取值范围 [5,3600]<br>- 单位: 秒<br>|
|**saveMode**|Integer|True| |存储模式<br>  1: 覆盖存储<br>  2: 顺序存储<br>|
|**saveBucket**|String|True| |存储桶|
|**saveEndpoint**|String|True| |存储地址|
|**template**|String|True| |截图模板自定义名称:<br>- 取值要求: 数字、大小写字母或短横线("-"),<br>  首尾不能有特殊字符("-")<br>- <b>注意: 不能与已定义命名重复</b><br>|


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
https://live.jdcloud-api.com/v1/snapshotCustoms:template

```
```
{
    "fillType": 1, 
    "format": "jpg", 
    "saveBucket": "testbucket", 
    "saveEndpoint": "oss.xxx.com", 
    "saveMode": 1, 
    "snapshotInterval": 30, 
    "template": "mysnapshottemplate"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
