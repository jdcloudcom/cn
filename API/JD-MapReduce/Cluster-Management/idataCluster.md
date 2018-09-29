# idataCluster


## 描述
查询用户指定clusterId对应的集群列表及相关服务的一些信息

## 请求方式
GET

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/idata

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**id**|String|True| |集群ID；由八位字符组成|
|**regionId**|String|True| |地域ID|

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
|**data**|Object|"包括集群信息列表 - clusters"<br>"集群机器总数 - total"<br>|
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
