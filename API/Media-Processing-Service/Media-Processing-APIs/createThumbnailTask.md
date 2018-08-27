# createThumbnailTask


## 描述
创建截图任务

## 请求方式
POST

## 请求地址
https://mps.jdcloud-api.com/v1/regions/{regionId}/thumbnail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||region id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createdTime**|String|False||任务创建时间 时间格式(GMT): yyyy-MM-dd’T’HH:mm:ss.SSS’Z’  (readonly)|
|**errorCode**|Integer|False||错误码 (readonly)|
|**lastUpdatedTime**|String|False||任务创建时间 时间格式(GMT): yyyy-MM-dd’T’HH:mm:ss.SSS’Z’  (readonly)|
|**rule**|[ThumbnailTaskRule](##ThumbnailTaskRule)|False|||
|**source**|[ThumbnailTaskSource](##ThumbnailTaskSource)|True|||
|**status**|String|False||状态 (SUCCESS, ERROR, PENDDING, RUNNING) (readonly)|
|**target**|[ThumbnailTaskTarget](##ThumbnailTaskTarget)|True|||
|**taskID**|String|False||任务ID (readonly)|

### <a name="ThumbnailTaskRule">ThumbnailTaskRule</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**count**|Integer|False||截图数量, mode=single时不可选. default:1|
|**endTimeInSecond**|Integer|False||生成截图的结束时间, mode=single/average时不可选, 且不得小于startTimeInSecond. default:-1(代表视频时长)|
|**keyFrame**|Boolean|False||是否开启关键帧截图 default: true|
|**mode**|String|False||截图模式 单张: single 多张: multi 平均: average default: single|
|**startTimeInSecond**|Integer|False||生成截图的开始时间, mode=average 时不可选. default:0|
### <a name="ThumbnailTaskSource">ThumbnailTaskSource</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bucket**|String|True||输入视频信息的 bucket|
|**key**|String|True||输入视频信息的 Key|
### <a name="ThumbnailTaskTarget">ThumbnailTaskTarget</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**destBucket**|String|True||输入存放目标文件的 bucket|
|**destKeyPrefix**|String|False||目标截图的Key的前缀, '前缀-taskID-%04d(num).(format)', 默认: sourceKey|
|**format**|String|False||目标截图的格式 default: jpg|
|**heightInPixel**|Integer|False||目标截图的高, 如果视频实际分辨率低于目标分辨率则按照实际分辨率输出 default: 0 代表源视频高 其他[8, 4096]|
|**keys**|String[]|False||目标截图的Key的集合 (readonly)|
|**widthInPixel**|Integer|False||目标截图的宽, 如果视频实际分辨率低于目标分辨率则按照实际分辨率输出 default: 0 代表源视频高 其他[8, 4096]|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**thumbnailTaskID**|[ThumbnailTaskID](##ThumbnailTaskID)||
### <a name="ThumbnailTaskID">ThumbnailTaskID</a>
|名称|类型|描述|
|---|---|---|
|**taskID**|String||

## 返回码
|返回码|描述|
|---|---|
|**200**|成功|
