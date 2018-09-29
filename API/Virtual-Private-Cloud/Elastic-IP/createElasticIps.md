# createElasticIps


## 描述
创建一个或者多个弹性Ip

## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/elasticIps/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**elasticIpAddress**|String|False| |指定弹性ip地址进行创建，当申请创建多个弹性ip时，必须为空|
|**elasticIpSpec**|ElasticIpSpec|True| |弹性ip规格|
|**maxCount**|Integer|True| |购买弹性ip数量；取值范围：[1,100]|

### ElasticIpSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bandwidthMbps**|Integer|True| |弹性公网IP的限速（单位：Mbps），取值范围为[1-200]|
|**chargeSpec**|ChargeSpec|False| |计费配置|
|**provider**|String|True| |IP服务商，取值为bgp或no_bgp，cn-north-1：bgp；cn-south-1：[bgp，no_bgp]；cn-east-1：[bgp，no_bgp]；cn-east-2：bgp|
### ChargeSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result|返回结果|

### Result
|名称|类型|描述|
|---|---|---|
|**elasticIpIds**|String[]|弹性IP ID列表|
|**requestId**|String|请求ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**400**|Invalid param 'xxx'|
|**500**|Unknown server error|
|**401**|Unauthenticated user pin 'xxx'|
|**503**|Service unavailable|
