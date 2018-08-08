# createInstance


## 描述
创建数据库集群实例</br>- SQL Server：支持</br>- MySQL：支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceSpec**|[DBInstanceSpec](##DBInstanceSpec)|True||新建实例规格|

### <a name="DBInstanceSpec">DBInstanceSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**azId**|String[]|True||可用区ID， 第一个ID必须为主实例所在的可用区。如两个可用区一样，也需输入两个azId|
|**chargeSpec**|[ChargeSpec](##ChargeSpec)|True||计费配置|
|**engine**|String|True||数据库类型 MySQL|SQL Server|
|**engineVersion**|String|True||数据库版本 MySQL支持5.6、5.7  SQL Server支持2008 R2、2012 EE、2014 EE、2016 EE|
|**instanceClass**|String|True||实例规格代码|
|**instanceName**|String|False||数据库实例名，如不填则缺省为instanceId|
|**instanceStorageGB**|Integer|True||磁盘大小，单位GB|
|**subnetId**|String|True||子网ID|
|**vpcId**|String|True||VPC的ID|
### <a name="ChargeSpec">ChargeSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False||预付费计费时长，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeUnit**|String|False||预付费计费单位，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
POST
```

```

## 返回示例
无
