# createRefreshTask


## 描述
创建刷新预热任务

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/task


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**taskType**|String|False| |刷新预热类型,(url:url刷新,dir:目录刷新,prefetch:预热)|
|**urls**|String[]|False| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**errorCount**|Integer|失败任务的个数|
|**taskId**|String|任务的id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
