# getExpiringOrders


## 描述
查询资源单列表接口，不含已删除资源

## 请求方式
POST

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/getExpiringOrders

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|False| |appCode|
|**billingStatus**|Integer|False| |计费状态 0:停止计费 1:计费中|
|**billingType**|Integer|False| |计费类型 1:按配置 2:按用量 3:包年包月|
|**billingTypeList**|Number[]|False| |billingTypeList|
|**departmentId**|Integer|False| |部门（节点云查询使用）|
|**endTime**|String|False| |结束时间|
|**excludeResources**|String[]|False| |excludeResources|
|**expireInDays**|Integer|False| |>0: 订单还有几天到期; ==0: 订单已经到期; <0: 不管是否到期|
|**expiringInDays**|Integer|False| |1、内部计算，使用getExpiringOrderCount时使用，不用传值 默认为-1mybatis筛选时不会关注 2、selectResourceOrderForTask定时任务查询列表时使用，停服天数，必须大于0|
|**id**|Integer|False| |主键id|
|**isOnTrial**|Integer|False| |isOnTrial|
|**isSpecial**|Integer|False| |是否是专有云 1:是  其他不是|
|**networkOperator**|Integer|False| |网络类型 0: non-BGP, 1: BGP|
|**node**|String|False| |专有云节点的code（节点云查询使用）|
|**nodeCode**|String|False| |节点信息|
|**offset**|Integer|False| | |
|**opTypes**|Number[]|False| | |
|**orderByClaus**|String|False| |orderByClaus|
|**pageIndex**|Integer|False| |当前页序号|
|**pageSize**|Integer|False| |每页结果数量|
|**pin**|String|False| |用户pin|
|**pinList**|String[]|False| | |
|**region**|String|False| |地域|
|**resourceId**|String|False| |资源id|
|**resourceIdList**|String[]|False| |resourceIdList|
|**serviceCode**|String|False| |服务编码|
|**serviceCodeList**|String[]|False| |产品码列表|
|**site**|Integer|False| |站点信息 0:中国 1:国际|
|**startTime**|String|False| |开始时间|
|**status**|Integer|False| |资源状态 1:正常 2:停服 3:删除|
|**statusList**|Number[]|False| |statusList|
|**timeout**|Integer|False| |超时时间，暂时不用|
|**transactionNos**|String[]|False| |交易单号列表|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**pagination**|Pagination| |
|**result**|ResourceOrderVo[]| |
### Pagination
|名称|类型|描述|
|---|---|---|
|**currPageNo**|Integer|当前页|
|**numberPages**|Integer|页数|
|**numberRecords**|Integer|每页记录数|
|**pageSize**|Integer|页面大小|
|**startIndex**|Integer|起始页|
### ResourceOrderVo
|名称|类型|描述|
|---|---|---|
|**aeStatus**|Integer|欠费过期状态|
|**appCode**|String|应用码|
|**applicant**|String|资源申请人|
|**billingCategoryDescription**|String|计费类型描述 例如:按配置、包年包月|
|**billingMode**|Integer|计费模式  1.停服停止计费  2.关机停止计费|
|**billingStartTime**|String|计费开始时间 续费时本次续费周期开始时间|
|**billingStatus**|Integer|计费状态 0:停止计费 1:计费中|
|**billingType**|Integer|计费类型 1:按配置 2:按用量 3:包年包月 4:一次性|
|**billingTypeName**|String|计费类型单号|
|**chargeDuration**|Integer|timeSpan兼容交易系统字段|
|**chargeMode**|Integer|billingType兼容交易系统字段|
|**chargeUnit**|Integer|timeUnit兼容交易系统字段|
|**createTime**|String|创建时间|
|**description**|String|计费详情描述 例如:按配置、包年包月（一年）|
|**discountedPrice**|Number|折扣后订单价格|
|**endTime**|String|结束时间|
|**expiringDays**|Integer|即将到期天数|
|**favorableInfo**|String|促销明细|
|**formula**|Formula[]|配置信息|
|**formulaStr**|String|formula转换成字符串|
|**id**|Integer|主键id|
|**isOnTrial**|Integer|否为试用资源 0:非试用 1:试用|
|**networkOperator**|Integer|网络类型0:无 1: non-BGP, 2: BGP|
|**operateTime**|String|启服、停服、停止计费时间|
|**payTime**|String|支付时间|
|**pin**|String|用户pin|
|**price**|Number|订单折扣前总价|
|**priceMap**|Map|最新价格map|
|**priceSnapshot**|String|价格快照|
|**processType**|Integer|变配明细（1-升配，2-降配，3-调整配置,4-续费,5-续费升配,6-续费降配,7-配置转包年包月）|
|**refundNo**|String|refundNo|
|**region**|String|资源区域|
|**releasingTime**|String|欠费、过期资源释放时间|
|**resourceId**|String|资源id|
|**resourceName**|String|资源名|
|**serviceCode**|String|服务码|
|**site**|Integer|站点标识0:中国 1:国际|
|**sourceId**|String|交易单模块sourceId 计费不关心|
|**startTime**|String|开始时间|
|**status**|Integer|资源状态 1:正常 2:停服 3:删除|
|**timeSpan**|Integer|时长字段，与timeUnit字段构成具体时长|
|**timeUnit**|Integer|时长类型 1:小时 2:天 3:月 4:年|
|**transactionNo**|String|交易单唯一标识|
### Formula
|名称|类型|描述|
|---|---|---|
|**key**|String|计费项别名|
|**number**|Number|计费项数量|
|**unit**|String|单位|
|**value**|Number|用量|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
