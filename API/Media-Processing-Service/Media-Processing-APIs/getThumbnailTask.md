# getThumbnailTask


## 描述
根据任务ID获取截图任务。

## 请求方式
GET

## 请求地址
https://mps.jdcloud-api.com/v1/regions/{regionId}/thumbnail/{taskId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |region id|
|**taskId**|String|True| |task id|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**thumbnailTask**|ThumbnailTask| |
### ThumbnailTask
|名称|类型|描述|
|---|---|---|
|**createdTime**|String|任务创建时间 时间格式(GMT): yyyy-MM-dd’T’HH:mm:ss.SSS’Z’  (readonly)|
|**errorCode**|Integer|错误码 (readonly)|
|**lastUpdatedTime**|String|任务创建时间 时间格式(GMT): yyyy-MM-dd’T’HH:mm:ss.SSS’Z’  (readonly)|
|**rule**|ThumbnailTaskRule| |
|**source**|ThumbnailTaskSource| |
|**status**|String|状态 (SUCCESS, ERROR, PENDDING, RUNNING) (readonly)|
|**target**|ThumbnailTaskTarget| |
|**taskID**|String|任务ID (readonly)|
### ThumbnailTaskRule
|名称|类型|描述|
|---|---|---|
|**count**|Integer|截图数量, mode=single时不可选. default:1|
|**endTimeInSecond**|Integer|生成截图的结束时间, mode=single/average时不可选, 且不得小于startTimeInSecond. default:-1(代表视频时长)|
|**keyFrame**|Boolean|是否开启关键帧截图 default: true|
|**mode**|String|截图模式 单张: single 多张: multi 平均: average default: single|
|**startTimeInSecond**|Integer|生成截图的开始时间, mode=average 时不可选. default:0|
### ThumbnailTaskSource
|名称|类型|描述|
|---|---|---|
|**bucket**|String|输入视频信息的 bucket|
|**key**|String|输入视频信息的 Key|
### ThumbnailTaskTarget
|名称|类型|描述|
|---|---|---|
|**destBucket**|String|输入存放目标文件的 bucket|
|**destKeyPrefix**|String|目标截图的Key的前缀, '前缀-taskID-%04d(num).(format)', 默认: sourceKey|
|**format**|String|目标截图的格式 default: jpg|
|**heightInPixel**|Integer|目标截图的高, 如果视频实际分辨率低于目标分辨率则按照实际分辨率输出 default: 0 代表源视频高 其他[8, 4096]|
|**keys**|String[]|目标截图的Key的集合 (readonly)|
|**widthInPixel**|Integer|目标截图的宽, 如果视频实际分辨率低于目标分辨率则按照实际分辨率输出 default: 0 代表源视频高 其他[8, 4096]|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
