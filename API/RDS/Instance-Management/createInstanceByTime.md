# createInstanceByTime


## 描述
根据源实例备份创建一个新实例，并通过追加日志的方式，将新实例的数据恢复到跟源实例指定时间点的数据状态一样。<br>例如根据实例A在“2018-06-18 23:00:00”时间点创建一个实例B，就是新建一个实例B，该实例B的数据跟实例A在“2018-06-18 23:00:00”这个时间点的数据完全一致。<br>对于SQL Server，主备切换后30分钟内，不支持按时间点恢复/创建，例如在10:05分用户进行了主备切换，那么10:05 ~ 10:35这个时间段不能进行按时间点恢复/创建。

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:createInstanceByTime

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**restoreTime**|String|True| |根据源实例的哪个时间点创建新实例|
|**instanceSpec**|[RestoredNewDBInstanceSpec](#RestoredNewDBInstanceSpec)|True| |新建实例规格|

### <a name="RestoredNewDBInstanceSpec">RestoredNewDBInstanceSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceName**|String|False| |数据库实例名，名称的限制可参考[帮助中心文档](../../../documentation/Database-and-Cache-Service/RDS/Introduction/Restrictions/SQLServer-Restrictions.md)|
|**instanceClass**|String|True| |实例规格代码，可以查看文档[MySQL 实例规格](../Instance-Specifications/Instance-Specifications-MySQL.md)、[SQL Server实例规格](../Instance-Specifications/Instance-Specifications-SQLServer.md)|
|**instanceStorageGB**|Integer|True| |磁盘大小，单位GB|
|**azId**|String[]|True| |可用区ID， 第一个ID必须为主实例所在的可用区。如两个可用区一样，也需输入两个azId|
|**vpcId**|String|True| |VPC的ID|
|**subnetId**|String|True| |子网ID|
|**parameterGroup**|String|False| |参数组ID, 缺省系统会创建一个默认参数组<br>- 仅支持MySQL|
|**chargeSpec**|[ChargeSpec](#ChargeSpec)|True| |计费规格，包括计费类型，计费周期等|
|**instanceStorageType**|String|False| |存储类型，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md), 缺省值为：LOCAL_SSD<br>- 仅支持MySQL|
|**instancePort**|String|False| |应用访问端口, 仅支持 MySQL，Percona, MariaDB, 默认值为 3306|
|**storageEncrypted**|Boolean|False| |实例数据加密(存储类型为云硬盘才支持数据加密)。false：不加密，true：加密，缺省为false<br>- 仅支持MySQL|
|**instanceType**|String|False| |实例的高可用架构。standalone：单机，cluster：主备双机架构，缺省为cluster<br>- 仅支持SQL Server|
### <a name="ChargeSpec">ChargeSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**autoRenew**|Boolean|False| |True=：OPEN——开通自动续费、False=CLOSE—— 不开通自动续费，默认为CLOSE|
|**buyScenario**|String|False| |产品线统一活动凭证JSON字符串，需要BASE64编码，目前要求编码前格式为 {"activity":{"activityType":必填字段, "activityIdentifier":必填字段}}|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|新创建的实例ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
