# createInstance


## 描述
创建实例

## 请求方式
POST

## 请求地址
https://mongodb.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeSpec**|ChargeSpec|False| |付费方式|
|**instanceSpec**|DBInstanceSpec|True| |实例规格|

### DBInstanceSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**azId**|String[]|True| |可用区ID，必填，第一个ID为primary所在可用区ID，第二个为secondary，第三个为hidden。multiAZ选择是，则primary与secondary的可用区ID需相同，且与hidden不同；multiAZ选择否，三个节点写相同的可用区ID。|
|**backupId**|String|False| |按备份创建使用的具体备份ID|
|**engine**|String|False| |数据库类型，MongoDB|
|**engineVersion**|String|False| |数据库版本，3.2|
|**instanceClass**|String|True| |实例规格代码。mongo.s1.small：1核2G;mongo.s1.medium：2核4G;mongo.s1.large：4核8G;mongo.s1.xlarge：8核16G;mongo.s2.2xlarge：8核32G;mongo.s2.4xlarge：16核64G;|
|**instanceName**|String|False| |实例名称，只支持数字、字母、英文下划线、中文，且不少于2字符不超过32字符。|
|**instanceStorageGB**|Integer|True| |存储空间，单位GB，取值10-1000,10的倍数。|
|**multiAZ**|Boolean|True| |是否选择多可用区部署|
|**originDBInstanceId**|String|False| |基于一个实例的备份创建新实例，如填写则restoreTime也需要填写。|
|**password**|String|False| |密码，必须包含且只支持字母及数字，不少于8字符不超过16字符。|
|**restoreTime**|String|False| |用户指定备份保留周期内的任意时间点，如2011-06-11T16:00:00Z，非必填，与backupId互斥。|
|**subnetId**|String|True| |子网ID|
|**vpcId**|String|True| |VPCID|
### ChargeSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**instanceId**|String| |
|**orderId**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
