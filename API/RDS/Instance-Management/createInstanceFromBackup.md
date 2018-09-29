# createInstanceFromBackup


## 描述
根据源实例全量备份创建一个新实例，新实例的数据跟源实例在创建备份时的数据状态一样。<br>例如根据源实例A的一个全量备份“mybak”新建一个实例B，该备份是在“‘2018-8-18 03:23:54”创建的。那么新建实例B的数据状态跟实例A‘2018-8-18 03:23:54’的状态一致<br>- 仅支持MySQL

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances:createInstanceFromBackup

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backupId**|String|True| |备份ID|
|**engine**|String|True| |标识是创建什么类型的实例，例如MySQL，SQL Server等,具体可参见文档[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)<br>**注意：备份来源实例的engine和要创建的实例的engine必须一致**|
|**instanceSpec**|RestoredNewDBInstanceSpec|True| |新建实例规格|

### RestoredNewDBInstanceSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**azId**|String[]|True| |可用区ID， 第一个ID必须为主实例所在的可用区。如两个可用区一样，也需输入两个azId|
|**chargeSpec**|ChargeSpec|True| |计费规格，包括计费类型，计费周期等|
|**instanceClass**|String|True| |实例规格代码，可以通过[describeInstanceClasses](../instance/describeInstanceClasses.md)接口获取|
|**instanceName**|String|False| |数据库实例名，名称的限制可参考[帮助中心文档](../../../documentation/Cloud-Database-and-Cache/RDS/Introduction/Restrictions/SQLServer-Restrictions.md)|
|**instanceStorageGB**|Integer|True| |磁盘大小，单位GB|
|**subnetId**|String|True| |子网ID|
|**vpcId**|String|True| |VPC的ID|
### ChargeSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**instanceId**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
