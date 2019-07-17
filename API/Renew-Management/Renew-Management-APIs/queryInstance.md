# queryInstance


## 描述
提供可续费的实例信息查询。

## 请求方式
POST

## 请求地址
https://renewal.jdcloud-api.com/v2/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**queryInstanceParam**|QueryInstanceParam|True| | |

### QueryInstanceParam
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|True| |业务线|
|**serviceCode**|String|True| |产品线|
|**instanceName**|String|False| |资源名称|
|**instanceId**|String|False| |资源ID|
|**renewStatus**|String|True| |资源续费状态(AUTO-开通自动续费资源,MANUAL-未开通自动续费资源,ALL-全部资源)|
|**billingType**|String|False| |资源计费类型(CONFIG-按配置,FLOW-按用量,MONTHLY-包年包月)，不传显示全部资源|
|**expireType**|String|False| |资源到期类型(EXPIRED-已到期,UNEXPIRED-未到期,ONE-1天内到期,THREE-3天内到期,SEVEN-7天内到期,ALL_TIME-全部)|
|**ipAddress**|String|False| |主机绑定的内网IP地址|
|**pageNumber**|Integer|False| |当前页码，不传默认为1|
|**pageSize**|Integer|False| |每页条数，不传默认为10|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**listQueries**|ListQuery[]|列表详情|
|**totalCount**|Integer|查询总数|
### ListQuery
|名称|类型|描述|
|---|---|---|
|**appCode**|String|业务线|
|**serviceCode**|String|产品线|
|**resourceId**|String|资源ID|
|**resourceName**|String|资源名称|
|**region**|String|地域|
|**billingType**|String|资源计费类型(CONFIG-按配置,FLOW-按用量,MONTHLY-包年包月)，不传显示全部资源|
|**expireTime**|String|资源到期时间|
|**lastTime**|Integer|倒计时|
|**autoRenewStatus**|String|自动续费状态(UNOPENED-未开通,OPENED-已开通)|
|**autoRenewPeriod**|String|自动续费周期，单位为月|
|**associateResource**|String|是否绑定关联资源一并续费(BIND-是,UNBIND-否)|
|**extendField**|String|扩展字段，包括数据库类型、资源特殊说明等|
|**relationList**|RelationResource[]|绑定资源列表|
### RelationResource
|名称|类型|描述|
|---|---|---|
|**appCode**|String|业务线|
|**serviceCode**|String|产品线|
|**resourceId**|String|资源ID|
|**resourceName**|String|资源名称|
|**region**|String|地域|
|**billingType**|String|资源计费类型(CONFIG-按配置,FLOW-按用量,MONTHLY-包年包月)，不传显示全部资源|
|**expireTime**|String|资源到期时间|
|**lastTime**|Integer|倒计时|
|**autoRenewStatus**|String|自动续费状态(UNOPENED-未开通,OPENED-已开通)|
|**extendField**|String|扩展字段，包括数据库类型、资源特殊说明等|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|Not found|
|**500**|Internal server error|
