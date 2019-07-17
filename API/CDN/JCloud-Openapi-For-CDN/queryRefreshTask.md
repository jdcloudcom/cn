# queryRefreshTask


## 描述
查询刷新预热任务

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/task


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|False| |查询起始时间,UTC时间，格式为:yyyy-MM-dd'T'HH:mm:ss'Z'，示例:2018-10-21T10:00:00Z|
|**endTime**|String|False| |查询截止时间,UTC时间，格式为:yyyy-MM-dd'T'HH:mm:ss'Z'，示例:2018-10-21T10:00:00Z|
|**keyword**|String|False| |url或者目录的模糊查询关键字|
|**taskId**|String|False| |任务id|
|**taskStatus**|String|False| | |
|**taskType**|String|False| | |
|**pageNumber**|Integer|False| |分页页数,默认值1|
|**pageSize**|Integer|False| |分页页面大小,默认值50|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**total**|Integer|总的刷新预热条数.|
|**tasks**|RefreshTask[]| |
### RefreshTask
|名称|类型|描述|
|---|---|---|
|**createDate**|String|任务创建时间,UTC时间|
|**failed**|Float|任务失败率|
|**success**|Float|任务成功率|
|**taskId**|String|刷新预热的任务id|
|**id**|Long|数据库表id|
|**retryStatus**|String|重试状态(unretry:不重试,retry:重试)|
|**taskStatus**|String|任务状态(running:执行中,success:成功,failed:失败)|
|**taskType**|String|刷新预热类型,(url:url刷新,dir:目录刷新,prefetch:预热)|
|**urlTasks**|UrlTask[]|详细的任务|
### UrlTask
|名称|类型|描述|
|---|---|---|
|**taskType**|String|刷新预热类型,(url:url刷新,dir:目录刷新,prefetch:预热)|
|**url**|String|刷新预热的url|
|**status**|String|任务状态(running:执行中,success:成功,failed:失败)|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
