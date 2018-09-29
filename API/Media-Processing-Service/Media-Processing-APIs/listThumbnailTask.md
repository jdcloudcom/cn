# listThumbnailTask


## 描述
查询截图任务，返回满足查询条件的任务列表。

## 请求方式
GET

## 请求地址
https://mps.jdcloud-api.com/v1/regions/{regionId}/thumbnail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |region id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**begin**|String|False| |开始时间 时间格式(GMT): yyyy-MM-dd'T'HH:mm:ss.SSS'Z'|
|**end**|String|False| |结束时间 时间格式(GMT): yyyy-MM-dd'T'HH:mm:ss.SSS'Z'|
|**limit**|Integer|False|1000|查询记录数 [1, 1000]|
|**marker**|String|False| |查询标记|
|**status**|String|False| |task 状态 (PENDING, RUNNING, SUCCESS, FAILED)|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**thumbnailQuery**|ThumbnailQuery| |
### ThumbnailQuery
|名称|类型|描述|
|---|---|---|
|**begin**|String|查询开始时间 时间格式(GMT): yyyy-MM-dd’T’HH:mm:ss.SSS’Z’|
|**end**|String|查询结束时间 时间格式(GMT): yyyy-MM-dd’T’HH:mm:ss.SSS’Z’|
|**limit**|Integer|本次请求返回的任务列表的最大元素个数, 有效值: [1-1000]，默认值: 1000|
|**marker**|String|本次请求的marker, 标记查询的起始位置, 此处为taskID|
|**nextMarker**|String|获取下一页所需要传递的marker值(此处为taskID), 仅当isTruncated为true时(数据未全部返回)出现 (readonly)|
|**status**|String|状态 (SUCCESS, ERROR, PENDDING, RUNNING)|
|**taskList**|ThumbnailTask[]|返回的task列表 (readonly)|
|**truncated**|Boolean|指明返回数据是否被截断. true表示本页后面还有数据, 即数据未全部返回; false表示已是最后一页, 即数据已全部返回 (readonly)|
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
|**200**|成功|
